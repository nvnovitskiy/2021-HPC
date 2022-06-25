# Bilateral Filter (Белинейный фильтр сглаживания изображения с сохранением четких границ)

Реализация белинейного фильтра проводилась в Google Colaboratory

# The following coulee be used to implement the bilateral filter

1. Copy input data to device memory
2. Bind input data to a texture link
3. Extract each pixel together with its surrounding pixels via texture memory into 9-elements array
4. Calculate the result pixel intensity using the formulas above
5. Store the result into the array

# Изображение для тестирования фильтра:

![test_img](https://github.com/nvnovitskiy/high-performance-computing/blob/main/Bilateral%20Filtering/test_img.png)

# Результат обработки изображения фильтром на CPU:

![cpu_image](https://github.com/nvnovitskiy/high-performance-computing/blob/main/Bilateral%20Filtering/result_cpu.bmp)

# Результат обработки изображения филтром на GPU:

![cpu_image](https://github.com/nvnovitskiy/high-performance-computing/blob/main/Bilateral%20Filtering/result_gpu.bmp)

# Затраченное время на обработку:
|    |   Время на GPU |   Время на CPU |   CPU/GPU |
|---:|---------------:|---------------:|----------:|
|  0 |      0.0131254 |        81.8392 |   6235.17 |

Результат обработки изображения идентичен, но стоит отметить, что функция на GPU справляется с своей задачей в разы быстрее нежели на CPU.
