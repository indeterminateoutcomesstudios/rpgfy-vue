<template>
    <div class="two-third card">
        <header>Quest Report</header>
        <div>
            <table class="primary">
                <thead>
                    <tr>
                        <th>Between</th>
                        <th>Completed</th>
                        <th>Failed</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="questReport in questReportCollection">
                        <td>{{questReport.range.start}} - {{questReport.range.end}}</td>
                        <td>{{questReport.completed}}</td>
                        <td>{{questReport.failed}}</td>
                    </tr>
                </tbody>
            </table>
        </div>
        <footer>
            
        </footer>
    </div>
</template>
<script>
import QuestReportService from "@/service/quest-report";
import mutationTypes from "@/store/mutation-types";
export default {
    data()
    {
        return { questReportCollection :[] }
    },
    beforeCreate()
    {
        this.$store.commit(mutationTypes.CHANGE_BACKGROUND, 'background-plain')
        return QuestReportService.get('/quest-report')
            .then(questReportCollection => this.questReportCollection = questReportCollection)
    }
}
</script>
