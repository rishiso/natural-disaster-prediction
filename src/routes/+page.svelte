<script lang="ts">
  import { Input } from "$lib/components/ui/input";
  import * as Tabs from "$lib/components/ui/tabs";
  let googleMapsUrl = "https://www.google.com/maps/embed/v1/place?key=AIzaSyCPl0t1z471mvNMji79lGnQ7FbSzrkuXQY&q=Georgia+Tech";

  function handleKeyDown(event: KeyboardEvent) {
      const { key, target } = event as unknown as { key: string; target: { value: any } };
      if (key === "Enter") {
          const address = target.value;
          googleMapsUrl = `https://www.google.com/maps/embed/v1/place?key=AIzaSyCPl0t1z471mvNMji79lGnQ7FbSzrkuXQY&q=${encodeURIComponent(address)}`;
      }
  }
</script>

<div class="background-container">
  <img src="src/lib/pictures/green5.jpeg" alt="Background" class="background-image" />
  <h1 class="title text-black">Natural Disaster Prediction</h1>
  <p class="subtitle">Search any address to see its risk from flooding</p>
  <form class="input-form flex w-full max-w-sm items-center space-x-2">
      <Input 
          type="Address" placeholder="Ex: 742 Evergreen Terrace, Springfield, IL 62704, USA" 
          on:keydown={handleKeyDown}
          style="outline: none;" 
          {...$$restProps}
      />
  </form>
</div>

<div class="content-container flex flex-col items-center justify-center w-full">
  <Tabs.Root value="account" class="w-full">
    <Tabs.List class="flex justify-center space-x-4 mb-4">
      <Tabs.Trigger class="flex-1 text-center shadow-xl " value="account">About</Tabs.Trigger>
      <Tabs.Trigger class="flex-1 text-center shadow-xl " value="map">Map</Tabs.Trigger>
      <Tabs.Trigger class="flex-1 text-center shadow-xl " value="password">Team</Tabs.Trigger>
    </Tabs.List>
    <Tabs.Content value="account">
      <!-- Content for About -->
      <div class="flex flex-col items-center bg-[rgb(140,186,134)] p-8">
        <div class="w-full max-w-4xl bg-green-100 p-6 rounded-xl shadow-lg flex flex-col items-center justify-center">
          <h2 class="font-bold text-3xl text-green-800 mb-8 text-center">OUR GOAL</h2>
          <div class="grid md:grid-cols-2 gap-2 w-full">
            <p class="text-green-700">
              Climate change is a pressing global issue with irreversible effects on nature and societies. Climate tech is a crucial emerging field focused on developing technologies to tackle climate change impacts, such as extreme weather events, rising sea levels, and shifting precipitation patterns. Without immediate action, these issues will worsen. Currently, predicting natural disasters is challenging due to complex natural systems, data gaps, and model limitations.
            </p>
            <p class="text-green-700">
              Our approach uses machine learning techniques like transfer learning and computer vision to analyze Google Earth Engine Datasets for regional climate patterns. We employ computer vision to process global satellite data and link it with climate data to assess natural disaster likelihood. Transfer learning then tailors the analysis to user-inputted regions, considering factors like climate trends, dryness, humidity, and surrounding influences. Our end product provides users with analyses of potential natural disasters, estimated timeframes, and more for their selected region.
            </p>
          </div>
        </div>
      </div>
    </Tabs.Content>

    <Tabs.Content value="map">
      <div class="flex flex-col items-center bg-[rgb(140,186,134)] p-8">
        <iframe
          title="Map"
          src={googleMapsUrl}
          width="800"
          height="600"
          style="border:0; margin-top: 20px;"
        ></iframe>
      </div>
    </Tabs.Content>
    
    <Tabs.Content value="password">
    <div class="flex flex-col items-center bg-[rgb(140,186,134)] p-8">
      <div class="w-full max-w-4xl bg-green-100 p-6 rounded-xl shadow-lg flex flex-col items-center justify-center">
        <h2 class="font-bold text-3xl text-green-800 mb-8 text-center">OUR TEAM</h2>
        <div class="grid md:grid-cols-2 gap-2 w-full">
          <div class="text-center text-green-700">Sidharth Subbarao</div>
          <div class="text-center text-green-700">Rishi Soni</div>
          <div class="text-center text-green-700">Cole McGinnis</div>
          <div class="text-center text-green-700">Pranav Narala</div>
          <div class="text-center text-green-700">Aneeta Thokkadam</div>
          <div class="text-center text-green-700">Varun Vudathu</div>
          <div class="text-center text-green-700">Rohit Prasanna</div>
          <div class="text-center text-green-700">Aman Patel</div>
          <div class="text-center text-green-700">Ananya Kumar</div>
          <div class="text-center text-green-700">Shitij Govil</div>
          <div class="text-center text-green-700">Kevin Park</div>
          <div class="text-center text-green-700">Tia Kungwani</div>
          <div class="text-center text-green-700">Pranav Somu</div>
          <div class="text-center text-green-700">John Kucharewicz</div>
          <div class="text-center text-green-700">Leo Jiang</div>
          <div class="text-center text-green-700">Sai Guntabonu</div>
        </div>
      </div>
    </div>
  </Tabs.Content>

  </Tabs.Root>

</div>

  <style>
    .background-container {
      width: 100%;
      height: 500px;
      position: relative;
      overflow: hidden;
    }
  
    .background-image {
      width: 100%;
      height: 100%;
      object-fit: cover;
      position: relative;
      top: 0;
      left: 0;
      z-index: 1;
    }

    .background-image::after {
    content: '';
    position: absolute;
    top: -10px; right: -10px; bottom: -10px; left: -10px; 
    box-shadow: 0 0 15px 10px white; 
    z-index: -1;
    }

    .title {
      position: absolute;
      top: 40%;
      left: 50%;
      transform: translate(-50%, -50%);
      z-index: 1;
      color: white;
      font-weight: bold;
      font-size: 3em;
      text-align: center;
    }
  
    .subtitle {
      position: absolute;
      top: 52%; 
      left: 50%;
      transform: translate(-50%, -50%);
      z-index: 1;
      color: white;
      font-size: 1.5em; 
      text-align: center;
      max-width: 80%;
    }
  
    .input-form {
    position: absolute;
    top: 60%; 
    left: 50%;
    transform: translate(-50%, -50%);
    z-index: 2;
    width: 100%; 
    max-width: 600px;
  }

  .content-container {
        background-color: rgb(140, 186, 134);
        flex:1;
    }
  
  .map-container {
    width: 100%;
    height: 500px;
    position: relative;
    overflow: hidden;
  }

  </style>