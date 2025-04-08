---
title: Three.js testing 
published_at: 2025-04-04
snippet: learning how to import 3.js
disable_html_sanitization: true
allow_math: true
--- 
 # Using npm
    npm install three

    # Or using yarn
    yarn add three

<script src="https://threejs.org/build/three.min.js">

const scene = new THREE.Scene();
    const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
    const renderer = new THREE.WebGLRenderer();
    renderer.setSize(window.innerWidth, window.innerHeight);
    document.body.appendChild(renderer.domElement); 

<div id="three.js_container"></div>

<script type="importmap">
			{
				"imports": {
					"three": "../build/three.module.js",
					"three/addons/": "./jsm/"
				}
			}
		</script>

<script type="module">
    import * as THREE from "../3jdasset/three.module.js"

    console.log (THREE)

    const container = document.getElementByID ('three.js_container')
    const width = container.parentNode.scrollWidth
    const height = width * 9/16

    </script>