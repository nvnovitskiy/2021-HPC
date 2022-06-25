# Spectrogram

Построение спектрограммы было произведено с помощью двух библиотек Librosa (CPU) & NVIDIA Dali (GPU)

# Spectrogram with NVIDIA Dali:

![nvidia_dali](https://github.com/witssaa/2021-HPC/blob/main/Spectrogram/images/Nvidia_Dali_Spectrogram.png)

# Spectrogram with Librosa:

![lebrosa](https://github.com/witssaa/2021-HPC/blob/main/Spectrogram/images/Librosa_Spectrogram.png)

# Результаты работы двух библиотек:

|    |   Average error |   Time Librosa |   Time Dali |   Speed up |
|---:|----------------:|---------------:|------------:|-----------:|
|  0 |      0.00667399 |       0.210443 |     1.14406 |   0.183944 |

# Ссылка на документацию:

+ https://docs.nvidia.com/deeplearning/dali/user-guide/docs/index.html
