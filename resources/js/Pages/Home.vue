<script setup>
import { Link } from '@inertiajs/vue3';

defineProps({ page: String });
</script>

<template>
    <div class="text-center pb-5">
        <h1>{{ page }}</h1>

        <Link class="btn btn-primary mt-3 rounded-pill" href="/users">CRUD User</Link>
    </div>
</template>
