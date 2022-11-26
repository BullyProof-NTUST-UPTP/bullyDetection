###Antes de poder correr este modelo, hay que entrar a la carpeta donde está descargado models.lst y correr los sgtes comandos (asumo que todos ya tenemos openvino, openvino-dev y openvino-dev[tensorflow] instalados como librerías)
### Descargar los modelos compatibles (2 GB aprox)
omz_downloader --list models.lst

### Convertir los modelos a un formato compatible con OpenVINO
### Los modelos pueden tener dependencias extra (midasnet me pedía instalar la librería onnx, por ejemplo)
omz_converter --list models.lst

### Luego usar el sgte comando para correr (Si tienen procesador de Intel)

python monodepth_demo.py -d GPU -i <input_video_path>\<video_name>.mp4 -m <model_path>\midasnet.xml --loop

### En caso de no tener CPU Intel, usen -d CPU en vez de GPU

python monodepth_demo.py -d CPU -i <input_video_path>\<video_name>.mp4 -m <model_path>\midasnet.xml --loop

### Al usar imágenes, el programa se cierra si no le ponemos la opción --loop
