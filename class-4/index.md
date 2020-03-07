# Class 4

Practice using surface methods to model sprial stair with railing and (energy saving) lightbulb.  

- [Slides_Stair](./Spiral_Stair_Railing.pdf)
- [Slides_Lightbulb](./Lightbulb.pdf)

# Topics
```
##Curves
- Helix

##Surfaces
- Pipe

## In-class practice
- Elliptical stair with railing
- Lightbulb

```

# Practice Assignment
Continue to work on modelling the light bulb using the surface creation methods reviewed in class.  Break down the model into three sections - top (the helical bulb elements); middle (cylindrical encasement); bottom (threaded end).  Refer to the tutorial in Slides linked above for reference.

__Example__

<div id="canvas" style="width: 100%; height: 320px;"></div>

<script type="text/javascript" src="/viewer/resources/three.min.js"></script>
<script type="text/javascript" src="/viewer/resources/OrbitControls.js"></script>
<script type="text/javascript" src="/viewer/resources/rhino3dm.js"></script>
<script type="text/javascript">

    var modelURL = '/viewer/models/RhinoI_Bulb.3dm';

    let fetchPromise = fetch(modelURL);

    rhino3dm().then(async m => {
        let rhino = m;

        let res = await fetchPromise;
        let buffer = await res.arrayBuffer();
        let arr = new Uint8Array(buffer);
        let doc = rhino.File3dm.fromByteArray(arr);

        THREE.Object3D.DefaultUp = new THREE.Vector3(0,0,1)
        init();
        let material = new THREE.MeshNormalMaterial();

        let objects = doc.objects();
        for (let i = 0; i < objects.count; i++) {
            let mesh = objects.get(i).geometry();
            if(mesh instanceof rhino.Mesh) {
                // convert all meshes in 3dm model into threejs objects
                let threeMesh = meshToThreejs(mesh, material);
                scene.add(threeMesh);
            }
        }
    });

    var scene, camera, renderer, controls;

    function init(){
        var canvas = document.getElementById("canvas");

        scene = new THREE.Scene();
        scene.background = new THREE.Color(1,1,1);
        camera = new THREE.PerspectiveCamera( 45, canvas.offsetWidth/canvas.offsetHeight, 1, 10000 );
        camera.position.set(900, 450, 900)

        renderer = new THREE.WebGLRenderer({antialias: true});
        renderer.setPixelRatio( window.devicePixelRatio );
        renderer.setSize( canvas.offsetWidth, canvas.offsetHeight );
        
        canvas.appendChild( renderer.domElement );

        controls = new THREE.OrbitControls( camera, renderer.domElement  );

        window.addEventListener( 'resize', onWindowResize, false );
        animate();
    }

    var animate = function () {
        requestAnimationFrame( animate );
        controls.update();
        renderer.render( scene, camera );
    };

    function onWindowResize() {
        camera.aspect = window.innerWidth / window.innerHeight;
        camera.updateProjectionMatrix();
        renderer.setSize( window.innerWidth, window.innerHeight );
        animate();
    }

    function meshToThreejs(mesh, material) {
        let loader = new THREE.BufferGeometryLoader();
        var geometry = loader.parse(mesh.toThreejsJSON());
        return new THREE.Mesh(geometry, material);
    }
</script>
