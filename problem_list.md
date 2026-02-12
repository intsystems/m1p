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
Необходимо разработать метод, который по параметрам (или их преобразованиям, например спектральным характеристикам) обученной генеративной модели: 1) предсказывает тип или состав датасета обучения; 2) оценивает различие между датасетами через расстояние между соответствующими представлениями моделей.  
  **Note:** Стоит опираться на спектральные или иные устойчивые характеристики весов и проверить метод на моделях, обученных на подвыборках стандартных датасетов. Кроме того можно изучить возможность использовать графовые сети и кодирование слоев для этой задачи.  
* __Постановка 2:__ ГВыходы генеративных моделей можно рассматривать как представление самих моделей и косвенно — данных обучения. Требуется построить метрику близости между моделями на основе различий в распределениях их сгенерированных данных.
Необходимо разработать метод получения эмбеддингов моделей, который: 1) использует статистики сгенерированных данных (или их признаковые представления); 2) обучает метрику близости между моделями без жёстко заданной функции расстояния; 3) позволяет выявлять сходство датасетов через сходство генеративных моделей.  
	**Note:** В качестве базового подхода предлагается обучать многобашенную сеть, сопоставляющую реальные и сгенерированные выборки разных групп и формирующую эмбеддинги с мета-признаками датасетов.
* __Постановка 3:__ Эмбеддинги генеративных моделей могут обладать заданной геометрической структурой, отражающей смешение базовых датасетов. Предлагается исследовать обучение эмбеддингов, в которых представление модели, обученной на смеси данных, выражается через комбинацию представлений базисных моделей. Цель — проверить, можно ли восстанавливать структуру смесей датасетов и управлять геометрией пространства моделей. Необходимо: 1) выделить базисные подвыборки (например, через кластеризацию в латентном пространстве); 2) обучить модели на базисах и их смесях; 3) построить эмбеддер моделей, учитывающий как метрику близости, так и геометрические ограничения (например, линейные комбинации эмбеддингов базисов).  
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
Apply The Fourier operator or other similar operator and use this transformation to predict the time series.
* **Proposed solution**
Using an operator learning framework, propose a solution for different types of operators used in physics, image analysis, etc. Propose an idea to implement ICA to reduce the dimensionality of an operator to compute it in an efficient way.
* **Novelity**
There are no soluton to learning the operators used in physics.
* **Authors** 
    - Expert: Стрижов
    - Consultant: Alexander Terentyev

 ## Задача 187 (Нужно узнать актуальность: Вадим Викторович)
 * __Title__: Hybrid Memory System for Personalized AI Agent Responses Using Knowledge Graphs
* __Problem__: Modern AI assistants, particularly in banking risk assessment, require personalized and context-aware interactions. However, they often lack effective memory mechanisms for recalling and utilizing past interactions, leading to impersonalized responses. This research develops a hybrid memory system that integrates short-term and long-term memory to improve personalization while maintaining computational efficiency. The proposed system combines short-term memory for preserving recent interactions and long-term memory for accumulating knowledge. Knowledge graphs (AriGraph) structure semantic and episodic memory, while an intelligent memory selection mechanism dynamically adjusts storage strategies based on interaction complexity and computational constraints. Additionally, triplets and subgraphs from the knowledge graph are transformed into structured memory storage for efficient retrieval and response generation.
* __Data__: The study uses open-source datasets. Potential sources include banking risk assessment interaction logs, knowledge graph datasets such as Wikidata and DBpedia, and conversation datasets.
* __Reference__:
  	- Li, X., Wang, S., Zeng, S., Wu, Y., & Yang, Y. (2024). A survey on LLM-based multi-agent systems: workflow, infrastructure, and challenges. Vicinagearth, 1(1), p.9.
 	- Huang, X., Liu, W., Chen, X., Wang, X., Wang, H., Lian, D., Wang, Y., Tang, R., & Chen, E. (2024). Understanding the planning of LLM agents: A survey. arXiv preprint arXiv:2402.02716.
 	- Anokhin, P., Semenov, N., Sorokin, A., Evseev, D., Burtsev, M., & Burnaev, E. (2024). Arigraph: Learning knowledge graph world models with episodic memory for LLM agents. arXiv preprint arXiv:2407.04363.
 	- Hu, M., Chen, T., Chen, Q., Mu, Y., Shao, W., & Luo, P. (2024). Hiagent: Hierarchical working memory management for solving long-horizon agent tasks with large language models. arXiv preprint arXiv:2408.09559.
