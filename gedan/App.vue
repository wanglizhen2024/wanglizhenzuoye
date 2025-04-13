<template>
    <div class="container">
      <!-- 热门歌手 -->
      <section class="section">
        <h2 class="section-title">热门歌手</h2>
        <ItemGrid :items="artists">
          <template #item="{ item }">
            <div class="artist-card">
              <!-- eslint-disable-next-line vue/no-parsing-error -->
              
              <p class="artist-name">{{ item.name }}</p >
            </div>
          </template>
        </ItemGrid>
      </section>
  
      <!-- 榜单 -->
      <section class="section">
        <h2 class="section-title">榜单</h2>
        
        <div class="charts-wrapper">
          <!-- 新歌榜 -->
          <div class="chart-container">
            <ItemGrid :items="newSongs.tracks">
              <template #header>
                <div class="chart-header">
                  <h3 class="chart-title">新歌榜</h3>
                  <p class="chart-description">{{ newSongs.description }}</p >
                </div>
              </template>
              <template #item="{ item, index }">
                <div class="chart-item">
                  <span class="chart-rank">{{ index + 1 }}</span>
                  <span class="chart-name">{{ item.name }}</span>
                </div>
              </template>
            </ItemGrid>
          </div>
  
          <!-- 热歌榜 -->
          <div class="chart-container">
            <ItemGrid :items="hotSongs.tracks">
              <template #header>
                <div class="chart-header">
                  <h3 class="chart-title">热歌榜</h3>
                  <p class="chart-description">{{ hotSongs.description }}</p >
                </div>
              </template>
              <template #item="{ item, index }">
                <div class="chart-item">
                  <span class="chart-rank">{{ index + 1 }}</span>
                  <span class="chart-name">{{ item.name }}</span>
                </div>
              </template>
            </ItemGrid>
          </div>
  
          <!-- 原创榜 -->
          <div class="chart-container">
            <ItemGrid :items="originSongs.tracks">
              <template #header>
                <div class="chart-header">
                  <h3 class="chart-title">原创榜</h3>
                  <p class="chart-description">{{ originSongs.description }}</p >
                </div>
              </template>
              <template #item="{ item, index }">
                <div class="chart-item">
                  <span class="chart-rank">{{ index + 1 }}</span>
                  <span class="chart-name">{{ item.name }}</span>
                </div>
              </template>
            </ItemGrid>
          </div>
        </div>
      </section>
    </div>
  </template>
  
  <script>
  import ItemGrid from "./components/ItemGrid.vue";
  import newSongs from "./data/newSong.js";
  import hotSongs from "./data/hotSong.js";
  import originSongs from "./data/originSong.js";
  import artists from "./data/artist.js";
  
  export default {
    components: {
      ItemGrid,
    },
    data() {
      return {
        newSongs,
        hotSongs,
        originSongs,
        artists,
      };
    },
    methods: {
      handleImageError(e) {
        e.target.src = 'https://via.placeholder.com/80'; 
      }
    }
  };
  </script>
  
  <style scoped>
  .container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 20px;
  }
  
  .section {
    margin-bottom: 40px;
  }
  
  .section-title {
    font-size: 24px;
    font-weight: bold;
    margin-bottom: 20px;
    border-bottom: 1px solid #eee;
    padding-bottom: 10px;
  }
  
  .charts-wrapper {
    display: flex;
    flex-wrap: wrap;
    gap: 20px;
  }
  
  .chart-container {
    flex: 1;
    min-width: 300px;
  }
  
  .artist-card {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin: 0 10px;
    cursor: pointer;
    transition: transform 0.2s;
  }
  
  .artist-card:hover {
    transform: scale(1.05);
  }
  
  .artist-img {
    width: 80px;
    height: 80px;
    border-radius: 50%;
    object-fit: cover;
    margin-bottom: 5px;
    background-color: #f5f5f5;
  }
  
  .artist-name {
    font-size: 14px;
    text-align: center;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
    max-width: 100px;
  }
  
  .chart-header {
    margin-bottom: 15px;
  }
  
  .chart-title {
    font-size: 18px;
    font-weight: bold;
    margin-bottom: 5px;
  }
  
  .chart-description {
    font-size: 12px;
    color: #666;
  }
  
  .chart-item {
    display: flex;
    align-items: center;
    margin-bottom: 10px;
    padding: 5px;
    border-radius: 4px;
  }
  
  .chart-item:hover {
    background-color: #f5f5f5;
  }
  
  .chart-rank {
    font-weight: bold;
    margin-right: 10px;
    width: 20px;
    text-align: center;
  }
  
  .chart-name {
    flex: 1;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }
  
  @media (max-width: 768px) {
    .charts-wrapper {
      flex-direction: column;
    }
    
    .chart-container {
      min-width: 100%;
    }
  }
  </style>
