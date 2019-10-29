t# singularity_image_classifier

Running Singularity on Stampede2

- Start an interactive development session
  > idev
- Once you are on a compute node, load the tacc-singularity module
  > module load tacc-singularity
  > module list (would now show tacc-singularity if it is loaded properly)
  You now have access to singularity commands on Stampede2
  
- Git clone the https://github.com/shwetagopaul92/docker_image_classifier
  > cd docker_image_classifier
  > singularity pull docker://reshg/image_classifier
  This would create a .simg file which can be used to execute the image. 
  
  > singularity exec /work/06935/sgopal/singularity_cache/image_classifier.simg classify_image.py --image_file dog.jpg
  
  > singularity run -B $PWD:/data docker://reshg/image_classifier classify_image.py --model_dir /model --image_file /data/dog.jpg
  
  The way Singularity mounts the volume is different. 
  
  Result: 
  Successfully downloaded inception-2015-12-05.tgz 88931400 bytes.
  2019-10-29 20:55:31.858613: I tensorflow/core/platform/cpu_feature_guard.cc:137] Your CPU supports instructions that this     TensorFlow binary was not compiled to use: SSE4.1 SSE4.2 AVX AVX2 AVX512F FMA
  2019-10-29 20:55:33.162185: W tensorflow/core/framework/op_def_util.cc:343] Op BatchNormWithGlobalNormalization is          
  deprecated. It will cease to work in GraphDef version 9. Use tf.nn.batch_normalization().
  golden retriever (score = 0.90329)
  Labrador retriever (score = 0.00466)
  kuvasz (score = 0.00458)
  Saluki, gazelle hound (score = 0.00371)
  English setter (score = 0.00307)
  
  
  
  
  Some useful singularity commands for running docker images:
  
  > singularity shell docker://ubuntu:latest
  > singularity run docker://ubuntu:latest
  > singularity exec docker://ubuntu:latest echo "Hello Dinosaur!"
  > singularity pull docker://ubuntu:latest
  > singularity build ubuntu.img docker://ubuntu:latest
