<script setup>
import { Link, router } from '@inertiajs/vue3';

defineProps({ session: Object, users: Array });

function destroy(id) {
    if (confirm("Are you sure you want to Delete")) {
        router.delete(`/users/${id}`);
    }
}
</script>

<template>
    <div class="container pt-5">
        <h1 class="text-center">CRUD User</h1>

        <Link class="btn btn-primary mb-3" href="/users/create">Create User</Link>

        <div class="alert alert-success" v-if="session.success">
            {{ session.success }}
        </div>
        <table class="table">
            <thead>
                <tr>
                    <th scope="col">#</th>
                    <th scope="col">Name</th>
                    <th scope="col">Email</th>
                    <th scope="col">Action</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(user, i) in users">
                    <th scope="row">{{ i + 1 }}</th>
                    <td>{{ user.name }}</td>
                    <td>{{ user.email }}</td>
                    <td>
                        <Link class="btn btn-primary btn-sm me-2" :href="`/users/${user.id}/edit`">Edit</Link>
                        <button class="btn btn-danger btn-sm" @click="destroy(user.id)">Delete</button>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>
