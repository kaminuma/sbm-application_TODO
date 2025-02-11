<template>
  <div>
    <h2>ログイン</h2>
    <input v-model="email" type="email" placeholder="メールアドレス" />
    <input v-model="password" type="password" placeholder="パスワード" />
    <button @click="signUp">新規登録</button>
    <button @click="login">ログイン</button>
    <button @click="logout">ログアウト</button>
    <p v-if="user">現在ログイン中: {{ user.email }}</p>
  </div>
</template>

<script>
import { ref, onMounted } from "vue";
import { supabase } from "../supabase";

export default {
  setup() {
    const email = ref("");
    const password = ref("");
    const user = ref(null);

    onMounted(async () => {
      const { data } = await supabase.auth.getUser();
      if (data) user.value = data.user;
    });

    const signUp = async () => {
      const { data, error } = await supabase.auth.signUp({
        email: email.value,
        password: password.value,
      });
      if (error) console.error("サインアップエラー:", error.message);
      else user.value = data.user;
    };

    const login = async () => {
      const { data, error } = await supabase.auth.signInWithPassword({
        email: email.value,
        password: password.value,
      });
      if (error) console.error("ログインエラー:", error.message);
      else user.value = data.user;
    };

    const logout = async () => {
      const { error } = await supabase.auth.signOut();
      if (error) console.error("ログアウトエラー:", error.message);
      else user.value = null;
    };

    return { email, password, user, signUp, login, logout };
  },
};
</script>
