<script setup lang="ts">
import { Head, Link } from '@inertiajs/vue3';
import { dashboard, login, register } from '@/routes';

withDefaults(
    defineProps<{
        canRegister: boolean;
    }>(),
    {
        canRegister: true,
    },
);
</script>

<template>
    <Head title="Welcome">
    
    </Head>
    <div
        class="flex min-h-screen flex-col items-center bg-[#FDFDFC] p-6 text-[#1b1b18] lg:justify-center lg:p-8 dark:bg-[#0a0a0a]"
    >
        <header
        >
            <nav class="flex items-center justify-end gap-100">
                <Link
                    v-if="$page.props.auth.user"
                    :href="dashboard()"
                >
                    Dashboard
                </Link>
                <template v-else>
                    <Link
                        :href="login()"
                    >
                        Log in
                    </Link>
                    <Link
                        v-if="canRegister"
                        :href="register()"
                    >
                        Register
                    </Link>
                </template>
            </nav>
        </header>
    
    </div>
</template>
