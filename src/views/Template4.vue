<template>
  <div class="template-page">

 <div class="mt-4 mb-2 ml-5 download-container">
      <v-btn color="primary" @click="downloadNow">Download</v-btn>
    </div>
    <div class="routine-container">
      <div class="routine routine--template4" id="routine" ref="routine">
        <div class="date">
          <input type="text" class="date-input" v-model="routineDate" />
        </div>

        <table class="rSSSFDoutine-table">
          <thead>
            <tr>
              <th class="column1">শ্রেণী</th>
              <th class="column2">১ম পিরিয়ড</th>
              <th class="column3">২য় পিরিয়ড</th>
            </tr>
          </thead>

          <tbody>
            <tr v-for="(r, i) in routine" :key="i">
              <td class="column1">
                <input type="text" v-model="r.class" class="table-input" />
              </td>
              <td class="column2">
                <input type="text" v-model="r.subject1" class="table-input" />
                <input
                  type="text"
                  v-model="r.time1"
                  class="table-input table-input--small"
                />

                <input type="text" v-model="r.subject2" class="table-input" />
                <input
                  type="text"
                  v-model="r.time2"
                  class="table-input table-input--small"
                />
              </td>
              <td class="column3">
                <hr class="blank" v-if="!r.subject3" />
                <template v-else>
                  <input type="text" v-model="r.subject3" class="table-input" />
                  <input
                    type="text"
                    v-model="r.time3"
                    class="table-input table-input--small"
                  />

                  <input type="text" v-model="r.subject4" class="table-input" />
                  <input
                    type="text"
                    v-model="r.time4"
                    class="table-input table-input--small"
                  />
                </template>
              </td>
            </tr>

            <!-- <tr v-for="(r, i) in routine" :key="i">
              <td>
                <div contenteditable="true" :value="r.class">
                  {{ r.class }}
                </div>
              </td>
              <td>
                <div contenteditable="true" :value="r.subject">
                  {{ r.subject }}
                </div>
              </td>
              <td>
                <div contenteditable="true" :value="r.duration">
                  {{ r.duration }}
                </div>
              </td>
            </tr> -->
          </tbody>
        </table>
      </div>
    </div>



  </div>
</template>

<script>
import html2canvas from "html2canvas";


export default {
       components: {
   
    },
  data() {
    return {
      routineDate: "৩ মে এর সময়সূচি ",
      routine: [
        {
          class: "৯ম",
          subject1: "জেনারেল ইলেক্ট্রিক্যাল ওয়ার্কস",
          time1: "(বিকেল ২.৩০)",
          subject2: "করোনা বিষয়ক সচেতনতা",
          time2: "(বিকেল ২.৪৮)",
          subject3: "ফার্ম মেশিনারী",
          time3: "(বিকেল ২.৫০)",
          subject4: "করোনা বিষয়ক সচেতনতা",
          time4: "(বিকেল ৩.০৮)"
        },
        {
          class: "১০ম",
          subject1: "ওয়েল্ডিং অ্যান্ড ফেব্রিকেশন",
          time1: "(বিকেল ৩.১০)",
          subject2: "করোনা বিষয়ক সচেতনতা",
          time2: "(বিকেল ২.২৯)",
          subject3: "",
          time3: "",
          subject4: "",
          time4: ""
        }
      ]
    };
  },
  mounted() {},
  methods: {
    downloadNow() {
      this.$refs.routine.style.border = "none";
      html2canvas(this.$refs.routine).then(canvas => {
        // document.body.appendChild(canvas);
        var a = document.createElement("a");
        // toDataURL defaults to png, so we need to request a jpeg, then convert for file download.
        a.href = canvas
          .toDataURL("image/jpeg")
          .replace("image/jpeg", "image/octet-stream");
        a.download = "template1.jpg";
        a.click();
        this.$refs.routine.style.border = "1px solid #000";
      });
    }
  }
};
</script>

<style>
.template-page{
   font-family: "Hind Siliguri", sans-serif;

}


.routine--template4 .rSSSFDoutine-table th {
  padding: 5px 0;
  font-size: 20px;
}

.routine--template4 .rSSSFDoutine-table td {
  border: 1px solid #fff;
  color: #fff;
  font-size: 18px;
  padding: 7px 0;
  text-align: center;
}

.routine--template4 .column2 {
  width: 232px;
}
.routine--template4 .column2 .table-input {
  max-width: 222px;
}

.routine--template4 .column3 {
  width: 232px;
}

.routine--template4 .table-input {
  width: 222px;
}

.table-input--small {
  font-size: 16px;
}

hr.blank {
  width: 155px;
  border-top: 1px solid #015758;
  border-bottom: 1px solid #2f8788;
  margin: auto;
}


 .column1 {
  min-width: 99px;
} 

 .column1 .table-input {
  max-width: 104px;
}


.column2 .table-input {
  max-width: 288px;
}


.column3 .table-input {
  max-width: 240px;
}





.rSSSFDoutine-table {
    border: 2px solid #fff;
    width: 575px;
    margin-left: 163px;
    margin-top: 6px;
    border-collapse: collapse;
}

.rSSSFDoutine--template2 .rSSSFDoutine-table {
  margin-left: 104px;
  margin-top: 22px;
}

.rSSSFDoutine-table th {
  border: 1px solid #fff;
  border-collapse: collapse;
  color: #fff;
  font-size: 22px;
  padding: 10px 0;
  text-align: center;
  font-weight: bold;
}

.rSSSFDoutine-table td {
  border: 1px solid #fff;
  color: #fff;
  font-size: 25px;
  padding: 10px 0;
  text-align: center;
}
</style>
