# mmwave_sunmore_c
### Introduction

------------


This repository contains code for sunmoretek mmWave radar **Vitial Signs(Breath rate & Heart rate)** and **Sleeping stage** C Code Version.
Converted from the python code of our project:　[wwave_sunmore](https://github.com/zx50814558/wwave_sunmore.git "wwave_sunmore")

### Prepare

------------


1. Opening port ( Jetson nano )
```
sudo chmod +777 /dev/ttyTHS1
```

2. Git clone respository
```
git clone https://github.com/zx50814558/mmwave_sunmore_c.git
```

### Download models ( Random forest classifier C model )

------------

1. Put the model into the specified path. ( [sleep_feature_min_rf.c](https://drive.google.com/file/d/13cBlKjgBkZv5qSBsSFkn1Ow16-rulids/view?usp=sharing "sleep_feature_min_rf.c") )
```
cd <your repositories path>/sleeping
```

### Running ( Vitial signs )

------------


1. Setting up the path.
```
cd <your repositories path>/vitial_signs
```

2. Compiling C Program.
```
gcc -O3 -o vitial_signs *.c -lm
```

3. Execution commands.
```
Windows: vitial_signs
Linux: ./vitial_signs
```

### Running ( Sleeping stage )

------------


1. Setting up the path.
```
cd <your repositories path>/sleeping
```

2. Compiling RFC Model. (NEED TO INCREASE SWAP SPACE > 13GB, It takes about 2 to 3 days to compile)
```
gcc -Os -c sleep_feature_min_rf.c -lm
ar -rcs sleep_feature_min_rf.a sleep_feature_min_rf.o
```

3. Compiling C Program.
```
gcc -Os -o sleeping *.c sleep_feature_min_rf.a -lm
```

4. Execution commands.
```
Windows: sleeping
Linux: ./sleeping
```
