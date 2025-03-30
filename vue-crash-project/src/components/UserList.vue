<script>
    export default {
        props: [
            users: Array    
        ],
    };
</script>

<template>
    <!-- Users List -->
    <div>
        <table v-if="user.length" class="w-full bg-white rounded-md">
            <tr>
                <th>
                    <h3>Users List</h3>
                </th>
            </tr>
            <tr>
                <td>
                    <li v-for="user in users" :key="user">
                        <p>
                            {{ user.name }}
                        </p>
                        <p>
                            {{ user.email }}
                        </p>
                    </li>
                </td>
            </tr>
        </table>
    </div>
</template>