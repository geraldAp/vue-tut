<template>
    <div class="container mb-3 mt-3">
        <form action="">
            <div class="row">
                <div class="col-md-8">
                    <div class="mb-3">
                        <label class="form-label">
                            Page Title
                        </label>
                        <input v-model="pageTitle" type="text" class="form-control">
                    </div>
                    <div class="mb-3">
                        <label for="" class="form-label"></label>
                        <textarea v-model="content" name="" class="form-control" id="" cols="30" rows="10">
                        </textarea>
                    </div>
                </div>
                <div class="col">
                    <div class='mb-3'>
                        <label for="" class="form-label">
                            Link Text
                        </label>
                        <input v-model="linkText" type="text" class="form-control">
                    </div>
                    <div class='mb-3'>
                        <label for="">
                            Link url
                        </label>
                        <input v-model="linkUrl" type="text" class="form-control">
                    </div>
                    <div class='row mb-3'>
                        <div class="form-check ">
                            <input v-model="published" type="checkbox" class="form-check-input">
                            <label for="gridCheck1" class="form-check-label">Published</label>
                        </div>
                    </div>
                </div>
            </div>
            <div class="mb-3">
                <button class="btn btn-primary" :disabled="isFormInvalid" @click.prevent="submitForm">
                    Create Page
                </button>
            </div>
        </form>
    </div>
</template>

<script>
export default {
    props: ['pageCreated'],
    data() {
        return {
            pageTitle: '',
            content: '',
            linkText: '',
            linkUrl: '',
            published: true
        };
    },
    computed: {
        isFormInvalid() {
            return !this.pageTitle || !this.content || !this.linkText || !this.linkUrl;
        }
    },
    methods: {
        submitForm() {
            if (!this.pageTitle || !this.content || !this.linkText || !this.linkUrl) {
                alert('Please fill up the form');
                return;
            }

            // Modify this line to match your data structure
            this.pageCreated({
                link: {
                    text: this.linkText,
                    url: this.linkUrl
                },
                title: this.pageTitle,
                content: this.content,
                published: this.published
            });
        }
    }
};
</script>
