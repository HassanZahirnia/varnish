<template>
    <div class="demo py-[40px] px-[64px]">

        <!-- Title -->
        <h1 class="text-[32px] font-semibold leading-snug -tracking-[.7px] mb-12">
            TextBox - Playground
        </h1>

        <!-- Textboxes -->
        <div class="flex flex-col gap-y-4 max-w-[300px]">

            <!-- Heading -->
            <h2 class="font-semibold mt-6">
                TextBox (plain)
            </h2>

            <!-- TextBox (plain) -->
            <v-textbox v-model="one"></v-textbox>

            <!-- Heading -->
            <h2 class="font-semibold mt-6">
                TextBox (with icon)
            </h2>

            <!-- TextBox (with icon) -->
            <v-textbox v-model="two"
                       icon="fas fa-user">
            </v-textbox>

            <!-- Heading -->
            <h2 class="font-semibold mt-6">
                TextBox (with custom label)
            </h2>

            <!-- TextBox (with custom label) -->
            <v-textbox v-model="three"
                       label="First name"
                       icon="fas fa-user">
            </v-textbox>

            <!-- Heading -->
            <h2 class="font-semibold mt-6">
                TextBox (Multi Line)
            </h2>

            <!-- TextBox (Multi Line) -->
            <v-textbox :lines="5"
                       v-model="four"
                       label="Biography"
                       icon="fas fa-comment">
            </v-textbox>

            <!-- Heading -->
            <h2 class="font-semibold mt-6">
                Populated TextBox (with custom label)
            </h2>

            <!-- Populated TextBox (with custom label) -->
            <v-textbox label="First name"
                       icon="fas fa-user"
                       v-model="input_content">
            </v-textbox>

            <!-- Heading -->
            <h2 class="font-semibold mt-6">
                Populated TextBox (Multi Line)
            </h2>

            <!-- Populated TextBox (Multi Line) -->
            <v-textbox :lines="5"
                       label="Biography"
                       icon="fas fa-comment"
                       v-model="multi_line_content">
            </v-textbox>


        </div>

    </div>
</template>

<script>
    import TextBoxComponent from '../../../src/components/textbox.vue';

    export default
    {
        components : {
            'v-textbox' : TextBoxComponent,
        },

        data() {
            return {
                one                : '',
                two                : '',
                three              : '',
                four               : '',
                input_content      : 'John',
                multi_line_content : 'Lorem ipsum, dolor sit amet consectetur adipisicing elit. Tempore, aperiam voluptas, labore error porro distinctio dolorem iure nam assumenda rerum laborum.',
            }
        },
    }
</script>