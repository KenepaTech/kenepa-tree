<template>
    <b-navbar>
        <template #brand>
            <b-navbar-item tag="router-link" :to="{ path: '/' }">
                <img
                    src="../assets/kenepa_logo_text.png"
                    alt="Kenepa Logo with text."
                >
            </b-navbar-item>
        </template>
        <template #start>
            <b-navbar-item href="#">
                Home
            </b-navbar-item>
            <b-navbar-item href="#">
                Programming Languages
            </b-navbar-item>
        </template>
    </b-navbar>
</template>