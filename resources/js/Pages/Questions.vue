<script setup>
import Layout from '../Shared/Layout.vue';
import QuestionModal from '@/Shared/QuestionModal.vue';
import { ref } from 'vue';

const showQuestionModal = ref(false);

function createQuestion() {
    showQuestionModal.value = true;
}

function destroyModal() {
    showQuestionModal.value = false;
}

</script>

<template>
    <Layout>
        <button @click="createQuestion" class="btn btn-success">Create</button>
        <table class="table table-striped">
            <thead>
                <tr>
                    <th scope="col">#</th>
                    <th scope="col">First</th>
                    <th scope="col">Last</th>
                    <th scope="col">Handle</th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <th scope="row">1</th>
                    <td>Mark</td>
                    <td>Otto</td>
                    <td>@mdo</td>
                </tr>
                <tr>
                    <th scope="row">2</th>
                    <td>Jacob</td>
                    <td>Thornton</td>
                    <td>@fat</td>
                </tr>
                <tr>
                    <th scope="row">3</th>
                    <td colspan="2">Larry the Bird</td>
                    <td>@twitter</td>
                </tr>
            </tbody>
        </table>

        <Teleport to="body">
            <QuestionModal :show="showQuestionModal" @close="destroyModal">
                <template #header>
                    <h5>Add new question</h5>
                </template>
                <template #body>
                    <form>
                        <div class="mb-3">
                            <label for="question" class="form-label">New question</label>
                            <input type="text" class="form-control" id="question">
                        </div>
                        <button type="submit" class="btn btn-primary">Submit</button>
                    </form>
                </template>
                <template #footer>

                </template>
            </QuestionModal>
        </Teleport>
    </Layout>
</template>