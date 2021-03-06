## Live example

<eg-base>
  <eg-basic-marker-cluster />
</eg-base>

## Source code

```html
<body>
  <div id="root">
    <gmap-map :center="center" :zoom="7" style="width: 100%; height: 500px">
      <gmap-cluster>
        <gmap-marker v-for="(m, index) in markers"
          :position="m.position"
          :clickable="true" :draggable="true"
          @click="center=m.position"
          :key="index"
          ></gmap-marker>
      </gmap-cluster>
    </gmap-map>
  </div>

  <script src="https://cdnjs.cloudflare.com/ajax/libs/vue/2.5.0/vue.js"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/markerclustererplus/2.1.4/markerclusterer.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/gmap-vue@1.0.0/dist/gmap-vue.min.js"></script>

  <script>
    Vue.use(GmapVue, {
      load: {
        key: 'AIzaSyDf43lPdwlF98RCBsJOFNKOkoEjkwxb5Sc'
      },
    });

    document.addEventListener('DOMContentLoaded', function() {
      // gmapCluster *must* be manually imported
      Vue.component('gmap-cluster', GmapVue.Cluster);

      new Vue({
        el: '#root',
        data: {
          center: {
            lat: 10.0,
            lng: 10.0
          },
          markers: [{
            position: {
              lat: 10.0,
              lng: 10.0
            }
          }, {
            position: {
              lat: 11.0,
              lng: 11.0
            }
          }]
        },
      });
    });
  </script>
</body>
```
