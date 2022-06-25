# Salt and Pepper

# 1. Introduction
One of the most common types of noise in digital photo and video is «Salt and Pepper» noise of random white and black pixels. A number of filters could be used to remove this type of noise: median filters, morphological filters and contra harmonic filters. Median filter for «Salt and Pepper» noise could be naturally parallelized: each pixel could be processed independently.

# 2. Task definition
Given the image of size MxN with «Salt and Pepper» noise, implement and apply a CUDA Version of 9-point median filter and store the result to output image. Missing values for edge rows and columns are to be taken from nearest pixels. CUDA implementation must make use of texture memory.

# 3. Proposed method
The following method could be used to implement the median filter:

* Copy input data to device memory;
* Bind input data to a texture link;
* Extract each pixel together with its surrounding pixels via texture memory into 9-elements array;
* Sort array using any simple method, for instance the «Bubble» method;
* Store the median element into the output array.

# Входные данные:

Фотография, размерность любая, но для тестирования было выбрано три одинаковых фотографии разной размерности (256x256, 512x512, 1024x1024):

![test_image](https://github.com/witssaa/2021-HPC/blob/main/Salt%20and%20Pepper/images/1024.bmp)

# Выходные данные:

Очищенные фотографии очищенные от шумов:

* CPU:

![cpu_output](https://github.com/witssaa/2021-HPC/blob/main/Salt%20and%20Pepper/cpu_result/1024.bmp)

* GPU:

![gpu_output](https://github.com/witssaa/2021-HPC/blob/main/Salt%20and%20Pepper/gpu_result/1024.bmp)

# Реализация:

Каждый элемент выходного изображения на GPU вычислялся отдельной нить(потоком). Чтобы ускорить вычисленя на GPU, внутри каждого блока изображения была выполнена реализация копирования элементов из глобальной памяти в разделяемую, данная манипуляция позволила нам уменьшить число обращений к глобальной памяти. Чтобы получить массив чисел, который характеризует цвет пикселя, была использована библиотека Pillow.

# Время работы функций на CPU/GPU:

|    | Filename   |   CPU Time |   GPU Time |   Speed Up |
|---:|:-----------|-----------:|-----------:|-----------:|
|  0 | 256.bmp    |    5.83029 | 0.00517917 |    1125.72 |
|  1 | 512.bmp    |   24.4522  | 0.01281    |    1908.84 |
|  2 | 1024.bmp   |   98.5632  | 0.0193307  |    5098.78 |

# График времени работы функций на CPU/GPU:

![graphix](https://github.com/witssaa/2021-HPC/blob/main/Salt%20and%20Pepper/images/gpu_cpu.png)

# Speed Up:

![speed_up](https://github.com/witssaa/2021-HPC/blob/main/Salt%20and%20Pepper/images/speed_up.png)

# Вывод: 

В рамках задачи медианной фильтрации лучше использовать GPU, это нам даст большой прирост в плане производительности.
