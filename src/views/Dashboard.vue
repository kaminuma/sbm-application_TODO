<template>
  <div>
    <h2>ダッシュボード</h2>
    <p v-if="user">ようこそ, {{ user.email }} さん</p>
    <button @click="logout">ログアウト</button>
  </div>
</template>

<script>
import { ref, onMounted } from "vue";
import { supabase } from "../supabase";
import { useRouter } from "vue-router";

export default {
  setup() {
    const user = ref(null);
    const router = useRouter();

    onMounted(async () => {
      const { data } = await supabase.auth.getUser();
      if (data) {
        user.value = data.user;
      } else {
        router.push("/");
      }
    });

    const logout = async () => {
      await supabase.auth.signOut();
      router.push("/");
    };

    return { user, logout };
  },
};
</script>
