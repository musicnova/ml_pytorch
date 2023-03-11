2. Выберите верные утверждения
1. MaxPool по умолчанию сжимает изображение во столько раз по каждому измерению, каков его размер по соответствующему измерению (с точностью до округления) ДА
2. MaxPool с ядром размера K содержит K x K параметров НЕТ
3. Если увеличить изображение ровно в 2 раза по каждой из размерностей, то число операций в свертке 1 x 1 без пулинга и страйда вырастет ровно в 4 раза (страйд по умолчанию) ДА
4. Свертка c ядром 1x1 над каждым пикселем работает точно так же, как и линейный слой над входом ДА
5. Любой пулинг — это нелинейная операция НЕТ

Ответ введите в виде строки, в которой будут перечислены пункты, соответствующие правильным ответам, разделенные пробелом
Пример:
1 3 5

ChatGPT, [11.03.2023 11:33]
1 4

верно ли, что MaxPool по умолчанию сжимает изображение во столько раз по каждому измерению, каков его размер по соответствующему измерению (с точностью до округления)?

ChatGPT, [11.03.2023 11:34]
Нет, MaxPool не по умолчанию сжимает изображение во столько раз по каждому измерению, каков его размер по соответствующему измерению. Вместо этого пользователь должен задать размер окна и шаг для MaxPool, чтобы определить, насколько сильно изображение будет сжиматься.

верно ли, что MaxPool с ядром размера K содержит K x K параметров?

ChatGPT, [11.03.2023 11:35]
Неверно. В алгоритме MaxPool нет параметров.

верно ли, что если увеличить изображение ровно в 2 раза по каждой из размерностей, то число операций в свертке 1 x 1 без пулинга и страйда вырастет ровно в 4 раза (страйд по умолчанию)?

ChatGPT, [11.03.2023 11:35]
Нет, это неверно. Число операций в свертке 1x1 без пулинга и страйда вырастет в 2 раза.

верно ли, что  Свертка c ядром 1x1 над каждым пикселем работает точно так же, как и линейный слой над входом?

ChatGPT, [11.03.2023 11:36]
Нет, это неверно. Свертка с ядром 1x1 над каждым пикселем использует только один параметр для применения к каждому пикселю, в то время как линейный слой использует множество параметров для применения ко всему входу.

верно ли, что Любой пулинг — это нелинейная операция?

ChatGPT, [11.03.2023 11:36]
Нет, неверно. Нелинейными операциями называются операции, выполняемые на изображении, такие как свертка, расширение, дискретное дифференцирование и др. Пулинг — это специфический способ применения нелинейной операции, при котором используются малые фильтры.

Ответ: 1 3 4


1 4 SKIP
1 4 5 SKIP
2 4 SKIP
1 2 4 SKIP
1 3 SKIP