* __Baseline__: The baseline approaches compared with the proposed solution include retrieval-augmented generation (RAG), and hierarchical memory models like Hiagent. 
* __Proposed solution__: The research develops a hybrid memory system integrating different approaches for structured memory management. A modular architecture combines short-term (context-aware) and long-term (knowledge-based) memory with an intelligent selection mechanism optimizing retrieval efficiency. Knowledge graph triplets and subgraphs are transformed into structured memory representations.
Experimental validation on a banking risk assessment AI assistant evaluates personalization, retrieval efficiency, and response quality. Performance metrics include retrieval time, contextual accuracy using semantic similarity metrics, and storage efficiency versus response accuracy trade-offs.
* __Authors__:
	- Consultant: Ivan Novikov - Ph.D student at MIPT
		Seminarist on Quantitative Finance, research Scientist at Skolkovo.
		Consultant at InteRData and Scientific Programming Centre. 
		Participated in 7 industrial projects for banks and steel industry. 

 ## Задача 188 (Нужно узнать актуальность: Вадим Викторович)
 * __Title__: Multi-Agent Simulation for Economic and Social Behavior Modeling: From Individual Agents to Synthetic Populations and Integrated Environments
* __Problem__:
This project aims to develop a multi-agent simulation framework to model social and economic behavior in financial contexts, progressively advancing from individual agent decision-making to population-scale interactions and a fully integrated simulation environment. The research is structured into three phases:
 	- 1. Single-Agent Simulation: Modeling an LLM-based consumer agent that simulates decision-making, spatial mobility, and responses to financial stimuli.
 	- 2. Synthetic Population Modeling: Extending the framework to generate a heterogeneous synthetic population with realistic socio-economic characteristics and network interactions.
 	- 3. Integrated Multi-Agent Environment: Creating a large-scale, data-driven simulation that incorporates real socio-economic data, spatial topology, and agent synchronization for financial behavior analysis.

	This research bridges the gap between theoretical consumer behavior models and empirical financial decision-making. The findings can be applied in banking, financial risk assessment, and economic policy optimization.
* __Data__: The computational experiments will use the following datasets:
 	- Nielsen Consumer Panel Data – Consumer purchase behavior and spending trends.
 	- Public Census and Financial Data – Socio-economic and demographic datasets.
 	- Bank Transactional Data (Anonymized) – Patterns in financial decisions and responses to market changes.
 	- GIS Data for Spatial Analysis – Geospatial information to model mobility and location-based financial decisions.
* __Reference__:
	- Park et al. (2023). "Generative Agents: Interactive Simulacra of Human Behavior."
 	- Leng, Y. (2024). "Can LLMs Mimic Human-Like Mental Accounting and Behavioral Biases?"
	- Wang, J. et al. (2024). "Large Language Models as Urban Residents: An LLM Agent Framework for Personal Mobility Generation."
 	- Azamuke, D., et al. (2024). "MoMTSim: A Multi-agent-based Simulation Platform Calibrated for Mobile Money Transactions." IEEE Access.
 	- Guo, T. et al. (2024). "Large Language Model-based Multi-Agents: A Survey of Progress and Challenges." arXiv.
* __Baseline__:
	- 1. Baseline for agent-based simulations can be taken from AgentScope, an existing multi-agent framework optimized for large-scale simulations (arXiv:2407.17789).
	- 2. Existing financial decision models and LLM-based decision-making (Generative Agents).
