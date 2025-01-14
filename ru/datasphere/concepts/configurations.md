# Конфигурации вычислительных ресурсов

Сразу после создания проект запускается с минимальной конфигурацией вычислительных ресурсов — <q>c1.4</q> (4 vCPU).
Вы можете [изменить конфигурацию](../operations/projects/control-compute-resources.md) в процессе работы в ноутбуке. При этом состояние интерпретатора сохранится: все переменные и результаты вычислений не потеряются.

Имя | Количество vCPU | Количество GPU
---- | ---- | ----
**Конфигурации с vCPU на<br>[платформе Intel Broadwell](../../compute/concepts/performance-levels.md)**
**c1.4** (по умолчанию) | 4 | 0
**c1.8** | 8 | 0 
**c1.32** (доступна по запросу в техническую поддержку) | 32 | 0
**c1.80** (доступна по запросу в техническую поддержку) | 80 | 0
**Конфигурации с vCPU на [платформе Intel Broadwell](../../compute/concepts/performance-levels.md) и GPU [NVIDIA® Tesla® V100](../../compute/concepts/gpus.md)**
**g1.1** (доступна по запросу в техническую поддержку или при остатке на счете не менее 500 ₽) | 8 | 1
**g1.2** (доступна по запросу в техническую поддержку) | 16 | 2
**g1.4** (доступна по запросу в техническую поддержку) | 32 | 4
**Конфигурации с vCPU на [платформе AMD EPYC™](../../compute/concepts/gpus.md) и GPU [NVIDIA® Ampere® A100](https://www.nvidia.com/ru-ru/data-center/a100/)**
**g2.mig** | 4 | 1/8
**g2.1** (доступна по запросу в техническую поддержку) | 28 | 1
**g2.2** (доступна по запросу в техническую поддержку) | 56 | 2 
**g2.4** (доступна по запросу в техническую поддержку) | 112 | 4 
**g2.8** (доступна по запросу в техническую поддержку) | 224 | 8

#### См. также

* [{#T}](../operations/projects/control-compute-resources.md)
* [{#T}](../../compute/concepts/performance-levels.md)
* [{#T}](../../compute/concepts/gpus.md)