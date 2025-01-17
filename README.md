# MindAR Image Tracking with 3D Model Animation

This project demonstrates how to create an interactive **Augmented Reality (AR)** experience using **MindAR** and **A-Frame**. The AR experience is triggered by an **image target**, where a 3D model appears and animates on top of the image. The model rotates and scales, with proper lighting effects for an immersive experience.

---

## 📖 **Project Overview**

This AR project utilizes the **MindAR** and **A-Frame** libraries to display a **3D model** (Apple Vision Pro) triggered by an image target. The model includes rotation and scaling animations, with various lighting effects to enhance the visual appeal. The AR experience is set up using an **HTML** structure, integrated with the **MindAR** and **A-Frame** scripts.

---

## 🛠️ **Setup and Usage**

### Step 1: **View the Project**

To view the live demo of the AR project, visit the following link:

- [Project Demo](https://webarimagetrack.glitch.me)

---

### Step 2: **Create Image Targets**

To create image targets (markers) for the AR application, follow these steps:

1. Go to the [MindAR Image Target Compiler](https://hiukim.github.io/mind-ar-js-doc/tools/compile/).
2. Upload your image to generate a **`.mind` file**.
3. Download the `.mind` file and host it publicly on a server.

---

### Step 3: **Host Your AR Project**

To host the project on **Glitch**, follow these steps:

1. Go to [Glitch Dashboard](https://glitch.com/dashboard) and log in (or create an account).
2. Click on **New Project** and select **Create a New Project**.
3. Replace the default code in the editor with the HTML provided in this repository.
4. Upload your `.mind` file to the project files in Glitch.
5. Make sure to update the `mindar-image` source with the URL of your hosted `.mind` file.
6. Click on the **Show** button to view the project.

---

### Step 4: **Customize the AR Experience (Optional)**

- **3D Model:** Change the `src` attribute in the `<a-gltf-model>` tag to use a different GLTF model.
- **Image Target:** Modify the URL in `mindar-image="imageTargetSrc:"` to point to your custom `.mind` file.
- **Lighting & Animation:** Adjust the properties of the lights and animations to suit your design.

---

## 💻 **HTML Code**

Here's the core HTML code for displaying the AR experience:

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <script src="https://cdn.jsdelivr.net/npm/mind-ar@1.1.5/dist/mindar-image.prod.js"></script>
    <script src="https://aframe.io/releases/1.2.0/aframe.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/mind-ar@1.1.5/dist/mindar-image-aframe.prod.js"></script>
</head>

<body>
    <a-scene
        mindar-image="imageTargetSrc:https://cdn.glitch.global/4ab4383f-20a1-4b44-95f6-f8077367e16e/targets.mind?v=1737139459231;"
        vr-mode-ui="enabled: false" device-orientation-permission-ui="enabled:false">
        <a-camera position="0 0 0" look-controls="enabled: false"></a-camera>

        <!-- Image Target Entity -->
        <a-entity mindar-image-target="targetIndex: 0">
            <!-- 3D Model with Animations -->
            <a-gltf-model
                src="https://cdn.glitch.me/4ab4383f-20a1-4b44-95f6-f8077367e16e/apple_vision_pro.glb?v=1737140621683"
                position="0 0 0" scale="5 5 5" rotation="0 0 0" shadow="cast: true"
                animation="property: rotation; to: 90 360 0; loop: true; dur: 5000; easing: linear"
                animation__scale="property: scale; dir: alternate; dur: 2000; easing: easeInOutQuad; loop: true; to: 5.5 5.5 5.5"></a-gltf-model>

            <!-- Key Light for Strong Illumination -->
            <a-light type="directional" color="#ffffff" intensity="2.0" position="2 4 3" shadow="cast: true"></a-light>

            <!-- Fill Light for Balancing Shadows -->
            <a-light type="directional" color="#e0e0e0" intensity="1.2" position="-2 4 -3"
                shadow="cast: true"></a-light>

            <!-- Back Light for Depth and Contrast -->
            <a-light type="spot" color="#ffffff" intensity="0.7" position="0 6 -5" angle="45"
                shadow="cast: true"></a-light>

            <!-- Ambient Light for Soft Overall Illumination -->
            <a-light type="ambient" color="#d3d3d3" intensity="0.8"></a-light>

            <!-- Glow Effect for Enhanced Atmosphere -->
            <a-entity geometry="primitive: sphere; radius: 0.1"
                material="color: #f0f0f0; emissive: #f0f0f0; emissiveIntensity: 1" position="0 3 0"
                animation="property: position; to: 0 4 0; dur: 1500; dir: alternate; loop: true; easing: easeInOutSine"></a-entity>

        </a-entity>
    </a-scene>
</body>

</html>
```
🔗 Additional Resources
MindAR Documentation: MindAR Documentation – Official guide for using MindAR.
A-Frame Documentation: A-Frame Docs – Official documentation for A-Frame, a web framework for building virtual reality experiences.
