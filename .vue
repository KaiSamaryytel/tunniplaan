<script>
    const http = require("tns-core-modules/http");
    export default {
        data() {
            return {
                aine: "1",
                opetaja: "2"
            };
        },
        created() {
            this.getMyShedule();
        },
        methods: {

            getMyShedule() {
                var url =
                    "https://tkhk.siseveeb.ee/veebilehe_andmed/tunniplaan?nadal=2019-01-21&grupp=1223";


                http.request({
                    url: url,
                    method: "GET"
                }).then(this.parseResponse);
            },
            parseResponse(response) {
                var schedule = response.content.toJSON();
                var last = schedule["tunnid"]["2019-01-25"]["2019-01-26"][4];
                console.log(last);
                this.opetaja = last["opetaja"]
                this.aine = last["aine"]
                    return true:
            }
        }
    };
</script>