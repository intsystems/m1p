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

## Задача (Узнать актуальность)
* **Описание проблемы:** При оптимизации различных моделей в Машинном Обучении, часто возникают ситуации, когда стандартные методы типа градиентного спуска, работают не так эффективно. Поэтому приходится придумывать модификации, что сделать процедуру более стабильной и быстрой. В этом проекте предлагается поисследовать sign оператор в следующих постановках: (L0,L1) гладкость минимизируемой функции, борьба с тяжёлым шумом,  сходимость с высокой вероятностью, обобщение на выпуклые функции. Проект во многом теоретический, придется доказывать вещи из оптимизации. И не факт, что все получится, это нормально. Но и небольшие эксперименты будут. Релевантные статьи: https://arxiv.org/abs/1802.04434 https://arxiv.org/abs/2502.07923 https://arxiv.org/pdf/2409.14989
* **Авторы:** Корнилов Никита, Марк Иконников 

## Задача 177 (Нужно узнать актуальность)
* __Название__: Кодирование дискриминативных и генеративных моделей
* __Задача__: В работе исследуются различные методы энкодинга нейронных сетей, применяемые в дискриминативных и генеративных моделях. Основная цель проекта — имплементация и сравнительный анализ существующих методов энкодинга, представленных в научных статьях. Результатом проведенного исследования ожидается разработанная библиотека, объединяющая различные методы энкодинга, что позволит упростить их применение в практических задачах. В рамках проекта также предлагается изучить возможность комбинирования нескольких методов энкодинга и теоретически обосновать их совместную применимость. Например, рассмотреть ортогональности методов в функциональном пространстве, что может способствовать улучшению качества и эффективности кодирования нейронных сетей.
* __Данные__: CIFAR
* __Литература__:
	- [[1]](https://arxiv.org/pdf/2406.09997)
	- [[2]](https://arxiv.org/pdf/1703.03400)
	- [[3]](https://arxiv.org/pdf/2403.02484)
* __Базовый алгоритм__: [https://github.com/HSG-AIML/SANE](https://github.com/HSG-AIML/SANE) — интересный метод кодирования сеток, подходящий как для генеративных, так и дискриминативных моделей.
* __Авторы__:
	- Консультант: Никитина Мария
	- Эксперт: Бишук Антон

## Задача 179 (Нужно узнать актуальность)
* **Title:** Бандиты для Query selection
* **Problem:** 
In today's world, tools are needed for efficient data processing. Databases underlie all such systems, but as their complexity increases, the task of **Query Optimization** arises. In this paper, you will have to figure out this problem, implement a solution based on the Multi-Armed Bandits method proposed in [4], and also suggest a way to improve the proposed algorithm.
* **Data:**
Will be determined after the algorithm is developed.
* **Reference:**
	- [1] Hazan E. et al. Introduction to online convex optimization //Foundations and Trends® in Optimization. – 2016. – Vol. 2. – No. 3-4. – Pp. 157-325.
	- [2] Cesa-Bianchi N., Lugosi G. Prediction, learning, and games. – Cambridge University Press, 2006.
	- [3] Bandits M. A. Introduction to Multi-Armed Bandits.
	- [4] Marcus R. et al. Bao: Making learned query optimization practical //Proceedings of the 2021 International Conference on Management of Data. – 2021. – С. 1275-1288.
* **Baseline:**
Implement [4] and check it in work.
* **Proposed solution:** 
To implement contextual bandit algorithm in [4]. Improve the quality using contextual bandits.
* **Novelty:**
There is a rumour, that the result in [4] is not reproduced in practice. It is necessary to check this and suggest an improvement.
* **Authors:**
	- Expert Yuriy Dorn
	- Consultant: Ilgam Latypov

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

 ## Задача 187 (Вадим Викторович)
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

 ## Задача 188 (Вадим Викторович)
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

# Проекты от пятикурсников
Сюда добавить задачи студентам Андрея Грабового

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
