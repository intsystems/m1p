# Список задач по курсу Моя первая научная статья, весна 2026

<!-- Святослав перенес на 2027 
## Задача 159 (Вадим Викторович: спросить Святослава)
* **Название:** Восстановление функциональных групп головного мозга с помощью графовых диффузных моделей
* **Описание проблемы:** Решается задача построения модели анализа активности головного мозга, учитывающей пространственную структуру сигнала. Данные об активности мозга представлены в виде многомерных временных рядов, считываемых
электродами, расположенными на голове испытуемого одним из универсальных стандартов размещения. Из-за отсутствия регулярного определения окрестности на сферической поверхности мозга классические сверточные нейронные
сети не могут быть эффективно применены для учета пространственной информации. Предлагается использовать графовое представление сигнала, что позволит выявить более сложные взаимосвязи различных областей активности в пространстве и провести нейробиологическую интерпретацию функциональных связей мозга. 
* **Данные:** Юлия Березуцкая, код загрузки у четвертого курса
	- Berezutskaya J., et al Open multimodal iEEG-fMRI dataset from naturalistic stimulation with a short audiovisual film // Sci Data 9, 91, 2022.
* **Литература** Магистерская работа Наталии Вареник
* **Базовый алгоритм:** Graph Neural Diffusion: https://github.com/twitter-research/graph-neural-pde
* **Новизна:** Построить карту функциональных групп с изменением во времени в зависимости от внешнего воздействия (видео Пеппи)
* **Авторы:** Святослав Панченко, Стрижов
-->

## Задача 177.1 --- 177.3
* __Название__: Кодирование генеративных моделей
* __Направление задач__: Исследуются методы представления (энкодинга) обученных генеративных нейросетей в виде компактных векторных описаний, отражающих статистические свойства данных обучения. Цель проекта — проверить и развить гипотезы о связи параметров моделей, их выходных распределений и датасетов обучения, доведя их до воспроизводимых методов сравнения и анализа генеративных моделей.  
* __Постановка 1:__ Параметры обученной генеративной модели содержат информацию о статистике обучающих данных. Предполагается, что различия в весах моделей коррелируют с различиями между датасетами.  
Необходимо разработать метод, который по параметрам (или их преобразованиям, например спектральным характеристикам) обученной генеративной модели:
	- предсказывает тип или состав датасета обучения;
  	- оценивает различие между датасетами через расстояние между соответствующими представлениями моделей.  
  **Note:** Стоит опираться на спектральные или иные устойчивые характеристики весов и проверить метод на моделях, обученных на подвыборках стандартных датасетов. Кроме того можно изучить возможность использовать графовые сети и кодирование слоев для этой задачи.  
* __Постановка 2:__ ГВыходы генеративных моделей можно рассматривать как представление самих моделей и косвенно — данных обучения. Требуется построить метрику близости между моделями на основе различий в распределениях их сгенерированных данных.
Необходимо разработать метод получения эмбеддингов моделей, который:
	- использует статистики сгенерированных данных (или их признаковые представления);
	- обучает метрику близости между моделями без жёстко заданной функции расстояния;
	- позволяет выявлять сходство датасетов через сходство генеративных моделей.  
	**Note:** В качестве базового подхода предлагается обучать многобашенную сеть, сопоставляющую реальные и сгенерированные выборки разных групп и формирующую эмбеддинги с мета-признаками датасетов.
* __Постановка 3:__ Эмбеддинги генеративных моделей могут обладать заданной геометрической структурой, отражающей смешение базовых датасетов. Предлагается исследовать обучение эмбеддингов, в которых представление модели, обученной на смеси данных, выражается через комбинацию представлений базисных моделей. Цель — проверить, можно ли восстанавливать структуру смесей датасетов и управлять геометрией пространства моделей. Необходимо:
	- выделить базисные подвыборки (например, через кластеризацию в латентном пространстве);
 	- обучить модели на базисах и их смесях;
  	- построить эмбеддер моделей, учитывающий как метрику близости, так и геометрические ограничения (например, линейные комбинации эмбеддингов базисов).  
	**Note:** Дополнительно можно исследовать возможность комбинации базисных моделей для получения распределения, порожденного моделью, обученной на смесе данных.
