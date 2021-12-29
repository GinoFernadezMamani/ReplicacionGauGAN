# ReplicacionGauGAN

<h2>Re: Semantic Image Synthesis with SPADE </h2>

Se propone la replicación del articulo  de Taesung Park et al. (2019)  que realiza la normalización espacialmente adaptativa, para sintetizar imágenes fotorrealistas dada una imagen semántica de entrada.

El archivo ProyectoGauGAN ejecuta un modelo pre-entrenado(COCO-Stuff) y entrenado personalizado (CamVid), por último se realiza la evaluación FIP.

<h3> Instalación </h3>

`git clone https://github.com/GinoFernadezMamani/ReplicacionGauGAN`
`cd SPADE/`


 <h3> norma de lotes sincronizados </h3>
 
`!git clone https://github.com/vacancy/Synchronized-BatchNorm-PyTorch`
`!cp -rf Synchronized-BatchNorm-PyTorch/sync_batchnorm`

<h3>Test en un modelo Pre-entrenado</h3>

Descargamos el checkpoint para el modelo pre-entrenado, y en seguida creamos una carpeta donde los almacenaremos y descomprimiremos.
`!gdown https://drive.google.com/uc?id=12gvlTbMvUcJewQlSEaZdeb2CdOB-b8kQ`


<h3> Preparación del Dataset </h3>


CamVid (Cambridge‐driving Labeled Video Database) es una base de datos de compren‐sión de la escena de la conducción en carretera que fue capturada originalmente comocinco secuencias de vídeo con una cámara de resolución 960×720 montada en el salpi‐cadero de un coche. Esas secuencias se muestrearon (cuatro de ellas a 1 fps y una a15 fps) sumando 701 fotogramas mostrado en la Figura4. Esas imágenes fijas se ano‐taron manualmente con 32 clases: vacío, edificio, pared, árbol, vegetación, valla, acera,bloque de aparcamiento, columna/poste, cono de tráfico, puente, señal, texto diverso,semáforo, cielo, túnel, arco, carretera, arcén, marcas de carril (conducción), marcasde carril (no conducción), animal, peatón, niño, carro de equipaje, ciclista, motocicleta,coche, todoterreno/camión/camión, camión/autobús, tren y otro objeto en movimiento

`!wget -c http://web4.cs.ucl.ac.uk/staff/g.brostow/MotionSegRecData/files/701_StillsRaw_full.zip`


Descargamos los mapas de segmentación semántica del dataset CamVid

`!wget -c http://web4.cs.ucl.ac.uk/staff/g.brostow/MotionSegRecData/data/LabeledApproved_full.zip`

Calculamos ahora la puntuación FID para nuestras predicciones. Antes de que podamos hacer eso, debemos cambiar el tamaño de nuestros datos al mismo tamaño que nuestras imágenes generadas.

`!git clone https://github.com/mseitzer/pytorch-fid`

