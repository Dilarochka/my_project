<!DOCTYPE html>
<html lang="en">
	<head>
		<title>three.js webgl - геометрические фигуры</title>
		<meta charset="utf-8">
		<meta name="viewport" content="width=device-width, user-scalable=no, minimum-scale=1.0, maximum-scale=1.0">
		<link type="text/css" rel="stylesheet" href="https://threejs.org/examples/main.css">
	</head>
	<body>
		<div id="info">
			Стрелка
		</div>

		<script type="module">

			import * as THREE from 'https://threejs.org/build/three.module.js';

			import { OrbitControls } from 'https://threejs.org/examples/jsm/controls/OrbitControls.js';

			var camera, scene, renderer;
			var controls;
			var ambientLight, light;
			init();
			animate();

			function init() {

				var container = document.createElement( 'div' );
				document.body.appendChild( container );

				// CAMERA
				camera = new THREE.PerspectiveCamera( 45, window.innerWidth / window.innerHeight, 1, 80000 );
				camera.position.set( 150, 20, 400 );

				// LIGHTS
				ambientLight = new THREE.AmbientLight( 0x333333 );	// 0.2

				light = new THREE.DirectionalLight( 0xFFFFFF, 1.0 );
				light.position.set( 1, 1, 1 );				
				// direction is set in GUI

				// RENDERER
				renderer = new THREE.WebGLRenderer( { antialias: true } );
				renderer.setPixelRatio( window.devicePixelRatio );
				renderer.setSize( window.innerWidth, window.innerHeight );
				container.appendChild( renderer.domElement );

				// EVENTS
				window.addEventListener( 'resize', onWindowResize, false );

				// CONTROLS
				controls = new OrbitControls( camera, renderer.domElement );
				controls.addEventListener( 'change', render );
				//controls.rotateSpeed = 1; 
				controls.enableZoom = true;  
				controls.zoomSpeed = 0.5;  

				controls.minDistance = 50;
				controls.maxDistance = 2500;
				
				controls.enableDamping = true;

				// scene itself
				scene = new THREE.Scene();
				scene.background = new THREE.Color( 0xD3D3D3 );

				scene.add( ambientLight );
				scene.add( light );
			

				// scene objects
				
				var arrowShape = new THREE.Shape();

					( function roundedRect( ctx ){

					ctx.moveTo( -80, 10 );
					ctx.lineTo( 10, 10 );
					ctx.lineTo( 10, 40 );
					ctx.lineTo( 10, 40 );
					ctx.lineTo( 80, 0 );
					ctx.lineTo( 10, -40 );
					ctx.lineTo( 10, -10 );
					ctx.lineTo( 10, -10 );
					ctx.lineTo( -80, -10 );
					ctx.lineTo( -80, 10 );

					} )( arrowShape );
							

					var size = 9;
					var extrudeSettings = 
						{ 
							depth: size, bevelSegments: 8, curveSegments: 32 
						};

					var geometry = new THREE.ExtrudeGeometry( arrowShape, extrudeSettings );
					var material = new THREE.MeshPhongMaterial({ 
						color: 0xFF0000, specular: 0x708090, shininess: 20 
					});

					var arrow_right = new THREE.Mesh( geometry, material );
					scene.add( arrow_right );


			}

			// EVENT HANDLERS


			function onWindowResize() {

				camera.aspect = window.innerWidth / window.innerHeight;
				camera.updateProjectionMatrix();

				renderer.setSize( window.innerWidth, window.innerHeight );

			}

			//

			function animate() {

				requestAnimationFrame( animate );
				controls.update(); //
				render();

			}

			function render() {

				renderer.render( scene, camera );

			}			


		</script>

	</body>
</html>