* __Proposed solution__:
	- Phase / Project 1: Individual LLM-Based Consumer Agent
	An LLM-based agent is developed with structured financial reasoning, decision-making capabilities, and adaptive learning. It models consumer behavior by optimizing budget constraints, managing credit usage, and responding to financial incentives such as 		banking offers and interest rate changes. The agent navigates a simulated financial environment, making purchasing decisions and interacting with virtual financial entities. Its behavior is validated by comparing simulation results with real-world consumer 	transaction data.

	- Phase / Project 2: Synthetic Population and Network Interactions
	A synthetic population is generated using LLM-based personas with diverse demographic, financial, and psychographic characteristics. Network structures such as small-world and scale-free models capture peer influence, social interactions, and collective 		financial trends. The system models the emergence of financial behaviors such as herd effects, viral banking trends, and shifts in credit adoption. The synthetic population’s behavior is compared with empirical financial datasets to ensure representativeness 	and realism.

	- Phase / Project 3: Large-Scale Multi-Agent Environment
	A spatially structured multi-agent system is developed, integrating GIS data to model consumer mobility in urban and regional settings. Agents interact dynamically with banking institutions, businesses, and financial markets, responding to real-time 		macroeconomic changes. The simulation incorporates real-world socio-economic data, enabling predictive modeling of financial behavior under different economic policies. Optimization techniques ensure the framework scales efficiently for large simulations. The 	model is validated against historical financial events and economic trends.
* __Authors__
	- Consultant:
	Ivan Novikov - Ph.D stident at MIPT
	Seminarist on Quantitative Finance, research Scientist at Skolkovo.
	Consultant at InteRData and Scientific Programming Centre. 
	Participated in 7 industrial projects for banks and steel industry. 


