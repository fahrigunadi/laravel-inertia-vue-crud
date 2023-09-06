<script setup>
import { useForm } from '@inertiajs/vue3';

const form = useForm({
    name: null,
    email: null,
    password: null,
});
</script>

<template>
    <div class="container pt-5">
        <h1 class="text-center">CRUD User</h1>

        <form @submit.prevent="form.post('/users')">
            <div class="mb-3">
                <label class="form-label">Name</label>
                <input v-model="form.name" name="name" :class="'form-control' + (form.errors.name ? ' is-invalid' : '')">

                <div class="invalid-feedback" v-if="form.errors.name">
                    {{ form.errors.name }}
                </div>
            </div>

            <div class="mb-3">
                <label class="form-label">Email address</label>
                <input v-model="form.email" name="email" type="email" :class="'form-control' + (form.errors.name ? ' is-invalid' : '')">

                <div class="invalid-feedback" v-if="form.errors.email">
                    {{ form.errors.email }}
                </div>
            </div>

            <div class="mb-3">
                <label class="form-label">Password</label>
                <input v-model="form.password" name="password" type="password" :class="'form-control' + (form.errors.password ? ' is-invalid' : '')">

                <div class="invalid-feedback" v-if="form.errors.password">
                    {{ form.errors.password }}
                </div>
            </div>

            <button :disabled="form.processing" type="submit" class="btn btn-primary">Submit</button>
        </form>
    </div>
</template>
