<template>
    <div class="listing-card">
        <b-card no-body class="overflow-hidden mb-3" style="max-height: 150px;" ref="listingcard">
            <b-link v-on:click="$router.push(`walks/${user_id}/${walk_id}`)" class="stretched-link card-link">
                <b-row class="row-in-card" no-gutters>
                    <b-col cols="2" align-self="center">
                        <b-card-img :src="image" alt="Profile image" class="rounded-circle"
                                    style="max-height: 120px; max-width: 120px"></b-card-img>
                    </b-col>
                    <b-col cols="10">
                        <b-card-body class="pt-2 pb-2" :title="title">
                            <h6 class="card-subtitle text-muted mb-2">{{ first_name }} {{ last_name }} in {{ location }}</h6>
                            <b-card-text>
                                <b-row class="pl-2 pr-2 mb-1" no-gutters>
                                    <b-col sm="4">{{date}}</b-col>
                                    <b-col sm="4">{{time}}</b-col>
                                    <b-col sm="4">{{duration}} minutes</b-col>
                                </b-row>
                                <div class="description text-secondary">{{ description }}</div>
                            </b-card-text>
                        </b-card-body>
                    </b-col>
                </b-row>
            </b-link>
        </b-card>
    </div>
</template>

<script>
    export default {
        name: 'WalkListing',
        props: ['walk_id', 'title', 'date', 'time', 'duration', 'location', 'description', 'user_id', 'first_name', 'last_name', 'happening', 'image'],
        mounted() {
            if (this.happening === "now") {
                this.$refs.listingcard.style.backgroundColor = "#b5f4b5";
            }
        }
    }


</script>

<style lang="scss" scoped>

    .card {
        box-shadow: 0px 0px 15px #bbb;
    }

    .card:hover {
        box-shadow: 0px 0px 15px #666;
    }

    .description {
        white-space: nowrap;
        overflow: hidden;
        text-overflow: ellipsis;
    }

    .listing-card .card-link,
    .listing-card .card-link:hover {
        color: inherit;
    }
  
    .listing-card .card {
      padding: 10px;
      border: 10px;
      margin: 0 auto 10px; 
    }

</style>