## Задача 199
* __Название__: Анализ причинно-следственных связей между биомедицинскими сигналами (ЭЭГ-ЭКГ, ЭЭГ-МЭГ) через скрытые представления автоэнкодеров
* __Задача__: Исследование кросс-модальных причинно-следственных связей в нейрофизиологических данных. Основная гипотеза: связь между сердцем и мозгом (ЭЭГ ↔ ЭКГ) или между разными методами регистрации мозговой активности (ЭЭГ $\longleftrightarrow$ МЭГ) может быть выявлена через анализ динамики в скрытом пространстве. Предлагается архитектура из двух параллельных автоэнкодеров (по одному на модальность), после чего в латентном пространстве применяются методы оценки каузальности: Convergent Cross Mapping (CCM), transfer entropy или дифференциальные уравнения (Neural ODE/CDE). Цель — количественно оценить направленность влияния (мозг $\longrightarrow$ сердце vs сердце $\longrightarrow$ мозг).
* __Предыдщуие_результаты__:
	* Построен [метод апроксимации показаний fMRI по прослушиваемому звуковому ряду](https://github.com/intsystems/2024-Project-117/tree/master).
	* Построен [метод апроксимации показаний fMRI по видео ряду](https://github.com/DorinDaniil/Forecasting-fMRI-Images).
* __Данные__:
  * Мультимодальные записи во время прослушивания музыки: ЭЭГ, ЭМГ, ЭКГ — [OpenNeuro ds004840](https://openneuro.org/datasets/ds004840/versions/1.0.1)
  * Мультимодальные записи [Nature Scientific Data 2025](https://www.nature.com/articles/s41597-025-05580-x), [Pattern Recognition Letters 2017](https://www.sciencedirect.com/science/article/abs/pii/S0167865517304634), [Nature Scientific Data 2021](https://www.nature.com/articles/s41597-021-01046-y), [Human Brain Mapping 2023](https://onlinelibrary.wiley.com/doi/full/10.1002/hbm.26480)
* __Авторы__:
  * Даниил Дорин (tg: [@danulkin](https://t.me/danulkin))

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

# Индустриальные проекты от Антиплагиата

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
	* Герман Грицай (tg: [@ggritsay](https://t.me/ggritsay))

## Задача 195
* __Название__: Запоминание предыдущих токенов (Memorization of Preceding Tokens)
* __Задача__: Запоминание предыдущих токенов как паттерн для детекции машинно-сгенерированных текстов. Большая часть методов детектирования машинно-сгенерированных текстовых фрагментов анализируют только способность LLM предсказывать следующий токен, но игнорируют информацию, содержащуюся в логитах о предшествующих токенах. На основе недавнего исследования есть теория, что для человеческих текстов модель хуже предсказывает следующий токен, но лучше помнит предыдущий. Предлагается сравнить запоминание токенов для разных языков и различных жанров с использованием open-source легких моделей [https://neurips.cc/virtual/2024/poster/95814](https://neurips.cc/virtual/2024/poster/95814).
* __Авторы__: 
	* Герман Грицай (tg: [@ggritsay](https://t.me/ggritsay))

## Задача 196
* __Название__: Семантическая связность токенов (Token cohesiveness)
* __Задача__: Семантическая связность токенов внутри текста как усиление существующих детекторов машинно-сгенерированных фрагментов. Выдвигается гипотеза, что тексты, сгенерированные LLM, обладают более высокой связностью токенов, чем тексты, написанные людьми. Формально связность токенов определяется как ожидаемая семантическая разница между исходным текстом и его версией, из которой случайным образом удалена небольшая доля токенов. У LLM связность выше, потому что генерация каждого токена зависит каузально от всех предыдущих, что ведёт к более плотной семантической структуре. Предлагается сравнить семантическую связность токенов для разных языков и различных жанров. Оценить повышение качества актуальных решений с надстройкой token cohesiveness [https://arxiv.org/pdf/2409.16914](https://arxiv.org/pdf/2409.16914).
* __Авторы__:
	* Герман Грицай (tg: [@ggritsay](https://t.me/ggritsay))

## Задача 197
* __Название__: Анализ внутренних признаков языковых моделей (Text Fluoroscopy)
* __Задача__: Исследование внутренних признаков и промежуточных представлений LLM для детекции машинно-сгенерированных текстов. Большая часть существующих подходов детекции машинно-сгенерированного текста делится на две группы: 1) на основе семантических признаков (последние слои BERT/RoBERTa): хорошо работают на обучающей области, но плохо обобщаются на новые домены; 2) на основе лингвистических признаков (n-граммы, POS-теги и т.д.): более обобщаемы, но уязвимы к перефразированию. Исследование предполагает отход от крайних уровней абстракции и переход к промежуточным значениям, где подразумевается формирование стиля генерации. Также предлагается более детально рассмотреть отдельные слои моделей при помощи инструментов интерпретации (прим. Gemma Scope 2). Предлагается сравнить внутренние признаки и их интерпретацию для разных языков и различных жанров [https://aclanthology.org/2024.emnlp-main.885.pdf](https://aclanthology.org/2024.emnlp-main.885.pdf).
* __Авторы__:
	* Герман Грицай (tg: [@ggritsay](https://t.me/ggritsay))

## Задача 198
* __Название__: Анализ групповой структуры $D_4$ в модели предсказания последовательностей преобразований
* __Задача__: Показать, что нейросетевая модель способна внутренне выучить алгебраическую структуру диэдральной группы $D_4$ (симметрии квадрата), а не просто запоминать шаблоны. Вход — пара изображений, связанных элементом $g \in D_4$ или несвязанных ($\varnothing$); выход — элемент группы или $\varnothing$. Требуется доказать, что модель: (1) инвариантна к выбору последовательности операций, реализующих один элемент группы (например, `horizontal_flip` → `vertical_flip` ≡ `rotate_180`); (2) согласована с композицией: если $\mathbf{I}^2 = g_1(\mathbf{I}^1)$ и $\mathbf{I}^3 = g_2(\mathbf{I}^2)$, то предсказание для $(\mathbf{I}^1, \mathbf{I}^3)$ совпадает с $g_2 \cdot g_1$; (3) выдает каноническое представление элемента группы; (4) корректно обнаруживает несвязанные пары. Анализ внутренних представлений (attention maps, эмбеддинги) должен продемонстрировать кодирование таблицы умножения $D_4$. База — авторегрессивная архитектура (Siamese encoder + Transformer decoder) из работы [Image-Transform-Predict](https://github.com/DorinDaniil/Image-Transform-Predict). Контекст: современные генеративные модели (Kandinsky 5.0) и VLM (Qwen3-VL-4B-Instruct) плохо понимают геометрические зависимости между изображениями.
* __Авторы__:
  * Даниил Дорин (tg: [@danulkin](https://t.me/danulkin))

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
