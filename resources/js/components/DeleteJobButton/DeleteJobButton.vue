<script type="text/ecmascript-6">
    export default {
        props: {
            job_id: {
                required: true,
                type: Number,
            },
        },
        data: function () {
            return { };
        },
        methods: {
            /**
             * Delete a job.
             */
            deleteJob: function () {
                return this.$http.delete('/horizon/api/jobs/' + this.job_id)
                    .then(response => {
                        this.$emit('deleted:job_id', this.job_id);
                        alert(response.data.job_id + ' is deleted.');
                    })
                    .catch(error => {
                        console.log(error);
                        alert('Job cannot delete.');
                    });
            }
        }
    }
</script>

<template>
    <button type="button" @click="deleteJob">Delete</button>
</template>
