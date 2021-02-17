<template>
  <ion-page>
    <ion-header :translucent="true">
      <ion-toolbar>
        <ion-title>Blank</ion-title>
      </ion-toolbar>
    </ion-header>
    
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Blank</ion-title>
        </ion-toolbar>
      </ion-header>
    
      <div id="container">
        <strong>Ready to create an app?</strong>
        <p>Start with Ionic <a target="_blank" rel="noopener noreferrer" href="https://ionicframework.com/docs/components">UI Components</a></p>
        <Highcharts :options="chartOptions" />
      </div>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { IonContent, IonHeader, IonPage, IonTitle, IonToolbar } from '@ionic/vue';
import { defineComponent } from 'vue';
import Highcharts from 'highcharts';
import { createHighcharts } from 'vue-highcharts';

export default defineComponent({
  name: 'Home',
  components: {
    IonContent,
    IonHeader,
    IonPage,
    IonTitle,
    IonToolbar,
    Highcharts: createHighcharts('Highcharts', Highcharts)
  },
  ionViewWillEnter () {
    let chartOptions = {
      title: {
          text: 'Server Stats'
      },
      subtitle: {
          text: 'uptime'
      },
      xAxis: {
          type: 'datetime'
      },
      yAxis: {
          title: {
          text: 'y title'
          }
      },
      series: [{
          name: 'uptime',
          data: [{x: Date.now(), y: 0}],
          yAxis: 0,
          visible: true
      }]
    }
    return chartOptions
  }
});
</script>

<style scoped>
#container {
  text-align: center;
  
  position: absolute;
  left: 0;
  right: 0;
  top: 50%;
  transform: translateY(-50%);
}

#container strong {
  font-size: 20px;
  line-height: 26px;
}

#container p {
  font-size: 16px;
  line-height: 22px;
  
  color: #8c8c8c;
  
  margin: 0;
}

#container a {
  text-decoration: none;
}
</style>