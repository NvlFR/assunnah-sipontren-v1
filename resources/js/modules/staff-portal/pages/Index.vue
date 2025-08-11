<script setup>
    const features = [
      {
        icon: 'school',
        title: 'PPBD',
        description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut.'
      },
      {
        icon: 'settings',
        title: 'SYSTEM',
        description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut.'
      },
      {
        icon: 'auto_stories',
        title: 'AKADEMIK',
        description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut.'
      },
      {
        icon: 'groups', 
        title: 'KESISWAAN',
        description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut.'
      },
      {
        icon: 'wallet',
        title: 'ABSENSI',
        description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut.'
      },
      {
        icon: 'task_alt',
        title: 'KEUANGAN',
        description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut.'
      }
    ];
</script>

<template>
  <authenticated-layout>
    <q-page>
      <div
        class="relative-position overflow-hidden text-center bg-grey-2 rounded-borders q-mb-xl"
        style="padding: 80px 20px"
      >
        <q-icon
          name="arrow_back"
          color="black"
          style="
            position: absolute;
            opacity: 0.3;
            font-size: 34px;
            left: 40px;
            top: 50%;
            transform: translateY(-50%);
          "
        />

        <q-icon
          name="arrow_forward"
          color="black"
          style="
            position: absolute;
            opacity: 0.3;
            font-size: 34px;
            right: 40px;
            top: 50%;
            transform: translateY(-50%);
          "
        />

        <q-icon
          name="more_horiz"
          color="black"
          style="position: absolute; font-size: 20px; left: 40px; bottom: 20px"
        />

        <h1 class="text-h4 text-weight-bold q-ma-none">ALL INFORMATION</h1>
      </div>

      <div class="row q-col-gutter-xl">

      <div
        v-for="feature in features"
        :key="feature.title"
        class="col-12 col-sm-6 col-md-4"
      >
        <q-card flat bordered class="full-height text-center q-pa-md">
          <q-card-section>
            <q-avatar size="80px" font-size="45px" color="primary" text-color="white" :icon="feature.icon" />

            <div class="text-h6 text-weight-bold q-mt-md">{{ feature.title }}</div>

            <p class="text-caption text-grey-8 q-mt-sm">{{ feature.description }}</p>

          </q-card-section>
        </q-card>
      </div>
    </div>
    </q-page>
  </authenticated-layout>
</template>

<style scoped>
.app-icon-btn {
  color: #555 !important;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 140px;
  text-align: center;
  color: inherit;
  text-decoration: none;
  cursor: pointer;
  user-select: none;
  border-radius: 8px;
  transition: background-color 0.5s, color 0.5s;
  padding: 12px; /* untuk memberi jarak internal agar seimbang */
}

.app-icon-btn:hover {
  background-color: #eee;
  color: rgb(54, 158, 255) !important;
  transition: background-color 0.5s, color 0.5s;
}

.app-icon-btn > div.text-subtitle2 {
  width: 100%;
  text-align: center;
}
</style>
