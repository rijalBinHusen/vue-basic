<template>
    <div class="backdrop" @click.self="closeModal">
        <div class="modal">
            <h1>{{header}}</h1>
            <p>{{content}}</p>
            <slot>
                <!-- Will show when the parent didnt throw a slot template -->
                default content
            </slot>
            <div class="actions">
                <slot name="action"></slot>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "Modal",
    methods: {
        closeModal() {
            this.$emit("toggleModal")
        }
    },
    props: {
        header: {
            type: String,
            required: true,
        },
        content: {
            type: String,
            required: true
        }
    }
}
</script>

<style scoped>
    .modal {
        width: 400px;
        padding: 20px;
        margin: 100px auto;
        background: white;
        border-radius: 10px;
    }

    .backdrop {
        top: 0;
        position: fixed;
        background: rgba(0,0,0,0.5);
        width: 100%;
        height: 100%
    }

    .modal .actions {
        text-align: center;
        margin:30px 0 10px 0;
    }

    .modal .actions a {
        color: #333;
        padding: 8px;
        border: 1px solid #eee;
        border-radius: 4px;
        text-decoration: none;
        margin: 10px;
    }

    .modal h1 {
        color: #03cfb4;
        border: none;
        padding: 0;
    }

    .modal.sale {
        background: crimson;
        color: white;
    }

    .modal.sale h1 {
        color: white
    }
</style>