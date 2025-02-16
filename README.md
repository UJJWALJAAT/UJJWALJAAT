<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sukhi's 3D GitHub Profile</title>
    <!-- CSS Styling -->
    <style>
        body {
            margin: 0;
            overflow: hidden;
            background: #1e1e1e;
            color: white;
            font-family: Arial, sans-serif;
        }
        h1, h3 {
            position: absolute;
            width: 100%;
            text-align: center;
            z-index: 1;
        }
        h1 {
            top: 10%;
            font-size: 3em;
            color: #00ffc3;
        }
        h3 {
            top: 20%;
            color: #ff00c8;
        }
        .profile-section {
            position: relative;
            z-index: 2;
            text-align: center;
            margin-top: 30%;
        }
        .profile-section img {
            border-radius: 50%;
            width: 150px;
            height: 150px;
        }
        .profile-section h2 {
            color: #00ffc3;
        }
        .profile-section p {
            color: #ff00c8;
        }
    </style>
</head>
<body>
    <!-- Profile Heading -->
    <h1>Sukhi</h1>
    <h3>A Passionate Frontend Developer</h3>

    <!-- Profile Section with Image and Details -->
    <div class="profile-section">
        <img src="https://github.com/UJJWALJAAT/UJJWALJAAT/blob/main/1672731712565.png" alt="Sukhi's Logo">
        <h2>Connect with me:</h2>
        <p>Email: example@example.com</p>
        <p>LinkedIn: <a href="https://linkedin.com/in/yourusername" style="color: #00ffc3;">Profile Link</a></p>
    </div>

    <!-- Canvas for 3D Animation -->
    <canvas id="bg"></canvas>

    <!-- Three.js Library -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r134/three.min.js"></script>
    <script>
        // Scene, Camera, Renderer
        const scene = new THREE.Scene();
        const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
        const renderer = new THREE.WebGLRenderer({ canvas: document.querySelector('#bg'), antialias: true });
        renderer.setPixelRatio(window.devicePixelRatio);
        renderer.setSize(window.innerWidth, window.innerHeight);
        camera.position.setZ(30);

        // 3D Cube
        const geometry = new THREE.BoxGeometry(10, 10, 10);
        const material = new THREE.MeshStandardMaterial({ color: 0x00ff83, wireframe: true });
        const cube = new THREE.Mesh(geometry, material);
        scene.add(cube);

        // Lighting
        const pointLight = new THREE.PointLight(0xffffff);
        pointLight.position.set(20, 20, 20);
        scene.add(pointLight);

        // Animation Loop
        function animate() {
            requestAnimationFrame(animate);
            cube.rotation.x += 0.01;
            cube.rotation.y += 0.01;
            renderer.render(scene, camera);
        }
        animate();

        // Responsive Design
        window.addEventListener('resize', () => {
            camera.aspect = window.innerWidth / window.innerHeight;
            camera.updateProjectionMatrix();
            renderer.setSize(window.innerWidth, window.innerHeight);
        });
    </script>
</body>
</html>