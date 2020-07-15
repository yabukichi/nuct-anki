<template>
    <section class="container">
        <div class="login" @click="doLogin">[login:{{user_name}}]</div>
        <h1>{{title}}</h1>
        <p class="message">{{message}}</p>
        <div v-if="logined">
        <table>
            <tr>
                <th>Message</th>
                <td><input v-model="msg" size="50"></td>
                <td><button @click="add">投稿</button></td>
                <td><button @click="logout">ログアウト</button></td>
                <td><button @click="doLogin">ログイン</button></td>
            </tr>
        </table>
        <hr>
        <h3>{{user_id}}</h3>
        <hr>
        <ul v-for="(data, key) in json_data">
            <li><div class="list1">{{data.msg}}</div>
            <div class="list2">{{data.user}} ({{data.posted}})</div></li>
        </ul>
        </div>
    </section>
</template>


<script>
import firebase from "firebase";

const axios = require('axios');

// ※configの内容は、それぞれの環境に合わせて設定
// （FirebaseのAuthenticationの「ウェブ設定」からコピー＆ペースト）
let config = {
    apiKey: process.env.FIREBASEAPIKEY,
    authDomain: process.env.AUTHDOMAIN,
    databaseURL: process.env.DATABASEURL,
    projectId: process.env.PROJECTID,
    storageBucket: process.env.STORAGEBUCKET,
    messagingSenderId: process.env.MESSAGINGSENDERID,
    appId: process.env.APPID,
    measurementId: process.env.MEASUREMENTID
};

firebase.initializeApp(config);


export default {
    data: function(){
        return {
            title:'Board',
            message:'ミニ伝言板。最新の投稿を表示します。',
            user_name:'',
            user_id:'',
            logined: true,
            msg:'',
            page:0,
            num_per_page:10, //●取り出すデータ数
            json_data:{},
        };
    },
    methods:{
        login:function(){
            let provider = new firebase.auth.GoogleAuthProvider();
            let self = this;
            firebase.auth().signInWithPopup(provider)
                    .then(function(result) {
                console.log(result.user);
                self.user = result.user;
                self.user_name = result.user.displayName;
                self.user_id = result.user.uid;
                self.message = 'ログインしました。';
                let db = firebase.database();
                let ref = db.ref('board');
                ref.orderByKey()
                        .limitToLast(self.num_per_page)
                        .on('value', function(snapshot){
                    if (firebase.auth().currentUser != null){
                        let arr = [];
                        let data = snapshot.val();
                        for(let item in data){
                            arr.unshift(data[item]);
                        }
                        console.log(arr);
                        self.json_data =arr;
                    } else {
                        self.json_data = {};
                    }
                });
            });
        },
        logout: function(){
            firebase.auth().signOut();
            this.user_name = '';
            this.json_data = {};
            this.message = 'ログアウトしました。';
        },
        doLogin: function(){
            if (firebase.auth().currentUser == null){
                this.login();
            } else {
                this.logout();
            }
        },
        add: function(){
            if (firebase.auth().currentUser == null){
                alert('ログインしないと投稿できません。');
                return;
            }
            let db = firebase.database();
            let user = firebase.auth().currentUser;
            console.log(user);
            let ref = db.ref('board');
            let self = this;
            let d = new Date();
            let dstr = d.getFullYear() + '-' + (d.getMonth() + 1) + '-'
                + d.getDate() + ' ' + d.getHours() + ':' + d.getMinutes()
                + ':' + d.getSeconds();
            let id = d.getTime();
            let data = {
                msg:this.msg,
                user:user.displayName,
                posted:dstr,
                user_id:user.uid,
            };
            firebase.database().ref('board/' + id).set(data);
            this.msg = '';
            this.message = '投稿しました。';
        },
    },
    created: function(){
        if (firebase.auth().currentUser == null){
            this.login();
        }
        console.log(firebase.auth().currentUser);
    }
}
</script>