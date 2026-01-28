<template>
  <div class="flex justify-center items-center min-h-[80vh]">
    <div class="w-full max-w-sm bg-white rounded-xl p-8 border border-gray-100">

      <!-- Header -->
      <header class="text-center mb-2">
        <h1 class="text-xl font-bold text-gray-900">
          Create <span class="text-[#FF1493]">Account</span>
        </h1>
        <p class="text-sm text-gray-400 mt-1">
          Sign up to get started
        </p>
      </header>

      <!-- Form -->
      <form class="space-y-5">
        <Input
          label="Full Name"
          type="text"
          v-model="name"
          placeholder="John Doe"
        />

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
          Sign Up
        </BaseBtn>
      </form>

      <!-- Footer -->
      <p class="text-center text-sm text-gray-500 mt-2">
        Already have an account?
        <RouterLink to="/login" class="font-medium text-gray-900 hover:text-[#FF1493] hover:underline cursor-pointer transition">
          Sign in
        </RouterLink>
      </p>

    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import Input from '../components/ui/Input.vue'
import BaseBtn from '../components/ui/BaseBtn.vue'

const name = ref('')
const email = ref('')
const password = ref('')
</script>