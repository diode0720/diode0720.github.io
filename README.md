<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Custom Printing</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
    <style>
        body {
            margin: 0;
            overflow: hidden;
            font-family: Arial, sans-serif;
            text-align: center;
            background: linear-gradient(to right, #ff8a00, #e52e71);
            color: white;
        }
        .header {
            position: absolute;
            top: 20px;
            left: 50%;
            transform: translateX(-50%);
            font-size: 24px;
            font-weight: bold;
        }
        .gallery {
            position: absolute;
            top: 60px;
            left: 50%;
            transform: translateX(-50%);
            display: flex;
            gap: 10px;
            flex-wrap: wrap;
            width: 80%;
        }
        .gallery img {
            width: 150px;
            height: 150px;
            border-radius: 10px;
            cursor: pointer;
            transition: 0.3s;
        }
        .gallery img:hover {
            transform: scale(1.1);
        }
        .buy-button {
            position: absolute;
            bottom: 50px;
            left: 50%;
            transform: translateX(-50%);
            padding: 15px 30px;
            font-size: 18px;
            color: white;
            background: #ff4e50;
            border: none;
            border-radius: 10px;
            cursor: pointer;
            transition: 0.3s;
        }
        .buy-button:hover {
            background: #ff6f61;
        }
    </style>
</head>
<body>
    <div class="header">Customize & Print</div>
    
    <div class="gallery">
        <a href="product1.html"><img src="product1.jpg" alt="Product 1"></a>
        <a href="product2.html"><img src="product2.jpg" alt="Product 2"></a>
        <a href="product3.html"><img src="product3.jpg" alt="Product 3"></a>
    </div>
    
    <button class="buy-button" onclick="window.location.href='YOUR_PAYPAL_LINK_HERE'">Buy Now</button>
    
    <script>
        // Create 3D scene
        const scene = new THREE.Scene();
        const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
        const renderer = new THREE.WebGLRenderer();
        renderer.setSize(window.innerWidth, window.innerHeight);
        document.body.appendChild(renderer.domElement);
        
        // Create a rotating 3D cube
        const geometry = new THREE.BoxGeometry();
        const material = new THREE.MeshBasicMaterial({ color: 0xffffff, wireframe: true });
        const cube = new THREE.Mesh(geometry, material);
        scene.add(cube);
        
        camera.position.z = 5;
        
        function animate() {
            requestAnimationFrame(animate);
            cube.rotation.x += 0.01;
            cube.rotation.y += 0.01;
            renderer.render(scene, camera);
        }
        animate();
        
        // Resize handler
        window.addEventListener('resize', () => {
            renderer.setSize(window.innerWidth, window.innerHeight);
            camera.aspect = window.innerWidth / window.innerHeight;
            camera.updateProjectionMatrix();
        });
    </script>
</body>
</html>
