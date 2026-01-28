<template>
  <div class="flex justify-center items-center min-h-[80vh]">
    <div class="w-full max-w-sm bg-white rounded-xl p-8 border border-gray-100">

      <header class="text-center mb-2">
        <h1 class="text-xl font-bold text-gray-900">
          Welcome <span class="text-[#FF1493]">Back</span>
        </h1>
        <p class="text-sm text-gray-400 mt-1">
          Sign in to your account
        </p>
      </header>

      <form class="space-y-5">
        <Input
          label="Email"
          type="email"
          v-model="email"
          placeholder="hello@modern.com"
        />

        <Input
          label="Password"
          type="password"
          v-model="password"
          placeholder="••••••••"
        />
        <BaseBtn variant="primary" class="w-full">
          Sign In
        </BaseBtn>
      </form>
      <p class="text-center text-sm text-gray-500 mt-2">
        Don't have an account?
        <RouterLink to="/register" class="font-medium text-gray-900 hover:text-[#FF1493] hover:underline cursor-pointer transition">
          Sign up
        </RouterLink>
      </p>

    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import Input from '../components/ui/Input.vue'
import BaseBtn from '../components/ui/BaseBtn.vue'

const email = ref('')
const password = ref('')
</script>