* __Данные__: CIFAR, MNIST, Fashion-MNIST, etc
* __Литература__:
  	- [[1]](https://www.ubs.mtas.ru/bitrix/components/bitrix/forum.interface/show_file.php?fid=48274)
	- [[2]](https://arxiv.org/pdf/2406.09997)
	- [[3]](https://arxiv.org/pdf/1703.03400)
	- [[4]](https://arxiv.org/pdf/2403.02484)
* __Базовый алгоритм__:
  	- [https://github.com/HSG-AIML/SANE](https://github.com/HSG-AIML/SANE) -- интересный метод кодирования сеток, подходящий как для генеративных, так и дискриминативных моделей.
  	- [https://github.com/intsystems/Vector-space-of-generative-models/tree/master/code] -- базовый подход для постановки 1.
* __Авторы__:
	- Консультант: Никитина Мария
	- Эксперт: Бишук Антон

## Problem 185
* **Title** 
Operator learning in PINN
* **Problem**
Many machine learning tasks require working with operators over multidimensional vectors. For example, when working on images, the task is to find an operator that transforms the discretized image into another vector: in the case of a classification task, a probabilistic vector, and in the case of generation, it will also be the image space. If the dimensionality of the space is large, it makes sense to represent the image as a function on the coordinates, yielding a color from the RGB space. A similar problem exists for physical systems. Unlike images, they operate in three-dimensional space. And it is impossible to discretize the space for them. In a general way, this problem is solved by Operator Learning. In this problem, it is proposed to learn an operator on a continuous space. It is proposed to extend this idea to physical systems. The ultimate goal is to provide an efficient solution that compresses the space in which the operator operates, analogous to PCA for matrices.
* **Data**
    - [1]  MacCallum S, Merchant C (2011) Arc-lake v1.1-per-lake, 1995–2009 [https://doi.org/10.7488/ds/159](https://doi.org/10.7488/ds/159)
    - [2] Reiss, A. (2012). PAMAP2 Physical Activity Monitoring [Dataset]. UCI Machine Learning Repository. [https://doi.org/10.24432/C5NW2H](https://doi.org/10.24432/C5NW2H)
    - [3] Bousseljot R, Kreiseler D, Schnabel, A. Nutzung der EKG-Signaldatenbank CARDIODAT der PTB über das Internet. Biomedizinische Technik, Band 40, Ergänzungsband 1 (1995) S 317[https://doi.org/10.13026/C28C71](https://doi.org/10.13026/C28C71)
* **Reference**
    - [1] Kovachki, Nikola B., Samuel Lanthaler, and Andrew M. Stuart. "Operator learning: Algorithms and analysis." arXiv preprint arXiv:2402.15715 (2024). [https://doi.org/10.48550/arXiv.2402.15715](https://doi.org/10.48550/arXiv.2402.15715)
    - [2] Palummo, A., Arnone, E., Formaggia, L. et al. Functional principal component analysis for incomplete space–time data. Environ Ecol Stat 31, 555–582 (2024). [https://doi.org/10.1007/s10651-024-00598-7](https://doi.org/10.1007/s10651-024-00598-7)
    - [3] Gruber, Anthony, and Irina Tezaur. "Canonical and noncanonical Hamiltonian operator inference." Computer Methods in Applied Mechanics and Engineering 416 (2023): 116334. [https://doi.org/10.1016/j.cma.2023.116334](https://doi.org/10.1016/j.cma.2023.116334)
    - [4] Olivieri, M., Karakonstantis, X., Pezzoli, M. et al. Physics-informed neural network for volumetric sound field reconstruction of speech signals. J AUDIO SPEECH MUSIC PROC. 2024, 42 (2024). [https://doi.org/10.1186/s13636-024-00366-2](https://doi.org/10.1186/s13636-024-00366-2)
* **Baseline**
Apply The Fourier operator or other similar ohttps://t.me/@leg_bahperator and use this transformation to predict the time series.
* **Proposed solution**
Using an operator learning framework, propose a solution for different types of operators used in physics, image analysis, etc. Propose an idea to implement ICA to reduce the dimensionality of an operator to compute it in an efficient way.
* **Novelity**
There are no soluton to learning the operators used in physics.
* **Authors** 
    - Expert: Стрижов
    - Consultant: Alexander Terentyev

## Задача 199
* __Название__: Анализ причинно-следственных связей между биомедицинскими сигналами (ЭЭГ-ЭКГ, ЭЭГ-МЭГ) через скрытые представления автоэнкодеров
* __Задача__: Исследование кросс-модальных причинно-следственных связей в нейрофизиологических данных. Основная гипотеза: связь между сердцем и мозгом (ЭЭГ ↔ ЭКГ) или между разными методами регистрации мозговой активности (ЭЭГ $\longleftrightarrow$ МЭГ) может быть выявлена через анализ динамики в скрытом пространстве. Предлагается архитектура из двух параллельных автоэнкодеров (по одному на модальность), после чего в латентном пространстве применяются методы оценки каузальности: Convergent Cross Mapping (CCM), transfer entropy или дифференциальные уравнения (Neural ODE/CDE). Цель — количественно оценить направленность влияния (мозг $\longrightarrow$ сердце vs сердце $\longrightarrow$ мозг).
* __Предыдущие результаты__:
	* Построен [метод апроксимации показаний fMRI по прослушиваемому звуковому ряду](https://github.com/intsystems/2024-Project-117/tree/master).
	* Построен [метод апроксимации показаний fMRI по видео ряду](https://github.com/DorinDaniil/Forecasting-fMRI-Images).
* __Данные__:
  * Мультимодальные записи во время прослушивания музыки: ЭЭГ, ЭМГ, ЭКГ — [OpenNeuro ds004840](https://openneuro.org/datasets/ds004840/versions/1.0.1)
  * Мультимодальные записи [Nature Scientific Data 2025](https://www.nature.com/articles/s41597-025-05580-x), [Pattern Recognition Letters 2017](https://www.sciencedirect.com/science/article/abs/pii/S0167865517304634), [Nature Scientific Data 2021](https://www.nature.com/articles/s41597-021-01046-y), [Human Brain Mapping 2023](https://onlinelibrary.wiley.com/doi/full/10.1002/hbm.26480)
* __Авторы__:
  * Даниил Дорин (tg: [@danulkin](https://t.me/danulkin))
  * Грабовой Андрей

## Задача 200
* __Название__: Transfer learning for surrogate-based neural ensemble search

* __Задача__:  
Рассматривается задача поиска структур нейросетей для ансамблей (Neural ensemble search). В работе будет рассматриваться метод на основе суррогатных моделей-предикторов, которые по входным архитектурам предсказывают качество моделей и их разнообразие. Предлагается исследовать способность ли суррогатных функций, обученных подбирать высококачественные и разнообразные ансамбли архитектур на простом датасете, эффективно решать ту же задачу на более сложном датасете без дополнительного обучения. Анализ фокусируется на том, сохраняется ли структура и разнообразие отобранных ансамблей при переносе, и как эти свойства влияют на итоговое качество обобщения на новом, сложном датасете.

* __Данные__:  
Качество переноса планируется оценивать при переходе с датасета [CIFAR-10](https://www.cs.toronto.edu/~kriz/cifar.html) к более сложному датасету [CIFAR-100](https://www.cs.toronto.edu/~kriz/cifar.html).  

Для обучения суррогатной функции предполагается использовать набор предварительно обученных моделей на [CIFAR-10](https://disk.yandex.ru/d/1omda1mICnluAQ). Эти модели будут использованы для построения ансамблей и обучения суррогатной функции предсказывать качество и структуру ансамблей.

* __Литература__: 
  * [Transferrable Surrogates in Expressive Neural Architecture Search Spaces](https://arxiv.org/pdf/2504.12971) -- В статье показывается, что перенос суррогатной функции для поиска оптимальной архитектуры сети позволяет определять оптимальную архитектуру для более сложного датасета
  * [Similarity surrogate-assisted evolutionary neural architecture search with dual encoding strategy](https://www.aimspress.com/aimspress-data/era/2024/2/PDF/era-32-02-050.pdf) -- В статье представлен алгоритм, по отбору хороших архитектур посредством суррогатной функции
  * [Neural Ensemble Search for Uncertainty Estimation and Dataset Shift](https://proceedings.neurips.cc/paper_files/paper/2021/hash/41a6fd31aa2e75c3c6d427db3d17ea80-Abstract.htm) -- Представлены два метода построения ансамбля нейронных моделей в случае сдвига в данных, также есть подробный обзор статей посвященных NES

* __Базовой алгоритм__: В качестве базовых алгоритмов возьмем [DeepEns](https://proceedings.neurips.cc/paper_files/paper/2017/hash/9ef2ed4b7fd2c810847ffa5fa85bce38-Abstract.html) и RandomSearch.

* __Решение__: Обучить суррогатную функцию на датасете моделей, обученных на простом датасете. После этого, использовать ее для формирования ансамбля моделей для более сложного датасета. Далее нужно обучить составленный ансамбль. В качестве метрик нам в первую очередь интересна корреляция между долей совпадающих ответов и расстояний между эмбедденгами для моделей действующих на сложном датасете. Также, планируется замерить точность полученного ансамбля и метрики разнообразия (Normalized Disagreement, Ambiguity, Brier score).

* __Новизна__: Данное исследование является естественным продолжением исследования возможностей суррогатных функций при переносе на другой датасет, начатый авторами первой статьи в пункте "Литература". Сам метод обучения ансамблей на основе суррогатных моделей находится на рецензировании, очень ранняя черновая версия работы находится [здесь](https://github.com/intsystems/predicator-function-for-neural-networks/blob/master/paper/Udeneev2025Surrogate.pdf)

* __Авторы__:
  * Александр Уденеев (tg: [@demoren361](https://t.me/demoren361))
  * Олег Бахтеев (tg: [@leg_bah](https://t.me/leg_bah))

## Problem 205
* __Title__: Inductive Bias Meta-Learning with Generative Models
* __Problem__: This project studies inductive bias in machine learning models. By inductive bias we mean the preference of a model for certain types of functions or data structures over others (for example, convolutional neural networks are typically more suitable for vision tasks, while recurrent architectures are often more appropriate for sequential data). We consider the following inverse problem: given a fixed target model, can we construct data that this model can fit and generalize on particularly well? Previous work demonstrated that generating data labels for a fixed set of inputs allows one to reveal model properties. In this project, we extend this idea and aim to generate full synthetic datasets that are especially well-suited for the analyzed model.
* __Data__: Synthetic datasets generated by a trainable generative model.
* __Reference__: 
    * [Baseline paper: generating labels to infer inductive bias](https://arxiv.org/pdf/2211.13544)
    * [Classical paper on inductive bias and multi-task learning](https://link.springer.com/article/10.1023/A:1007379606734)
    * [Early foundational paper on inductive bias](https://link.springer.com/article/10.1007/BF00993474)
* __Baseline__: The method from [this paper](https://arxiv.org/pdf/2211.13544): generate labels for a fixed dataset so that the target model achieves strong generalization, and analyze the induced model preferences.
* __Proposed solution__: An extension of the baseline approach: instead of generating labels for a fixed dataset, we train a generative model (e.g., a decoder from a variational autoencoder) to produce entire synthetic datasets on which the target model achieves strong generalization performance.
* __Novelty__: The project investigates fundamental properties of machine learning models and proposes a generative meta-learning framework for studying and characterizing inductive bias.
* __Authors__: Oleg Bakhteev (tg: [@leg_bah](https://t.me/leg_bah))

## Problem 206
* __Title__: Оценка сложности инструментов ИИ-агентов
* __Problem__: Современные системы построения ИИ-агентов подразумевают использования LLM моделей как оператора различными инструментами, для решения поставленной задачи. Причем, агентная система обычно состоит не из одной модели, а нескольких, причем их сложности (число параметров) обычно различаются. Для выбора оптимальной LLM модели к заданому инструменту обычно используется RLHF подход, который настраивается под конкретные инструменты и задачу в процессе обучения. В рамках данного исследования предлагается на этапе предобучения построить оценку сложности инструментов. В качестве базового решения оценки сложности инструмента предлагается использовать собственную размерность текста описания инструмента, которая и задаст сложность инструмента. В качестве резульатат предлагается сравнить как меняется скорость сходимости RLHF метода без задания априорной информации о сложности инструментов и с заданием априорной информации на основе полученных оценок сложности.
*  __Authors__: Андрей Грабовой

## Problem 207
* __Title__: Инвариантный индекс текста на основе собственной размерности при машинном переводе
* __Problem__: Современные большие языковые модели используют внутрение представление текста для работы с ним. Тексты различной сложности имеют различное скрытое представление относительно заданой большой языковой модели. Современные работы показывают, что собственная размерность текста является инвариантом относительно перефразирования текста, так как не меняет его внутреней сложности. В рамках данной работы предлагается проверить гипотезу инвариантности перевода и перефразирования текста, а также гипотезу о возможности использования последовательности таких инвариант для больших документов с возможностью построения поискового индекса схожих кандидатов. Для проведения экспериментов предлагается использовать статьи разных языков wikipedia, где статьи одной темы можно считать как перевод (в очень грубом приближении).
* __Authors__: Андрей Грабовой
  
## Задача 208
* __Название__: Исследование эффективности метода Generative Drifting для задачи одношагового сверхвысокого разрешения (Super-Resolution)
* __Задача__: Цель работы — исследовать применимость подхода Drifting (дрейфа распределений) для восстановления деталей на изображениях низкого разрешения. Проблема заключается в том, что современные диффузионные модели, обеспечивая высокое качество, слишком медленны для реального времени, а быстрые MSE-методы дают размытый результат. В работе предлагается адаптировать механизм Drifting для условной генерации. Основная гипотеза: модель способна выучить прямой линейный транспорт от распределения размытых изображений к четким за один шаг инференса. Планируется сравнить качество (метрики PSNR, SSIM, LPIPS) и скорость работы с классическими GAN и дистиллированными диффузионными моделями, чтобы оценить потенциал Drifting как нового стандарта для быстрого апскейлинга.
* __Авторы__: Андрей Филатов (tg: [@anvilarth](https://t.me/anvilarth))

## Задача 209
- **Название**: Адаптивный выбор параметров распределения сэмплирования для Monte Carlo оценки сходимости оптимизационной поверхности
- **Задача**: Распределенный подход к оценке сходимости поверхности функции потерь использует Monte Carlo сэмплирование из гауссовского распределения в окрестности локального минимума. Существующие результаты показывают сильную зависимость оценки от параметра дисперсии $\sigma$ распределения сэмплирования, однако оптимальный выбор этого параметра остается открытым вопросом. В работе предлагается разработать адаптивные методы выбора параметров распределения сэмплирования на основе свойств Гессиана функции потерь и провести сравнительный анализ различных стратегий выбора.
- **Литература**:
  - [1] [Robust Convergence of Loss Landscapes through Distributional Averaging](https://github.com/kisnikser/robust-loss-landscape-convergence): базовая работа с распределенным подходом к оценке сходимости оптимизационной поверхности
  - [2] [Unraveling the Hessian: A Key to Smooth Convergence in Loss Function Landscapes](https://github.com/intsystems/landscape-hessian/tree/validation): точечный анализ Гессиана для оценки сходимости поверхности функции потерь
- **Данные**: Предлагается проводить вычислительный эксперимент на задаче классификации изображений, используя наборы данных
  - [MNIST](https://pytorch.org/vision/0.20/generated/torchvision.datasets.MNIST.html#torchvision.datasets.MNIST)
  - [FashionMNIST](https://pytorch.org/vision/0.20/generated/torchvision.datasets.FashionMNIST.html#torchvision.datasets.FashionMNIST)
  - [CIFAR10](https://pytorch.org/vision/0.20/generated/torchvision.datasets.CIFAR10.html#torchvision.datasets.CIFAR10)
- **Базовый алгоритм**: Использовать существующий подход из [1] с фиксированным $\sigma$, затем разработать методы адаптивного выбора на основе спектральных свойств Гессиана.
- **Решение**:
  - Проанализировать зависимость оценки сходимости от параметра $\sigma$ для различных архитектур
  - Предложить методы выбора $\sigma$ на основе собственных значений Гессиана (например, обратно пропорционально наибольшему собственному значению)
  - Рассмотреть адаптацию $\sigma$ в зависимости от размера выборки
  - Сравнить различные стратегии выбора параметров и их влияние на стабильность оценок
- **Новизна**: Ранее не исследовались адаптивные методы выбора параметров распределения сэмплирования. Развитие исследований в этом направлении позволит сделать распределенный подход более практичным и устойчивым.
- **Авторы**:
  - Консультант: Никита Киселев (tg: [@kisnikser](https://t.me/kisnikser))
  - Эксперт: Андрей Грабовой

## Задача 210
- **Название**: Улучшение оценки нормы разности Гессианов при увеличении размера выборки
- **Задача**: В существующих работах оценка сходимости поверхности функции потерь сводится к оценке нормы разности Гессианов $\mathbf{H}_{k+1}(\mathbf{w}^*) - \frac{1}{k}\sum_{i=1}^k \mathbf{H}_i(\mathbf{w}^*)$ (разность гессиана по $(k+1)$-му объекту и среднего по первым $k$). Сейчас эту норму оценивают по неравенству треугольника: $\big\| \mathbf{H}_{k+1} - \frac{1}{k}\sum_{i=1}^k \mathbf{H}_i \big\|_2 \leqslant \| \mathbf{H}_{k+1} \|_2 + \big\| \frac{1}{k}\sum_{i=1}^k \mathbf{H}_i \big\|_2 \leqslant 2 M_{\mathbf{H}}$, то есть константой, не зависящей от $k$. Такая оценка не отражает того, что разность «одного» Гессиана и среднего по $k$ объектам при росте $k$ должна убывать. В работе предлагается получить более точную теоретическую оценку нормы (спектральной или Фробениуса) этой разности, использующую структуру разности и дающую убывание по $k$ (например, порядок $O(1/k)$ или $O(1/\sqrt{k})$ при подходящих предположениях), с последующей практической валидацией на задачах классификации изображений.
- **Литература**:
  - [1] [Unraveling the Hessian: A Key to Smooth Convergence in Loss Function Landscapes](https://github.com/intsystems/landscape-hessian/tree/validation): постановка, второе приближение и оценка через $\| \mathbf{H}_{k+1} - \frac{1}{k}\sum \mathbf{H}_i \|_2 \leqslant 2 M_{\mathbf{H}}$
  - [2] [Robust Convergence of Loss Landscapes through Distributional Averaging](https://github.com/kisnikser/robust-loss-landscape-convergence): оценка $\| \mathbf{A}_k \|_2$ через неравенство треугольника и следы
  - [3] Работы по спектру Гессиана в нейросетях (Ghorbani, Sagun и др.): структура пер-объектных Гессианов
- **Данные**: Предлагается проводить вычислительный эксперимент на задаче классификации изображений, используя наборы данных
  - [MNIST](https://pytorch.org/vision/0.20/generated/torchvision.datasets.MNIST.html#torchvision.datasets.MNIST)
  - [FashionMNIST](https://pytorch.org/vision/0.20/generated/torchvision.datasets.FashionMNIST.html#torchvision.datasets.FashionMNIST)
  - [CIFAR10](https://pytorch.org/vision/0.20/generated/torchvision.datasets.CIFAR10.html#torchvision.datasets.CIFAR10)
- **Базовый алгоритм**: Опираться на явную запись $\mathbf{H}^{(k)} = \frac{1}{k}\sum_{i=1}^k \mathbf{H}_i$ и разность $\mathbf{H}_{k+1} - \mathbf{H}^{(k)}$; не ограничиваться оценкой по треугольнику, а использовать разложение разности (например, через $\frac{1}{k}\sum_{i=1}^k (\mathbf{H}_{k+1} - \mathbf{H}_i)$), ограниченность или концентрацию пер-объектных Гессианов, либо свойства спектра.
- **Решение**:
  - Записать разность $\mathbf{H}_{k+1} - \frac{1}{k}\sum_{i=1}^k \mathbf{H}_i$ в форме, удобной для оценки (например, через разность с «популяционным» средним или через суммы разностей пар)
  - Ввести подходящие предположения (ограниченность $\| \mathbf{H}_i \|$, ограниченность разностей $\| \mathbf{H}_i - \mathbf{H}_j \|$, моменты, концентрация и т.п.) и получить верхнюю оценку нормы разности вида $O(1/k)$ или $O(1/\sqrt{k})$ (по возможности с явными константами)
  - Сравнить новую оценку с существующей $2 M_{\mathbf{H}}$ и с поведением в эксперименте (оценка нормы разности Гессианов и метрики сходимости поверхности при разных $k$)
- **Новизна**: Сейчас в оценках сходимости оптимизационной поверхности норму разности Гессианов по сути заменяют на сумму норм и теряют убывание по $k$. Получение оценки, отражающей убывание разности при росте выборки, улучшит теоретическое обоснование скорости сходимости и даст более показательные константы в существующих результатах.
- **Авторы**:
  - Консультант: Никита Киселев (tg: [@kisnikser](https://t.me/kisnikser))
  - Эксперт: Андрей Грабовой
 
## Задача 211
- **Название**: Data Complexity via Data Geometry Using Generative Models
- **Задача**: Data complexity is a broad concept used to describe how complicated a dataset is. Many existing approaches to data complexity assume that all data points have the same complexity and that overall complexity grows linearly with dataset size. However, both assumptions are questionable. First, different datasets clearly have different inherent complexity: for example, image from CIFAR is more complex than handwritten digits from MNIST. Second, duplicating the same data points does not meaningfully increase complexity, even though the dataset size increases. We hypothesize that real-world data has an upper bound on intrinsic complexity. Modern generative models, such as diffusion models trained on large image datasets, may already be operating near this limit. If this hypothesis is correct, then data complexity does not scale linearly with dataset size, and current complexity estimation methods are inadequate. The challenge is to develop a method of complexity such that it adequately captures the notion of complexity. In terms of measure-theoretic this measure should be sub-additive.
- **Литература**:
  - [https://arxiv.org/abs/2406.03537](https://arxiv.org/abs/2406.03537)
  - [https://arxiv.org/abs/2212.12611](https://arxiv.org/abs/2212.12611)
- **Базовый алгоритм**: Generative models such as diffusion models learn to approximate the underlying data distribution. By analyzing the geometry of this distribution, we can assess the complexity of individual data points using notions such as intrinsic dimensionality (the dimension of the manifold on which the data lies) and curvature
- **Новизна**: Existing methods make no assumptions about the complexity and the scalability factor of datum.
- **Авторы**:
  - Консультант: Данила Черноусов (tg: @Danilacher)
  - Эксперт: Андрей Грабовой
 

# Проекты от пятикурсников
## Problem 201
* **Title** 
WAN and PINN versus Kolmogorov-Fokker-Plank
* **Problem**
Идея решения дифференциальных уравнений в частных производных с помощью операторных методов не нова. В 2020 году был предложен способ решения таких уравнений путем нахождения не точного, а слабого решения. Требуется связать этот подход с PINN и сравнить на простых задачах вроде стационарного случая процесса Фоккера-Колмогорова-Планка.
* **Data**
    - [1]   [бенчмарк для решения PDE](https://github.com/pdebench/PDEBench)
    - [2] синтетика
* **Reference**
    - [1] Weak Adversarial Networks for High-dimensional Partial Differential Equations [ссылочка](https://arxiv.org/pdf/1907.08272)
    - [2] opPINN: Physics-Informed Neural Network with operator learning to approximate solutions to the Fokker-Planck-Landau equation. [ссылочка](https://arxiv.org/pdf/2207.01765)
    - [3] Kovachki, Nikola B., Samuel Lanthaler, and Andrew M. Stuart. "Operator learning: Algorithms and analysis." arXiv preprint arXiv:2402.15715 (2024). [https://doi.org/10.48550/arXiv.2402.15715](https://doi.org/10.48550/arXiv.2402.15715)
* **Novelity**
Пока что такого никто не делал.
* **Authors** 
    - Expert: Стрижов
    - Consultant: Папай Иван

## Problem 202

* **Title**
  Detecting Optimization Regimes via Convergent Cross Mapping

* **Problem**
  Deep neural network training is a high-dimensional, non-convex optimization process where the internal dynamics of the weights are often opaque. While practitioners monitor scalar metrics (loss, gradient norms), standard correlations fail to capture the complex, time-varying interactions between these metrics and the optimizer's state.

  **Problem Statement:** We formulate the diagnostic task as a reconstruction problem: given a partial observation sequence yₜ (scalars) generated by a stochastic dynamical system wₜ₊₁ = F(wₜ, ξₜ) (where ξₜ represents data batches or hyperparameter schedules), we aim to recover the properties of the optimization trajectory and identify the causal drivers of convergence without accessing the full weight matrices.

  This project proposes to adapt Convergent Cross Mapping (CCM) and Partial CCM to deep learning dynamics. To address the non-stationarity of training (e.g., learning rate decay) and the stochasticity of SGD, we ground our approach in Stark’s theorems on delay embeddings for forced systems, rather than standard Takens’ theory. In the long run, we plan to validate this framework on three specific optimization challenges:

  * **Hyperparameter Sensitivity:** We propose a "causal probing" method where hyperparameters are oscillated with low amplitude; we will then use Partial CCM to quantify their causal influence on validation accuracy, offering a potential alternative to expensive grid search.
  * **Edge of Stability:** We aim to characterize the statistical signatures of the loss landscape when the optimizer enters the unstable, chaotic regime at the edge of stability: we will track the impact of the gradient norm on the loss and find the embedding dimension for the loss via simplex projection.
  * **Grokking:** We hypothesize that the transition from memorization to generalization corresponds to a collapse in the dimensionality of the optimal embedding of the yₜ time series. We will try tracking this dimensionality to predict grokking events before they manifest in test loss.

  Ultimately, this research seeks to establish a statistical framework for diagnosing and predicting optimization regimes using only low-cost scalar logs.

* **Data**
  * CIFAR-10 to train a CNN for hyperparameter sensitivity and edge of stability experiments: https://docs.pytorch.org/vision/main/generated/torchvision.datasets.CIFAR10.html.
  * Trivial synthetic data for the modular addition task for grokking with a 1-Layer transformer (see https://github.com/neelnanda-io/Grokking).

* **References**
  **Convergent Cross-Mapping:**
  * Sugihara, G., et al. (2012). Detecting Causality in Complex Ecosystems. Science.
  * Leng, S., et al. (2020). Partial cross mapping eliminates indirect causal influences. Nature Communications.

  **Dynamical systems:**
  * Takens, F. (1981). Detecting strange attractors in turbulence. Dynamical Systems and Turbulence, Warwick 1980.
  * Stark, J. (1999). Delay Embeddings for Forced Systems. I. Deterministic Forcing. Journal of Nonlinear Science.
  * Stark, J., et al. (2003). Delay Embeddings for Forced Systems. II. Stochastic Forcing. Journal of Nonlinear Science.

  **ML:**
  * Cohen, J., et al. (2021). Gradient Descent on Neural Networks Typically Occurs at the Edge of Stability. ICLR.
  * Power, A., et al. (2022). Grokking: Generalization Beyond Overfitting on Small Algorithmic Datasets. arXiv.
  * Notsawo, P. J. T., et al. (2023). Predicting Grokking Long Before it Happens: A look into the loss landscape of models which grok. arXiv.

* **Baseline**
  * CCM: https://github.com/SugiharaLab/pyEDM?tab=readme-ov-file and https://github.com/PrinceJavier/causal_ccm
  * Edge of Stability: https://github.com/locuslab/edge-of-stability
  * Grokking: https://github.com/openai/grok/tree/main and https://github.com/neelnanda-io/Grokking

* **Proposed solution**
  Application and adaptation of time-series methods to neural network training. See https://github.com/alexlegeartis/CCM-for-Optimization/blob/main/project_proposal/ccm_opt.pdf.

* **Visualizations**
  * CCM curves (prediction skill vs library length) for different scalar parameter pairs (accuracy, loss, gradient norm, lr, and so on)
  * 3D Plot: Loss(t), Loss(t-τ​​), Loss(t-2τ​) for the Edge of Stability mode.
  * Embedding dimensionality(training steps) for grokking.

* **Error analysis**
  We compare the Granger test, CCM, Partial CCM, and our method, which is based on Stark's theorems, on a deep learning task with known causality. The examples are: sinusoidal learning rate and gradient norm, "ghost driver" (forces both momentum and weight decay, for instance), and the "poisoned batch" (from time to time, inject a batch with randomized labels and check causality between such events and validation loss).

* **Novelty**
  To the best of our knowledge, no one has yet applied time series methods to obtain information from the logs of loss, accuracy, and the gradient norm.

* **Authors**
  * Consultant: Alexey Kravatskiy (tg: [@alexlegeartis](https://t.me/alexlegeartis))
  * Expert: Vadim Strijov

## Problem 203
* **Title**
  SignMuon: fast as Muon, communication-effective as SignSGD

* **Problem**
  signSGD is a popular algorithm due to its strong performance in both centralized and decentralized settings: first, signSGD performs almost as well as Adam (because it *is* essentially Adam without exponential moving averages), and second, it is communication-efficient because it transmits up to 32x fewer bits than standard optimizers.

  We propose applying the sign compressor to Muon, an algorithm that recently outperformed Adam in training both computer vision networks and transformers. In preliminary experiments, the resulting algorithm, SignMuon, was empirically almost on par with Muon in the centralized setting and outperformed signSGD in both centralized and federated settings. The current goal is to establish convergence guarantees for the algorithm and potentially modify it to improve convergence. It would also be interesting to examine the broader family of SignA algorithms, where A is an LMO (linear minimization oracle)-based algorithm. SignSignSGD and SignNormalizedSGD are simply SignSGD, but there are other viable LMO-based algorithms besides Muon, such as F-Muon and S-Muon, which use composite norm balls for the LMO set.

  Regardless of theoretical advances, which are difficult to predict, we plan to benchmark SignMuon and its possible modifications on a wide range of problems: synthetic problems, CIFAR-airbench, federated training for MNIST/CIFAR-10 classification, and, finally, pretraining or fine-tuning NanoGPT.


* **Data**
  * Image datasets MNIST and CIFAR-10 for CNN training: https://docs.pytorch.org/vision/main/generated/torchvision.datasets.MNIST.html and https://docs.pytorch.org/vision/main/generated/torchvision.datasets.CIFAR10.html.
  * Text dataset FineWeb for NanoGPT training: https://huggingface.co/datasets/HuggingFaceFW/fineweb.

* **References**
  **SignSGD:**
  * Bernstein, J., et al. (2018). signSGD: Compressed Optimisation for Non-Convex Problems. ICML.
  * Bernstein, J., et al. (2019). signSGD with Majority Vote is Communication Efficient And Fault Tolerant. ICML.

  **Muon and LMO-based algorithms:**
  * Bernstein, J., Newhouse L. (2024). Old Optimizer, New Norm: An Anthology. arXiv
  * Jordan, K., et al. (2024). Muon: An Optimizer for Hidden Layers in Neural Networks. Blog post.
  * Kovalev, D. (2025). Understanding Gradient Orthogonalization for Deep Learning via Non-Euclidean Trust-Region Optimization. arXiv.
  * Kravatskiy, A., et al. (2025). The Ky Fan Norms and Beyond: Dual Norms and Combinations for Matrix Optimization. ICOMP.

* **Baseline**
  * Muon: https://github.com/KellerJordan/muon
  * CIFAR-10 airbench: https://github.com/KellerJordan/cifar10-airbench
  * Modded-NanoGPT: https://github.com/KellerJordan/modded-nanogpt
  * Preliminary SignMuon experiments on CIFAR-10 and a synthetic smooth problem, as well as F-Muon and S-Muon implementations: https://github.com/alexlegeartis/Neon/blob/main/code/optimizers.py (the settings are taken from https://arxiv.org/pdf/2512.09678)
  * Federated learning backbone: https://github.com/AnonSubmitter135/FedEOV (we also have a private fork of this repo with signSGD and SignMuon implementation)

* **Proposed solution**
  We substitute the gradient G in SignSGD's update with Muon's UV^T, where G = U Sigma V^T is the singular value decomposition of the gradient.

* **Novelty**
  Although other works have proposed the quantization of Muon and error feedback with bidirectional compression for it, no one appears to have explored its signed version.

* **Authors**
  * Consultant: Alexey Kravatskiy (tg: [@alexlegeartis](https://t.me/alexlegeartis))
  * Expert: Dmitry Kovalev

## Problem 204
* **Title**
  Optimizing Sphere Packings and Kissing Numbers via AlphaEvolve and ImprovEvolve
* **Problem**
  The LLM-powered evolutionary coding agent AlphaEvolve has recently gained attention for achieving improved bounds and algorithms across a wide range of mathematical problems. Notable examples include an improvement over Strassen's matrix multiplication algorithm and a new state-of-the-art construction of 593 spheres for the kissing number problem in 11 dimensions (the problem of arranging as many non-overlapping unit spheres as possible so they touch a common unit sphere). Although AlphaEvolve's advances are diverse, they are clearly not definitive, as concurrent articles regularly demonstrate by reproducing or claiming to improve upon the AlphaEvolve framework (ShinkaEvolve, ThetaEvolve, TTT-Discover, etc.). These improvements often occur for less significant mathematical problems, such as circle packing and autocorrelation inequalities, so it is natural to ask how far the bounds can be pushed for more substantial mathematical challenges.

  Since we are not the DeepMind AlphaEvolve team, we propose to focus on a specific yet mathematically significant problem. AlphaEvolve managed to improve the lower bound for the kissing number problem only in 11 dimensions, and only by one sphere (from 592 to 593). The significant gap between the known lower and upper bounds suggests that much more progress is possible in this area.

  The kissing number is related to optimal spherical codes and sphere packing. Indeed, a spherical code that separates its points on a sphere by at least 60 degrees represents a valid center configuration for kissing spheres, and sphere packing can be viewed as a relaxation of the kissing number problem: the goal is to maximize the density of spheres in an unbounded space. These problems share much more than formulation similarity: their state-of-the-art solutions heavily rely on lattice structures and more intricate algebraic objects (see Ganzhinov's article, for example). For this reason, we suggest approaching the problems in parallel.

  In our recent ImprovEvolve article, we showed that it is better to solve a mathematical problem by iteratively optimizing the current solution rather than constructing a perfect one from scratch. With this approach, the solution is transferable between dimensions and can be derived from an earlier state-of-the-art result.

  Our plan is twofold. First, we delve into the mathematics underlying sphere packings, aiming to understand the available approaches for constructing them. Second, we transfer this knowledge into Python to work with GigaEvo, our open-source implementation of AlphaEvolve, in general, and ImprovEvolve in particular.

  We envision two ways to discover new packings. The first is to train ImprovEvolve to improve configurations, then start the evolved program from human state-of-the-art configurations. However, due to the tightness of lattices, this approach may yield only marginal increments, like AlphaEvolve did. Nonetheless, we expect some progress even with this method, especially for sphere packing, where we will start from the recently discovered packing based on the antipode construction.

  The second approach is to adapt the ImprovEvolve framework to our problems. We will need to optimize discrete lattices rather than points in Euclidean space, so it makes sense to add some group theory modules. If we succeed, the constructions will be easily interpretable, which was not the case for AlphaEvolve and its large integer center coordinates.

  The prerequisites for this project are a desire to learn and a confident mastery of university-level mathematics, rather than prior knowledge of the research topic. Modern LLMs excel in mathematics as well, so it is likely they will do most of the work, but a high-level understanding of the problem and a willingness to debug the LLM output are required.


* **Data**
  * Lower and upper bounds for the kissing number problem with references: https://cohn.mit.edu/kissing-numbers/
  * Spherical codes: http://neilsloane.com/packings/

* **References**
  **Evolutionary coding agents:**
  * Trailblazer article: Novikov, A., et al. (2025). AlphaEvolve: A Coding Agent for Scientific and Algorithmic Discovery. arXiv preprint.
  * Follow-up: Georgiev, B., et al. (2025). Mathematical exploration and discovery at scale. arXiv preprint.
  * Open-source implementation: Khrulkov, V., et al. (2025). GigaEvo: An Open Source Optimization Framework Powered by LLMs and Evolution Algorithms. arXiv preprint.
  * Technique of improving the solution: Kravatskiy, A., et al. (2026). ImprovEvolve: Ask AlphaEvolve to Improve the Input Solution and Then Improvise. arXiv preprint.


  **Mathematics:**
  * Recent article on the packing, which we will use as a primer for ImprovEvolve: Chen, R., et al. (2025). New Sphere Packings from the Antipode Construction. arXiv preprint.
  * Kissing number article: Ganzhinov, M. (2025). Highly Symmetric Lines. Linear Algebra and Its Applications.
  * Alternative to evolution: Ma, C., et al. (2025). Finding Kissing Numbers with Game-Theoretic Reinforcement Learning. arXiv preprint.

* **Baseline**
  * GigaEvo: https://github.com/FusionBrainLab/gigaevo-core
  * ImprovEvolve: we have a private a private fork of the repo with ImprovEvolve implementation

* **Proposed solution**
  1) We implement the proposed configurations and use them as initial configurations for the improver program that we obtain by ImprovEvolve evolution.
  2) We devise a way to optimize lattices rather than sphere centers in isolation.

* **Novelty**
  Beyond the obvious mathematical novelty of the discovered constructions, we are likely to propose a sophisticated structure for the program that searches for configurations. To the best of our knowledge, even the search using the generate_config–improve–perturb trinity of ImprovEvolve is quite novel.
* **Authors**
  * Consultant: Alexey Kravatskiy (tg: [@alexlegeartis](https://t.me/alexlegeartis))
  * Experts: Valentin Khrulkov and Ivan Oseledets
 
## Задача 199
* __Название__: Sample Complexity of Feature Selection in Deep Tabular Models

* __Задача__: In learning theory, sample complexity determines how much data is required for generalization. For linear models, classical results establish relationships between sample size, total dimensionality, and number of relevant features. However, for neural networks, the interplay between feature selection, data requirements, and model complexity remains poorly understood. Key open questions include: How does the required sample size scale with the number of irrelevant features when training neural networks? How do different feature selection methods affect this scaling? How do feature correlations impact the data efficiency of selection algorithms? This work aims to empirically investigate the sample complexity of modern feature selection methods for deep tabular models through controlled experiments.

* __Литература__:
- Yamada, Y., Lindenbaum, O., Negahban, S., & Kluger, Y. (2020). Feature selection using Stochastic Gates. ICML.
Lee, C., Imrie, F., & van der Schaar, M. (2021). Self-Supervision Enhanced Feature Selection with Correlated Gates. NeurIPS.
- Yasuda, T., et al. (2023). Sequential Attention for Feature Selection. ICLR.
Das, A., & Kempe, D. (2011). Submodular meets spectral: Greedy algorithms for subset selection. ICML.
Elenberg, E. R., et al. (2018). Restricted strong convexity implies weak submodularity. The Annals of Statistics.

* __Methods under investigation__:
- Stochastic Gates (STG) — Gaussian-based continuous relaxation
- Sequential Attention — adaptive greedy-style selection with attention
- SEFS — correlated gating with self-supervision
- LASSO — linear baseline with known theoretical guarantees
  
* __Авторы__:
	- Консультант: Мешков Владислав, Эйнуллаев Алтай, Рубцов Денис
	- Эксперт: Грабовой Андрей

## Задача 209
* __Название__: Большие языковые модели в применении к иерархической суммаризации и генерации интеллект-карт
* __Задача__: Иерархические сводки и интеллект-карты текстов документов/подборок документов являются инструментом, позволяющим эффективно организовывать информацию в порядке от главного к деталям. Создание подобных представлений информации, однако, весьма трудозатратно, поэтому перспективной становится задача автоматизации этого процесса. На данный момент исследований по данной теме немного, каждое представляет задачу по-своему и оценивает качество своим набором метрик. Предлагается сравнить существующие методы построения иерархических представлений текстов и сравнить их с применением больших языковых моделей в данной задаче на существующих выборках с использованием различных общих метрик. Предполагается, что результаты данной работы можно будет включить в публикацию по результатами более обширного исследования по теме автоматической иерархической суммаризации.
* __Особенности задачи__:
    - Существуют __различные постановки задачи__, для каждой из которых свои данные и модели. Необходимо будет их сравнить и обобщить.
    - __Нет общепринятых метрик__ для оценивания качества в данной задаче, поэтому предлагается использовать метрики из разных работ и сравнить их, а также применить новые (например, TTED [[5]](https://github.com/intsystems/Sobolevsky-MS-Thesis/blob/main/paper/IEEE_APEIE_2025/Sobolevsky2025TTED_IEEE_KNOTH.pdf)).
    - Объект генерации в данной задаче - __текстовые деревья__, т. е. структуры, объединяющие в себе свойства текстов и деревьев. Из-за этого теоретическая основа данной задачи становится уникальным сочетанием дискретной математики и NLP.
    - В качестве нового метода предлагается применить __большие языковые модели__, что предполагает работу с промпт-инжинирингом и развёртывание моделей локально либо взаимодействие с ними через API.

* __Литература__:
  	- [[1]](https://aclanthology.org/P14-1085.pdf) _J. Christensen, S. Soderland, G. Bansal_ Hierarchical summarization: Scaling up multi-document summarization
	- [[2]](https://aclanthology.org/L18-1503.pdf) _C. Tauchmann, T. Arnold, A. Hanselowski et al._ Beyond generic summarization: A multi-faceted hierarchical summarization corpus of large heterogeneous data 
	- [[3]](https://ojs.aaai.org/index.php/AAAI/article/download/29935/31634) _Z. Zhang, M. Hu, Y. Bai, Z. Zhang_ Coreference graph guidance for mind-map generation
    - [[4]](https://ib-bank.ru/bisjournal/post/2290) _Воронцов К., Курилов В._ Карты знаний. На пути к доверенным языковым моделям и системам представления знаний
	- [[5]](https://github.com/intsystems/Sobolevsky-MS-Thesis/blob/main/paper/IEEE_APEIE_2025/Sobolevsky2025TTED_IEEE_KNOTH.pdf) _F. Sobolevsky, K. Vorontsov_ Text Tree Edit Distance: A Language Model-Based Metric for Text Hierarchies
* __Данные__: Выборки из работ [[2]](https://aclanthology.org/L18-1503.pdf), [[3]](https://ojs.aaai.org/index.php/AAAI/article/download/29935/31634). Возможно, существуют и другие.
* __Базовые методы__: Методы из работ [[1]](https://aclanthology.org/P14-1085.pdf), [[3]](https://ojs.aaai.org/index.php/AAAI/article/download/29935/31634). Возможно, существуют и другие.
* __Авторы__:
	- Консультант: Соболевский Федор (tg: @theofficialfjord)
	- Эксперт: д. ф.-м. н. Воронцов Константин Вячеславович

## Задача 210
* __Title__: Cross-model knowledge distillation for vision encoders
* __Problem__: Most of existing vision-semantic embedding methods require pre-trained visual features from models trained with supervised classification on ImageNet. This raises a fundamental question: **Is the supervised pre-training stage necessary, or can language models and word embeddings alone provide sufficient supervision to train vision encoders from random initialization?** This tests whether distributional semantics contain enough structural information to guide visual representation learning without any intermediate softmax classification stage.
* __Data__:
    - ImageNet-1K
    - __Word2Vec__: Pre-trained word embeddings (such as Word2Vec and FastText) and language models (such as BERT and its improvements)
* __Reference__:
    - Kim et al., "COSMOS: Cross-Modality Self-Distillation for Vision Language Pre-training", CVF 2025
	- Frome et al., "DeViSE: A Deep Visual-Semantic Embedding Model," NeurIPS 2013
	- Norouzi et al., "Zero-Shot Learning by Convex Combination of Semantic Embeddings," ICLR 2014
	- Kodirov et al., "Semantic Autoencoder for Zero-Shot Learning," CVPR 2017
	- Akata et al., "Label-Embedding for Image Classification," TPAMI 2016
	- Mikolov et al., "Efficient Estimation of Word Representations," ICLR 2013
* __Baseline__: shared encoders trained in a supervised/semi-supervised manner
* __Proposed solution__: we consider the problem under the knowledge distillation framework: the student (vision model) tries to restore as much knowledge as possible from the language model. We will consider the distillation in a multi-task regime considering generalizability between multiple pairs of language models and vision datasets. 
* __Novelty__: We propose an approach to train multi-modal encoder with shared semantic knowledge based on the knowledge distillation framework. Most of the prior works rely on pre-extracted visual features from ImageNet-trained models, making it impossible to isolate whether semantic embeddings alone suffice for visual representation learning.
* __Authors__:
	- Consultant: Muhammadsharif Nabiev (tg: @AJommmy)
 	- Expert: Oleg Bakhteev (tg: @@leg_bah)

## Задача 211

* __Название__: Спектральный анализ устойчивости рекуррентного трансформера с Layer Normalization
* __Задача__: Исследовать влияние центрирования и аффинных преобразований в LayerNorm (LN) на динамическую устойчивость рекуррентного (looped) блока трансформера и сравнить результаты с RMSNorm. В отличие от RMSNorm, LN выполняет вычитание среднего: $\text{LN}(x) = \frac{x - \mu}{\sigma} \cdot \gamma + \beta$. Требуется: (1) Вывести аналитическую верхнюю границу спектральной нормы Якобиана полного блока ($J_F$) с использованием LN, учитывая проектор центрирования $P = I - \frac{1}{D}\mathbf{1}\mathbf{1}^\top$; (2) Доказать или опровергнуть, что LN обеспечивает асимптотическую устойчивость ($O(1)$) при больших шагах обновления $\nu \to \infty$, аналогично RMSNorm; (3) Проанализировать влияние обучаемого смещения $\beta$ (bias) на фиксированные точки динамики (fixed points); (4) Эмпирически сравнить скорость сходимости (contraction rate) и спектральные свойства LN и RMSNorm на синтетических данных и эмбеддингах CIFAR-10.
* __Литература__: [Recurrent Self-Attention Dynamics:
An Energy-Agnostic Perspective from Jacobians](https://arxiv.org/pdf/2505.19458)
* __Авторы__:
  * Консультанты: Дмитрий Василенко (tg: [@dimundeI](https://t.me/dimundeI)), Илья Степанов (tg: [@Iliatut94](https://t.me/Iliatut94)), Вадим Касюк(tg: [@vadimkasiuk](https://t.me/vadimkasiuk))
  * Эксперт: Грабовой Андрей (tg: [@hrabovyi](https://t.me/hrabovyi))


# Прикладные проекты

## Задача 190
* __Название__: Детекция строк в фотографиях страниц рукописных текстов
* __Задача__: Для обработки рукописных текстов зачастую необходимо находить строки текста на изображении. Задача не всегда тривиальна, так как изображения зачастую содержат шум: плохо освещены, повернуты, есть посторонние предметы, сами строки неровно расположены. На выходе ожидается репозиторий с python библиотекой для препроцессинга и детекции строк в изображениях с рукописными текстами (в первую очередь на русском языке).
* __Авторы__:
  * Ксения Варламова (tg: [@Kseny_var](https://t.me/Kseny_var))

## Задача 191
* __Название__: Контекстно зависимая валидация и редакция распознанных рукописных текстов
* __Задача__: Зачастую модели распознавания рукописных текстов (HTR) учитывают контекст уровня одной строки, из-за чего выход модели в начале/конце строки может быть менее качественным. Предлагается разработать способ редакции на уровне или уже распознанных слов, или векторов верхних слоев HTR.
* __Авторы__:
  * Ксения Варламова (tg: [@Kseny_var](https://t.me/Kseny_var))

## Задача 192
* __Название__: Синтез фрагментно измененных изображений
* __Задача__: Как известно, в машинном обучении очень высокая доля человекочасов тратится на сбор данных. Предлагается реализовать качественный синтез фрагментно измененных изображений, где под изменениями подразумевается широкий спектр преобразований, от наложения текста до изменений с помощью современных генеративных моделей. Такой сервис был бы полезен для задач обнаружения и сегментации искаженных изображений, в том числе AI-искаженных.
* __Авторы__:
  * Ксения Варламова (tg: [@Kseny_var](https://t.me/Kseny_var))

## Задача 193
* __Название__: Детекция визуального плагиата через бинарное логит-скоринг в Vision-Language моделях
* __Задача__: Предыдущие работы, посвященные попарному сравнению изображений для детекции визуального плагиата [1](https://elibrary.ru/item.asp?id=83189193), [2](https://github.com/DorinDaniil/Image-Transform-Predict). Наибольшую эффективность показывают методы на основе контрастивного и self-supervised обучения, обучающие инвариантные к аугментациям эмбеддинги. Однако остается проблема балансировки precision и recall: при высоком recall для обнаружения широкого спектра преобразований неизбежно растет число ложных срабатываний, особенно в доменах с высокой семантической схожестью. Предлагаемый подход: использование логитов бинарных ответов ("да"/"нет") VLM, например, на запрос "Является ли второе изображение преобразованной версией первого?"; использование предобученной open-source VLM для проверки базовой гипотезы (базовый эксперимент); в перспективе — дообучение через LoRA и архитектурное упрощение. Модели для экспериментов: [Qwen2.5-VL](https://huggingface.co/Qwen/Qwen2.5-VL-7B-Instruct), [Qwen3-VL](https://huggingface.co/Qwen/Qwen3-VL-4B-Instruct).
* __Авторы__:
  * Даниил Дорин (tg: [@danulkin](https://t.me/danulkin))

## Задача 194
* __Название__: Использование перплексии для детекции машинно сгенерированных текстов
* __Задача__: Цель работы — исследовать применимость перплексии и ее модификаций для детекции ИИ-генерированных текстов на русском языке. Перплексия часто раньше использовалась для разделения сгенерированных и человеческих текстов, однако в последнее время видим, что такие классификаторы недостаточно робастны. Однако таких исследований особо не проводилось для других языков. Интересно было бы сравнить паттерны различий перплексии для разных языков и разных жанров, чтобы дать итоговую оценку, есть ли смысл обращаться к этой метрике при построении детекторов.
* __Авторы__:
	- Консультант: Минашкин Владислав (tg: [@minashkinvladislav](https://t.me/minashkinvladislav))
	- Эксперт: Герман Грицай (tg: [@ggritsay](https://t.me/ggritsay))

## Задача 195
* __Название__: Запоминание предыдущих токенов (Memorization of Preceding Tokens)
* __Задача__: Запоминание предыдущих токенов как паттерн для детекции машинно-сгенерированных текстов. Большая часть методов детектирования машинно-сгенерированных текстовых фрагментов анализируют только способность LLM предсказывать следующий токен, но игнорируют информацию, содержащуюся в логитах о предшествующих токенах. На основе недавнего исследования есть теория, что для человеческих текстов модель хуже предсказывает следующий токен, но лучше помнит предыдущий. Предлагается сравнить запоминание токенов для разных языков и различных жанров с использованием open-source легких моделей [https://neurips.cc/virtual/2024/poster/95814](https://neurips.cc/virtual/2024/poster/95814).
* __Авторы__: 
	- Консультант: Минашкин Владислав (tg: [@minashkinvladislav](https://t.me/minashkinvladislav))
	- Эксперт: Герман Грицай (tg: [@ggritsay](https://t.me/ggritsay))

## Задача 196
* __Название__: Семантическая связность токенов (Token cohesiveness)
* __Задача__: Семантическая связность токенов внутри текста как усиление существующих детекторов машинно-сгенерированных фрагментов. Выдвигается гипотеза, что тексты, сгенерированные LLM, обладают более высокой связностью токенов, чем тексты, написанные людьми. Формально связность токенов определяется как ожидаемая семантическая разница между исходным текстом и его версией, из которой случайным образом удалена небольшая доля токенов. У LLM связность выше, потому что генерация каждого токена зависит каузально от всех предыдущих, что ведёт к более плотной семантической структуре. Предлагается сравнить семантическую связность токенов для разных языков и различных жанров. Оценить повышение качества актуальных решений с надстройкой token cohesiveness [https://arxiv.org/pdf/2409.16914](https://arxiv.org/pdf/2409.16914).
* __Авторы__:
	- Консультант: Минашкин Владислав (tg: [@minashkinvladislav](https://t.me/minashkinvladislav))
	- Эксперт: Герман Грицай (tg: [@ggritsay](https://t.me/ggritsay))

## Задача 197
* __Название__: Анализ внутренних признаков языковых моделей (Text Fluoroscopy)
* __Задача__: Исследование внутренних признаков и промежуточных представлений LLM для детекции машинно-сгенерированных текстов. Большая часть существующих подходов детекции машинно-сгенерированного текста делится на две группы: 1) на основе семантических признаков (последние слои BERT/RoBERTa): хорошо работают на обучающей области, но плохо обобщаются на новые домены; 2) на основе лингвистических признаков (n-граммы, POS-теги и т.д.): более обобщаемы, но уязвимы к перефразированию. Исследование предполагает отход от крайних уровней абстракции и переход к промежуточным значениям, где подразумевается формирование стиля генерации. Также предлагается более детально рассмотреть отдельные слои моделей при помощи инструментов интерпретации (прим. Gemma Scope 2). Предлагается сравнить внутренние признаки и их интерпретацию для разных языков и различных жанров [https://aclanthology.org/2024.emnlp-main.885.pdf](https://aclanthology.org/2024.emnlp-main.885.pdf).
* __Авторы__:
	- Консультант: Минашкин Владислав (tg: [@minashkinvladislav](https://t.me/minashkinvladislav))
	- Эксперт: Герман Грицай (tg: [@ggritsay](https://t.me/ggritsay))

## Задача 198
* __Название__: Анализ групповой структуры $D_4$ в модели предсказания последовательностей преобразований
* __Задача__: Показать, что нейросетевая модель способна внутренне выучить алгебраическую структуру диэдральной группы $D_4$ (симметрии квадрата), а не просто запоминать шаблоны. Вход — пара изображений, связанных элементом $g \in D_4$ или несвязанных ($\varnothing$); выход — элемент группы или $\varnothing$. Требуется доказать, что модель: (1) инвариантна к выбору последовательности операций, реализующих один элемент группы (например, `horizontal_flip` → `vertical_flip` ≡ `rotate_180`); (2) согласована с композицией: если $\mathbf{I}^2 = g_1(\mathbf{I}^1)$ и $\mathbf{I}^3 = g_2(\mathbf{I}^2)$, то предсказание для $(\mathbf{I}^1, \mathbf{I}^3)$ совпадает с $g_2 \cdot g_1$; (3) выдает каноническое представление элемента группы; (4) корректно обнаруживает несвязанные пары. Анализ внутренних представлений (attention maps, эмбеддинги) должен продемонстрировать кодирование таблицы умножения $D_4$. База — авторегрессивная архитектура (Siamese encoder + Transformer decoder) из работы [Image-Transform-Predict](https://github.com/DorinDaniil/Image-Transform-Predict). Контекст: современные генеративные модели (Kandinsky 5.0) и VLM (Qwen3-VL-4B-Instruct) плохо понимают геометрические зависимости между изображениями.
* __Авторы__:
  * Даниил Дорин (tg: [@danulkin](https://t.me/danulkin))
  * Грабовой Андрей


<!---
## Problem template (EN)
## Problem 101
* __Title__: Title
* __Problem__: Problem description
* __Data__: Data description
* __Reference__: Links to the literature
* __Baseline__: baseline description
* __Proposed solution__: description of the idea to implement in the project
* __Novelty__: why the task is good and what does it bring to science?  (for editorial board and reviewers)
* __Authors__: supervisors, consultants, experts

## Шаблон задачи (RU)
## Задача 101
* __Название__: Название, под которым статья подается в журнал. 
* __Задача__: Описание или постановка задачи. Желательна постановка в виде задачи оптимизации (в формате argmin). Также возможна ссылка на классическую постановку задачи. 
* __Данные__: Краткое описание данных, используемых в вычислительном эксперименте, и ссылка на выборку. 
* __Литература__: Список научных работ, дополненный 1) формулировкой решаемой задачи, 2) ссылками на новые результаты, 3) основной информацией об исследуемой проблеме. 
* __Базовой алгоритм__: Ссылка на алгоритм, с которым проводится сравнение или на ближайшую по теме работу. 
* __Решение__: Предлагаемое решение задачи и способы проведения исследования. Способы представления и визуализации данных и проведения анализа ошибок, анализа качества алгоритма. 
* __Новизна__: Обоснование новизны и значимости идей (для редколлегии и рецензентов журнала). 
-->
