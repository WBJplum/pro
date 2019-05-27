<template>
  <div>
    <h2>{{list.title}}</h2>
    </div>
</template>

<script>

export default {
  data () {
    return {
     list:[]
    }
  },

   methods: { 
     requestData(a){
       var that=this;
       var apl=''+a;
    wx.request({
      url:a,
      header: {
        'content-type': 'application/json'
      },
      success: function(res) {
        console.log(res.data)
      }
    })
     }     
  },
  onload: function(options){
    var a=options.a;
    this.requestData(a);
  }

}
</script>
