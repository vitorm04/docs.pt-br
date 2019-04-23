---
title: Criar um classificador de imagens personalizadas do ML.NET com o TensorFlow
description: Descubra como criar um classificador de imagens personalizadas do ML.NET em um cenário de aprendizado de transferência do TensorFlow para classificar imagens reutilizando um modelo do TensorFlow pré-treinado.
ms.date: 04/05/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 9b9ac1f1f15b4003a19a3d30d6cadf3e86946376
ms.sourcegitcommit: 680a741667cf6859de71586a0caf6be14f4f7793
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59517961"
---
# <a name="tutorial-build-an-mlnet-custom-image-classifier-with-tensorflow"></a><span data-ttu-id="98bf4-103">Tutorial: Criar um classificador de imagens personalizadas do ML.NET com o TensorFlow</span><span class="sxs-lookup"><span data-stu-id="98bf4-103">Tutorial: Build an ML.NET custom image classifier with TensorFlow</span></span>

<span data-ttu-id="98bf4-104">Este tutorial de amostra ilustra como você pode usar um modelo de Classificador de Imagens `TensorFlow` já treinado para criar um novo modelo customizado para classificar imagens em algumas categorias.</span><span class="sxs-lookup"><span data-stu-id="98bf4-104">This sample tutorial illustrates how you can use an already trained Image Classifier `TensorFlow` model to build a new custom model to classify images into a few categories.</span></span>

<span data-ttu-id="98bf4-105">E se você pudesse reutilizar um modelo que já tenha sido pré-treinado para resolver um problema semelhante e treinar novamente todas ou algumas das camadas desse modelo para resolvê-lo?</span><span class="sxs-lookup"><span data-stu-id="98bf4-105">What if you could reuse a model that's already been pre trained to solve a similar problem and retrain either all or some of the layers of that model to make it solve your problem?</span></span> <span data-ttu-id="98bf4-106">Essa técnica de reutilizar parte de um modelo já treinado para construir um novo modelo é conhecida como [aprendizado de transferência](https://en.wikipedia.org/wiki/Transfer_learning).</span><span class="sxs-lookup"><span data-stu-id="98bf4-106">This technique of reusing part of an already trained model to build a new model is known as [transfer learning](https://en.wikipedia.org/wiki/Transfer_learning).</span></span>

<span data-ttu-id="98bf4-107">Treinar um modelo de [Classificação de Imagens](https://en.wikipedia.org/wiki/Outline_of_object_recognition) do zero requer a configuração de milhões de parâmetros, uma tonelada de dados de treinamento rotulados e uma grande quantidade de recursos de computação (centenas de horas de GPU).</span><span class="sxs-lookup"><span data-stu-id="98bf4-107">Training an [Image Classification](https://en.wikipedia.org/wiki/Outline_of_object_recognition) model from scratch requires setting millions of parameters, a ton of labeled training data and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="98bf4-108">Embora não seja tão eficaz quanto treinar um modelo personalizado do zero, o aprendizado de transferência permite que você ative esse processo trabalhando com milhares de imagens em comparação com milhões de imagens rotuladas e crie um modelo personalizado rapidamente (em uma hora em uma máquina sem GPU).</span><span class="sxs-lookup"><span data-stu-id="98bf4-108">While not as effective as training a custom model from scratch, transfer learning allows you to shortcut this process by working with thousands of images vs. millions of labeled images and build a customized model fairly quickly (within an hour on a machine without a GPU).</span></span>

<span data-ttu-id="98bf4-109">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="98bf4-109">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="98bf4-110">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="98bf4-110">Understand the problem</span></span>
> * <span data-ttu-id="98bf4-111">Reutilizar e ajustar o modelo pré-treinado</span><span class="sxs-lookup"><span data-stu-id="98bf4-111">Reuse and tune the pre-trained model</span></span>
> * <span data-ttu-id="98bf4-112">Classificar imagens</span><span class="sxs-lookup"><span data-stu-id="98bf4-112">Classify Images</span></span>

> [!NOTE]
> <span data-ttu-id="98bf4-113">Este tópico se refere ao ML.NET, que está atualmente na Versão Prévia, e o material pode estar sujeito a alterações.</span><span class="sxs-lookup"><span data-stu-id="98bf4-113">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="98bf4-114">Para obter mais informações, visite [a introdução ao ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="98bf4-114">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="98bf4-115">Este tutorial e uma amostra relacionada estão usando o **ML.NET versão 0.10** no momento.</span><span class="sxs-lookup"><span data-stu-id="98bf4-115">This tutorial and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="98bf4-116">Para obter mais informações, confira as notas sobre a versão no repositório do GitHub [dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="98bf4-116">For more information, see the release notes at the [dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes) GitHub repository.</span></span>

## <a name="image-classification-sample-overview"></a><span data-ttu-id="98bf4-117">Visão geral da amostra de classificação de imagens</span><span class="sxs-lookup"><span data-stu-id="98bf4-117">Image classification sample overview</span></span>

<span data-ttu-id="98bf4-118">O exemplo é um aplicativo de console que usa o ML.NET para criar um classificador de imagens reutilizando um modelo pré-treinado para classificar imagens com uma pequena quantidade de dados de treinamento.</span><span class="sxs-lookup"><span data-stu-id="98bf4-118">The sample is a console application that uses ML.NET to build an image classifier by reusing a pre-trained model to classify images with a small amount of training data.</span></span>

<span data-ttu-id="98bf4-119">Você pode encontrar o código-fonte para este tutorial no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF).</span><span class="sxs-lookup"><span data-stu-id="98bf4-119">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="98bf4-120">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="98bf4-120">Prerequisites</span></span>

* <span data-ttu-id="98bf4-121">[Visual Studio 2017 15.6 ou posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" instalada.</span><span class="sxs-lookup"><span data-stu-id="98bf4-121">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

* <span data-ttu-id="98bf4-122">Pacote Nuget Microsoft.ML 0.10.0</span><span class="sxs-lookup"><span data-stu-id="98bf4-122">Microsoft.ML 0.10.0 Nuget package</span></span>
* <span data-ttu-id="98bf4-123">Pacote Nuget Microsoft.ML.ImageAnalytics 0.10.0</span><span class="sxs-lookup"><span data-stu-id="98bf4-123">Microsoft.ML.ImageAnalytics 0.10.0 Nuget package</span></span>
* <span data-ttu-id="98bf4-124">Pacote Nuget Microsoft.ML.TensorFlow 0.10.0</span><span class="sxs-lookup"><span data-stu-id="98bf4-124">Microsoft.ML.TensorFlow 0.10.0 Nuget package</span></span>

* [<span data-ttu-id="98bf4-125">O arquivo .ZIP do diretório de recursos do tutorial</span><span class="sxs-lookup"><span data-stu-id="98bf4-125">The tutorial assets directory .ZIP file</span></span>](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip)

* [<span data-ttu-id="98bf4-126">O modelo de aprendizado de máquina InceptionV3</span><span class="sxs-lookup"><span data-stu-id="98bf4-126">The InceptionV3 machine learning model</span></span>](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="98bf4-127">Selecionar a tarefa de aprendizado de máquina apropriada</span><span class="sxs-lookup"><span data-stu-id="98bf4-127">Select the appropriate machine learning task</span></span>

<span data-ttu-id="98bf4-128">[Aprendizado profundo](https://en.wikipedia.org/wiki/Deep_learning) é um subconjunto do aprendizado de máquina, que está revolucionando áreas como Pesquisa Visual Computacional e Reconhecimento de Fala.</span><span class="sxs-lookup"><span data-stu-id="98bf4-128">[Deep learning](https://en.wikipedia.org/wiki/Deep_learning) is a subset of Machine Learning, which is revolutionizing areas like Computer Vision and Speech Recognition.</span></span>

<span data-ttu-id="98bf4-129">Os modelos de aprendizado profundo são treinados usando grandes conjuntos de [dados rotulados](https://en.wikipedia.org/wiki/Labeled_data) e [redes neurais](https://en.wikipedia.org/wiki/Artificial_neural_network) que contêm várias camadas de aprendizado.</span><span class="sxs-lookup"><span data-stu-id="98bf4-129">Deep learning models are trained by using large sets of [labeled data](https://en.wikipedia.org/wiki/Labeled_data) and [neural networks](https://en.wikipedia.org/wiki/Artificial_neural_network) that contain multiple learning layers.</span></span> <span data-ttu-id="98bf4-130">Aprendizado profundo:</span><span class="sxs-lookup"><span data-stu-id="98bf4-130">Deep learning:</span></span>

* <span data-ttu-id="98bf4-131">Funciona melhor em algumas tarefas como a Pesquisa Visual Computacional.</span><span class="sxs-lookup"><span data-stu-id="98bf4-131">Performs better on some tasks like Computer Vision.</span></span>

* <span data-ttu-id="98bf4-132">Funciona bem em enormes quantidades de dados.</span><span class="sxs-lookup"><span data-stu-id="98bf4-132">Performs well on huge data amounts.</span></span>

<span data-ttu-id="98bf4-133">A classificação de imagens é uma tarefa comum de aprendizado de máquina que nos permite classificar automaticamente as imagens em várias categorias, como:</span><span class="sxs-lookup"><span data-stu-id="98bf4-133">Image Classification is a common Machine Learning task that allows us to automatically classify images into multiple categories such as:</span></span>

* <span data-ttu-id="98bf4-134">Detectar uma face humana em uma imagem ou não.</span><span class="sxs-lookup"><span data-stu-id="98bf4-134">Detecting a human face in an image or not.</span></span>
* <span data-ttu-id="98bf4-135">Detectar gatos e cachorros.</span><span class="sxs-lookup"><span data-stu-id="98bf4-135">Detecting Cats vs. dogs.</span></span>

 <span data-ttu-id="98bf4-136">Ou, como nas imagens a seguir, que determinar se uma imagem é um alimento, brinquedo ou dispositivo:</span><span class="sxs-lookup"><span data-stu-id="98bf4-136">Or as in the following images determining if an image is a(n)  food, toy, or appliance:</span></span>

<span data-ttu-id="98bf4-137">![imagem de pizza](./media/image-classification/220px-Pepperoni_pizza.jpg)
![imagem de ursinho de pelúcia](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![imagem de torradeira](./media/image-classification/193px-Broodrooster.jpg)</span><span class="sxs-lookup"><span data-stu-id="98bf4-137">![pizza image](./media/image-classification/220px-Pepperoni_pizza.jpg)
![teddy bear image](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![toaster image](./media/image-classification/193px-Broodrooster.jpg)</span></span>

>[!Note]
> <span data-ttu-id="98bf4-138">As imagens anteriores pertencem ao Wikimedia Commons e são atribuídas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="98bf4-138">The preceding images belong to Wikimedia Commons and are attributed as follows:</span></span>
>
> * <span data-ttu-id="98bf4-139">"220px-Pepperoni_pizza.jpg" Public Domain, https://commons.wikimedia.org/w/index.php?curid=79505,</span><span class="sxs-lookup"><span data-stu-id="98bf4-139">"220px-Pepperoni_pizza.jpg" Public Domain, https://commons.wikimedia.org/w/index.php?curid=79505,</span></span>
> * <span data-ttu-id="98bf4-140">"119px-Nalle_-_a_small_brown_teddy_bear.jpg" By [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) - Self-photographed, CC BY-SA 2.0, https://commons.wikimedia.org/w/index.php?curid=48166.</span><span class="sxs-lookup"><span data-stu-id="98bf4-140">"119px-Nalle_-_a_small_brown_teddy_bear.jpg" By [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) - Self-photographed, CC BY-SA 2.0, https://commons.wikimedia.org/w/index.php?curid=48166.</span></span>
> * <span data-ttu-id="98bf4-141">"193px-Broodrooster.jpg" By [M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) - Own work, CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=27403</span><span class="sxs-lookup"><span data-stu-id="98bf4-141">"193px-Broodrooster.jpg" By [M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) - Own work, CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=27403</span></span>

<span data-ttu-id="98bf4-142">O aprendizado de transferência inclui algumas estratégias, como *readaptar todas as camadas* e a *penúltima camada*.</span><span class="sxs-lookup"><span data-stu-id="98bf4-142">Transfer learning includes a few strategies, such as *retrain all layers* and *penultimate layer*.</span></span> <span data-ttu-id="98bf4-143">Esse tutorial explicará e mostrará como usar a *estratégia de penúltima camada*.</span><span class="sxs-lookup"><span data-stu-id="98bf4-143">This tutorial will explain and show how to use the *penultimate layer strategy*.</span></span> <span data-ttu-id="98bf4-144">A *estratégia de penúltima camada* reutiliza um modelo que já foi pré-treinado para resolver um problema específico.</span><span class="sxs-lookup"><span data-stu-id="98bf4-144">The *penultimate layer strategy* reuses a model that's already been pre-trained to solve a specific problem.</span></span> <span data-ttu-id="98bf4-145">A estratégia, em seguida, treina novamente a camada final desse modelo para resolver um novo problema.</span><span class="sxs-lookup"><span data-stu-id="98bf4-145">The strategy then retrains the final layer of that model to make it solve a new problem.</span></span> <span data-ttu-id="98bf4-146">Reutilizar o modelo pré-treinado como parte de seu novo modelo economizará tempo e recursos significativos.</span><span class="sxs-lookup"><span data-stu-id="98bf4-146">Reusing the pre-trained model as part of your new model will save significant time and resources.</span></span>

<span data-ttu-id="98bf4-147">Seu modelo de classificação de imagens reutiliza o modelo [Concepção](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), um popular modelo de reconhecimento de imagens treinado no conjunto de dados `ImageNet` em que o modelo TensorFlow tenta classificar imagens inteiras em mil classes, como “guarda-chuva”, “camiseta” e “lava-louças”.</span><span class="sxs-lookup"><span data-stu-id="98bf4-147">Your image classification model reuses the [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), a popular image recognition model trained on the `ImageNet` dataset where the TensorFlow model tries to classify entire images into a thousand classes, like “Umbrella”, “Jersey”, and “Dishwasher”.</span></span>

<span data-ttu-id="98bf4-148">O `Inception v3 model` pode ser classificado como uma [rede neural convolucional profunda](https://en.wikipedia.org/wiki/Convolutional_neural_network) e pode alcançar um desempenho razoável em tarefas de reconhecimento visual, combinando ou excedendo o desempenho humano em alguns domínios.</span><span class="sxs-lookup"><span data-stu-id="98bf4-148">The `Inception v3 model` can be classified as a [deep convolutional neural network](https://en.wikipedia.org/wiki/Convolutional_neural_network) and can achieve reasonable performance on hard visual recognition tasks, matching or exceeding human performance in some domains.</span></span> <span data-ttu-id="98bf4-149">O modelo/algoritmo foi desenvolvido por múltiplos pesquisadores e baseado no artigo original: ["Reformulação da arquitetura de concepção para pesquisa visual computacional" por Szegedy, et. Al.](https://arxiv.org/abs/1512.00567)</span><span class="sxs-lookup"><span data-stu-id="98bf4-149">The model/algorithm was developed by multiple researchers and based on the original paper: ["Rethinking the Inception Architecture for Computer Vision” by Szegedy, et. al.](https://arxiv.org/abs/1512.00567)</span></span>

<span data-ttu-id="98bf4-150">Como o `Inception model` já foi pré-treinado em milhares de imagens diferentes, ele contém os [recursos de imagem](https://en.wikipedia.org/wiki/Feature_(computer_vision)) necessários para a identificação da imagem.</span><span class="sxs-lookup"><span data-stu-id="98bf4-150">Because the `Inception model` has already been pre trained on thousands of different images, it contains the [image features](https://en.wikipedia.org/wiki/Feature_(computer_vision)) needed for image identification.</span></span> <span data-ttu-id="98bf4-151">As camadas de recurso de imagens inferiores reconhecem recursos simples (como bordas), e as camadas superiores reconhecem recursos mais complexos (como formas).</span><span class="sxs-lookup"><span data-stu-id="98bf4-151">The lower image feature layers recognize simple features (such as edges) and the higher layers recognize more complex features (such as shapes).</span></span> <span data-ttu-id="98bf4-152">A camada final é treinada contra um conjunto muito menor de dados porque você está começando com um modelo pré-treinado que já entende como classificar imagens.</span><span class="sxs-lookup"><span data-stu-id="98bf4-152">The final layer is trained against a much smaller set of data because you're starting with a pre trained model that already understands how to classify images.</span></span> <span data-ttu-id="98bf4-153">Como seu modelo permite classificar mais de duas categorias, este é um exemplo de um [classificador multiclasse](../resources/tasks.md#multiclass-classification).</span><span class="sxs-lookup"><span data-stu-id="98bf4-153">As your model allows you to classify more than two categories, this is an example of a [multi-class classifier](../resources/tasks.md#multiclass-classification).</span></span> 

<span data-ttu-id="98bf4-154">`TensorFlow` é um popular kit de ferramentas de aprendizado profundo e aprendizado de máquina que permite o treinamento de redes neurais profundas (e cálculos numéricos gerais) e é implementado como um `transformer` no ML.NET.</span><span class="sxs-lookup"><span data-stu-id="98bf4-154">`TensorFlow` is a popular deep learning and machine learning toolkit that enables training deep neural networks (and general numeric computations), and is implemented as a `transformer` in ML.NET.</span></span> <span data-ttu-id="98bf4-155">Para este tutorial, é usado para reutilizar o `Inception model`.</span><span class="sxs-lookup"><span data-stu-id="98bf4-155">For this tutorial, it's used to reuse the `Inception model`.</span></span>

<span data-ttu-id="98bf4-156">Conforme mostrado no diagrama a seguir, você adiciona uma referência aos pacotes ML.NET NuGet em seus aplicativos .NET Core ou .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="98bf4-156">As shown in the following diagram, you add a reference to the ML.NET NuGet packages in your .NET Core or .NET Framework applications.</span></span> <span data-ttu-id="98bf4-157">Nos bastidores, o ML.NET inclui e faz referência à biblioteca `TensorFlow` nativa que permite escrever código que carrega um arquivo de modelo `TensorFlow` existente e treinado para pontuação.</span><span class="sxs-lookup"><span data-stu-id="98bf4-157">Under the covers, ML.NET includes and references the native `TensorFlow` library that allows you to write code that loads an existing trained `TensorFlow` model file for scoring.</span></span>  

![Diagrama de arco da transformação do TensorFlow do ML.NET](./media/image-classification/tensorflow-mlnet.png)

<span data-ttu-id="98bf4-159">O `Inception model` é treinado para classificar imagens em mil categorias, mas é necessário classificar imagens em um conjunto de categorias menor e apenas nessas categorias.</span><span class="sxs-lookup"><span data-stu-id="98bf4-159">The `Inception model` is trained to classify images into a thousand categories, but you need to classify images in a smaller category set, and only those categories.</span></span> <span data-ttu-id="98bf4-160">Digite a parte `transfer` de `transfer learning`.</span><span class="sxs-lookup"><span data-stu-id="98bf4-160">Enter the `transfer` part of `transfer learning`.</span></span> <span data-ttu-id="98bf4-161">Você pode transferir a capacidade de `Inception model` de reconhecer e classificar imagens para as novas categorias limitadas do seu classificador de imagens personalizadas.</span><span class="sxs-lookup"><span data-stu-id="98bf4-161">You can transfer the `Inception model`'s ability to recognize and classify images to the new limited categories of your custom image classifier.</span></span>  

 <span data-ttu-id="98bf4-162">Você vai treinar novamente a camada final desse modelo usando um conjunto de três categorias:</span><span class="sxs-lookup"><span data-stu-id="98bf4-162">You're going to retrain the final layer of that model using a set of three categories:</span></span>

* <span data-ttu-id="98bf4-163">Alimentação</span><span class="sxs-lookup"><span data-stu-id="98bf4-163">Food</span></span>
* <span data-ttu-id="98bf4-164">Brinquedos</span><span class="sxs-lookup"><span data-stu-id="98bf4-164">Toy</span></span>
* <span data-ttu-id="98bf4-165">Dispositivos</span><span class="sxs-lookup"><span data-stu-id="98bf4-165">Appliance</span></span>

<span data-ttu-id="98bf4-166">Sua camada usa um [algoritmo de regressão logística multinomial](https://en.wikipedia.org/wiki/Multinomial_logistic_regression) para encontrar a categoria correta o mais rápido possível.</span><span class="sxs-lookup"><span data-stu-id="98bf4-166">Your layer uses a [multinomial logistic regression algorithm](https://en.wikipedia.org/wiki/Multinomial_logistic_regression) to find the correct category as quickly as possible.</span></span> <span data-ttu-id="98bf4-167">Esse algoritmo classifica usando probabilidades para determinar a resposta, dando um valor para a categoria correta e um valor zero para os outros.</span><span class="sxs-lookup"><span data-stu-id="98bf4-167">This algorithm classifies using probabilities to determine the answer, giving a one value to the correct category and a zero value to the others.</span></span>  

### <a name="dataset"></a><span data-ttu-id="98bf4-168">DataSet</span><span class="sxs-lookup"><span data-stu-id="98bf4-168">DataSet</span></span>

<span data-ttu-id="98bf4-169">Há duas fontes de dados: o arquivo `.tsv` e os arquivos de imagem.</span><span class="sxs-lookup"><span data-stu-id="98bf4-169">There are two data sources: the `.tsv` file, and the image files.</span></span>  <span data-ttu-id="98bf4-170">O arquivo `tags.tsv` contém duas colunas: a primeira é definida como `ImagePath` e a segunda é a `Label` correspondente à imagem.</span><span class="sxs-lookup"><span data-stu-id="98bf4-170">The `tags.tsv` file contains two columns: the first one is defined as `ImagePath` and the second one is the `Label` corresponding to the image.</span></span> <span data-ttu-id="98bf4-171">O arquivo de exemplo a seguir não possui uma linha de cabeçalho e tem a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="98bf4-171">The following example file doesn't have a header row, and looks like this:</span></span>

<!-- markdownlint-disable MD010 -->
```tsv
broccoli.jpg    food
pizza.jpg   food
pizza2.jpg  food
teddy2.jpg  toy
teddy3.jpg  toy
teddy4.jpg  toy
toaster.jpg appliance
toaster2.png    appliance
```
<!-- markdownlint-enable MD010 -->

<span data-ttu-id="98bf4-172">As imagens de treinamento e teste estão localizadas nas pastas de recursos que você baixará em um arquivo zip.</span><span class="sxs-lookup"><span data-stu-id="98bf4-172">The training and testing images are located in the assets folders that you'll download in a zip file.</span></span> <span data-ttu-id="98bf4-173">Essas imagens pertencem ao Wikimedia Commons.</span><span class="sxs-lookup"><span data-stu-id="98bf4-173">These images belong to Wikimedia Commons.</span></span>
> <span data-ttu-id="98bf4-174">*[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), o repositório de mídia gratuito.*</span><span class="sxs-lookup"><span data-stu-id="98bf4-174">*[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), the free media repository.*</span></span> <span data-ttu-id="98bf4-175">Recuperado em 10:48, 17 de outubro de 2018 de:</span><span class="sxs-lookup"><span data-stu-id="98bf4-175">Retrieved 10:48, October 17, 2018 from:</span></span>  
> https://commons.wikimedia.org/wiki/Pizza  
> https://commons.wikimedia.org/wiki/Toaster  
> https://commons.wikimedia.org/wiki/Teddy_bear  

## <a name="create-a-console-application"></a><span data-ttu-id="98bf4-176">Criar um aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="98bf4-176">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="98bf4-177">Criar um projeto</span><span class="sxs-lookup"><span data-stu-id="98bf4-177">Create a project</span></span>

1. <span data-ttu-id="98bf4-178">Abra o Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="98bf4-178">Open Visual Studio 2017.</span></span> <span data-ttu-id="98bf4-179">Selecione **Arquivo** > **Novo** > **Projeto** na barra de menus.</span><span class="sxs-lookup"><span data-stu-id="98bf4-179">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="98bf4-180">Na caixa de diálogo **Novo Projeto**, selecione o nó **Visual C#** seguido pelo nó **.NET Core**.</span><span class="sxs-lookup"><span data-stu-id="98bf4-180">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="98bf4-181">Em seguida, selecione o modelo de projeto **Aplicativo de console (.NET Core)**.</span><span class="sxs-lookup"><span data-stu-id="98bf4-181">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="98bf4-182">Na caixa de texto**Nome**, digite "TransferLearningTF" e, em seguida, selecione o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="98bf4-182">In the **Name** text box, type "TransferLearningTF" and then select the **OK** button.</span></span>

2. <span data-ttu-id="98bf4-183">Instalar o **Pacote NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="98bf4-183">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="98bf4-184">No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="98bf4-184">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="98bf4-185">Escolha "nuget.org" como a fonte do pacote, selecione a guia Browse, procure por **Microsoft.ML**.</span><span class="sxs-lookup"><span data-stu-id="98bf4-185">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**.</span></span> <span data-ttu-id="98bf4-186">Clique na lista suspensa **Versão**, selecione o pacote **0.10.0** na lista e selecione o botão **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="98bf4-186">Click on the **Version** drop-down, select the **0.10.0** package in the list, and select the **Install** button.</span></span> <span data-ttu-id="98bf4-187">Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados.</span><span class="sxs-lookup"><span data-stu-id="98bf4-187">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="98bf4-188">Repita essas etapas para **Microsoft.ML.ImageAnalytics v0.10.0** e **Microsoft.ML.TensorFlow v0.10.0**.</span><span class="sxs-lookup"><span data-stu-id="98bf4-188">Repeat these steps for **Microsoft.ML.ImageAnalytics v0.10.0** and **Microsoft.ML.TensorFlow v0.10.0**.</span></span>

  > [!NOTE]
  > <span data-ttu-id="98bf4-189">Esse tutorial usa **Microsoft.ML v0.10.0**, **Microsoft.ML.ImageAnalytics v0.10.0** e **Microsoft.ML.TensorFlow v0.10.0**.</span><span class="sxs-lookup"><span data-stu-id="98bf4-189">This tutorial uses **Microsoft.ML v0.10.0**, **Microsoft.ML.ImageAnalytics v0.10.0**, and **Microsoft.ML.TensorFlow v0.10.0**.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="98bf4-190">Preparar seus dados</span><span class="sxs-lookup"><span data-stu-id="98bf4-190">Prepare your data</span></span>

1. <span data-ttu-id="98bf4-191">Baixe o [arquivo zip do diretório de materiais do projeto](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip) e descompacte.</span><span class="sxs-lookup"><span data-stu-id="98bf4-191">Download [The project assets directory zip file](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip), and unzip.</span></span>

2. <span data-ttu-id="98bf4-192">Copie o diretório`assets` no diretório do projeto *TransferLearningTF*.</span><span class="sxs-lookup"><span data-stu-id="98bf4-192">Copy the `assets` directory into your *TransferLearningTF* project directory.</span></span> <span data-ttu-id="98bf4-193">Este diretório e seus subdiretórios contêm os arquivos de dados e de suporte (exceto o modelo Concepção, que você irá baixar e adicionar na próxima etapa) necessários para este tutorial.</span><span class="sxs-lookup"><span data-stu-id="98bf4-193">This directory and its subdirectories contain the data and support files (except for the Inception model, which you'll download and add in the next step) needed for this tutorial.</span></span>

3. <span data-ttu-id="98bf4-194">Baixe o [modelo Concepção](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) e descompacte-o.</span><span class="sxs-lookup"><span data-stu-id="98bf4-194">Download the [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), and unzip.</span></span>

4. <span data-ttu-id="98bf4-195">Copie o conteúdo do diretório `inception5h` apenas descompactado em seu diretório de projeto *TransferLearningTF*`assets\inputs-train\inception`.</span><span class="sxs-lookup"><span data-stu-id="98bf4-195">Copy the contents of the `inception5h` directory just unzipped into your *TransferLearningTF* project `assets\inputs-train\inception` directory.</span></span> <span data-ttu-id="98bf4-196">Este diretório contém o modelo e os arquivos de suporte adicionais necessários para este tutorial, conforme mostrado na imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="98bf4-196">This directory contains the model and additional support files needed for this tutorial, as shown in the following image:</span></span>

   ![Conteúdo do diretório de concepção](./media/image-classification/inception-files.png)

5. <span data-ttu-id="98bf4-198">No Gerenciador de Soluções, clique com o botão direito do mouse em cada um dos arquivos no diretório e nos subdiretórios do ativo e selecione**Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="98bf4-198">In Solution Explorer, right-click each of the files in the asset directory and subdirectories and select **Properties**.</span></span> <span data-ttu-id="98bf4-199">Em **Avançado**, altere o valor de **Copiar para Diretório de Saída** para **Copiar se for mais novo**.</span><span class="sxs-lookup"><span data-stu-id="98bf4-199">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="98bf4-200">Criar classes e definir demarcadores</span><span class="sxs-lookup"><span data-stu-id="98bf4-200">Create classes and define paths</span></span>

<span data-ttu-id="98bf4-201">Adicione as seguintes instruções `using` adicionais ao início do arquivo *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="98bf4-201">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddUsings)]

<span data-ttu-id="98bf4-202">Crie campos globais para manter os caminhos para os vários ativos e variáveis globais para `LabelTokey`, `ImageReal` e `PredictedLabelValue`:</span><span class="sxs-lookup"><span data-stu-id="98bf4-202">Create global fields to hold the paths to the various assets, and global variables for the `LabelTokey`,`ImageReal`, and  `PredictedLabelValue`:</span></span>

* <span data-ttu-id="98bf4-203">`_assetsPath` tem o demarcador para os ativos.</span><span class="sxs-lookup"><span data-stu-id="98bf4-203">`_assetsPath` has the path to the assets.</span></span>
* <span data-ttu-id="98bf4-204">`_trainTagsTsv` tem o demarcador para o arquivo tsv de tags de dados de imagem de treinamento.</span><span class="sxs-lookup"><span data-stu-id="98bf4-204">`_trainTagsTsv` has the path to the training image data tags tsv file.</span></span>
* <span data-ttu-id="98bf4-205">`_predictTagsTsv` tem o demarcador para o arquivo tsv de tags de dados de imagem de previsão.</span><span class="sxs-lookup"><span data-stu-id="98bf4-205">`_predictTagsTsv` has the path to the prediction image data tags tsv file.</span></span>
* <span data-ttu-id="98bf4-206">`_trainImagesFolder` tem o demarcador para as imagens usadas para treinar o modelo.</span><span class="sxs-lookup"><span data-stu-id="98bf4-206">`_trainImagesFolder` has the path to the images used to train the model.</span></span>
* <span data-ttu-id="98bf4-207">`_predictImagesFolder` tem o demarcador para as imagens a serem classificadas pelo modelo treinado.</span><span class="sxs-lookup"><span data-stu-id="98bf4-207">`_predictImagesFolder` has the path to the images to be classified by the trained model.</span></span>
* <span data-ttu-id="98bf4-208">`_inceptionPb`tem o demarcador para o modelo Concepção pré-treinado para ser reutilizado para treinar seu modelo.</span><span class="sxs-lookup"><span data-stu-id="98bf4-208">`_inceptionPb` has the path to the pre-trained Inception model to be reused to retrain your model.</span></span>
* <span data-ttu-id="98bf4-209">`_inputImageClassifierZip` tem o demarcador de onde o modelo treinado é carregado.</span><span class="sxs-lookup"><span data-stu-id="98bf4-209">`_inputImageClassifierZip` has the path where the trained model is loaded from.</span></span>
* <span data-ttu-id="98bf4-210">`_outputImageClassifierZip` tem o demarcador em que o modelo treinado é salvo.</span><span class="sxs-lookup"><span data-stu-id="98bf4-210">`_outputImageClassifierZip` has the path where the trained model is saved.</span></span>
* <span data-ttu-id="98bf4-211">`LabelTokey` é o `Label` valor mapeado para uma chave.</span><span class="sxs-lookup"><span data-stu-id="98bf4-211">`LabelTokey` is the `Label` value mapped to a key.</span></span>
* <span data-ttu-id="98bf4-212">`ImageReal` é a coluna que contém o valor da imagem prevista.</span><span class="sxs-lookup"><span data-stu-id="98bf4-212">`ImageReal`  is the column containing the predicted image value.</span></span>
* <span data-ttu-id="98bf4-213">`PredictedLabelValue` é a coluna que contém o valor do rótulo previsto.</span><span class="sxs-lookup"><span data-stu-id="98bf4-213">`PredictedLabelValue` is the column containing the predicted label value.</span></span>

<span data-ttu-id="98bf4-214">Adicione o seguinte código à linha logo acima do método `Main` para especificar estes caminhos e as outras variáveis:</span><span class="sxs-lookup"><span data-stu-id="98bf4-214">Add the following code to the line right above the `Main` method to specify those paths and the other variables:</span></span>

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareGlobalVariables)]

<span data-ttu-id="98bf4-215">Crie algumas classes para os dados de entrada e as previsões.</span><span class="sxs-lookup"><span data-stu-id="98bf4-215">Create some classes for your input data, and predictions.</span></span> <span data-ttu-id="98bf4-216">Adicione uma nova classe ao seu projeto:</span><span class="sxs-lookup"><span data-stu-id="98bf4-216">Add a new class to your project:</span></span>

1. <span data-ttu-id="98bf4-217">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="98bf4-217">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="98bf4-218">Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *ImageData.cs*.</span><span class="sxs-lookup"><span data-stu-id="98bf4-218">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *ImageData.cs*.</span></span> <span data-ttu-id="98bf4-219">Em seguida, selecione o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="98bf4-219">Then, select the **Add** button.</span></span>

    <span data-ttu-id="98bf4-220">O arquivo *ImageData.cs* é aberto no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="98bf4-220">The *ImageData.cs* file opens in the code editor.</span></span> <span data-ttu-id="98bf4-221">Adicione a seguinte instrução `using` à parte superior do *ImageData.cs*:</span><span class="sxs-lookup"><span data-stu-id="98bf4-221">Add the following `using` statement to the top of *ImageData.cs*:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/ImageData.cs#AddUsings)]

<span data-ttu-id="98bf4-222">Remova a definição de classe existente e adicione o seguinte código para a classe `ImageData` do arquivo *ImageData.cs*:</span><span class="sxs-lookup"><span data-stu-id="98bf4-222">Remove the existing class definition and add the following code for the `ImageData` class to the *ImageData.cs* file:</span></span>

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/TransferLearningTF/ImageData.cs#DeclareTypes)]

<span data-ttu-id="98bf4-223">`ImageData` é a classe de conjunto de dados de entrada e tem os seguintes campos <xref:System.String>:</span><span class="sxs-lookup"><span data-stu-id="98bf4-223">`ImageData` is the input image data class and has the following <xref:System.String> fields:</span></span>

* <span data-ttu-id="98bf4-224">`ImagePath` contém o nome do arquivo de imagem.</span><span class="sxs-lookup"><span data-stu-id="98bf4-224">`ImagePath` contains the image file name.</span></span>
* <span data-ttu-id="98bf4-225">`Label` contém um valor para o rótulo da imagem.</span><span class="sxs-lookup"><span data-stu-id="98bf4-225">`Label` contains a value for the image label.</span></span>

<span data-ttu-id="98bf4-226">Adicione uma nova classe ao seu projeto para `ImagePrediction`:</span><span class="sxs-lookup"><span data-stu-id="98bf4-226">Add a new class to your project for `ImagePrediction`:</span></span>

1. <span data-ttu-id="98bf4-227">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="98bf4-227">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="98bf4-228">Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *ImagePrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="98bf4-228">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *ImagePrediction.cs*.</span></span> <span data-ttu-id="98bf4-229">Em seguida, selecione o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="98bf4-229">Then, select the **Add** button.</span></span>

    <span data-ttu-id="98bf4-230">O arquivo *ImagePrediction.cs* é aberto no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="98bf4-230">The *ImagePrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="98bf4-231">Remova as instruções `System.Collections.Generic` e `System.Text` `using` na parte superior do *ImagePrediction.cs*:</span><span class="sxs-lookup"><span data-stu-id="98bf4-231">Remove both the `System.Collections.Generic` and the `System.Text` `using` statements at the top of *ImagePrediction.cs*:</span></span>

<span data-ttu-id="98bf4-232">Remova a definição de classe existente e adicione o seguinte código, que tem a classe `ImagePrediction`, ao arquivo *ImagePrediction.cs*:</span><span class="sxs-lookup"><span data-stu-id="98bf4-232">Remove the existing class definition and add the following code, which has the `ImagePrediction` class, to the *ImagePrediction.cs* file:</span></span>

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/ImagePrediction.cs#DeclareTypes)]

<span data-ttu-id="98bf4-233">`ImagePrediction` é a classe de previsão de imagem e possui os seguintes campos:</span><span class="sxs-lookup"><span data-stu-id="98bf4-233">`ImagePrediction` is the image prediction class and has the following fields:</span></span>

* <span data-ttu-id="98bf4-234">`Score` contém a porcentagem de confiança para uma determinada classificação de imagem.</span><span class="sxs-lookup"><span data-stu-id="98bf4-234">`Score` contains the confidence percentage for a given image classification.</span></span>
* <span data-ttu-id="98bf4-235">`PredictedLabelValue` contém um valor para o rótulo de classificação de imagem previsto.</span><span class="sxs-lookup"><span data-stu-id="98bf4-235">`PredictedLabelValue` contains a value for the predicted image classification label.</span></span>

<span data-ttu-id="98bf4-236">`ImagePrediction` é a classe usada para previsão depois que o modelo foi treinado.</span><span class="sxs-lookup"><span data-stu-id="98bf4-236">`ImagePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="98bf4-237">Tem um `string` (`ImagePath`) para o demarcador da imagem.</span><span class="sxs-lookup"><span data-stu-id="98bf4-237">It has a `string` (`ImagePath`) for the image path.</span></span> <span data-ttu-id="98bf4-238">O `Label` é usado para reutilizar e treinar novamente o modelo.</span><span class="sxs-lookup"><span data-stu-id="98bf4-238">The `Label` is used to reuse and retrain the model.</span></span> <span data-ttu-id="98bf4-239">O `PredictedLabelValue` é usado durante a previsão e avaliação.</span><span class="sxs-lookup"><span data-stu-id="98bf4-239">The `PredictedLabelValue` is used during prediction and evaluation.</span></span> <span data-ttu-id="98bf4-240">Para avaliação, uma entrada com dados de treinamento, os valores previstos e o modelo são usados.</span><span class="sxs-lookup"><span data-stu-id="98bf4-240">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="98bf4-241">A [classe MLContext](xref:Microsoft.ML.MLContext) é um ponto de partida para todas as operações do ML.NET e a inicialização do `mlContext` cria um ambiente do ML.NET que pode ser compartilhado entre os objetos de fluxo de trabalho da criação de modelo.</span><span class="sxs-lookup"><span data-stu-id="98bf4-241">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="98bf4-242">Ele é semelhante, conceitualmente, a `DBContext` no Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="98bf4-242">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="98bf4-243">Inicializar variáveis em Main</span><span class="sxs-lookup"><span data-stu-id="98bf4-243">Initialize variables in Main</span></span>

<span data-ttu-id="98bf4-244">Inicialize a variável `mlContext` com uma nova instância de `MLContext`.</span><span class="sxs-lookup"><span data-stu-id="98bf4-244">Initialize the `mlContext` variable with a new instance of `MLContext`.</span></span>  <span data-ttu-id="98bf4-245">Substitua a linha `Console.WriteLine("Hello World!")` pelo seguinte código no método `Main`:</span><span class="sxs-lookup"><span data-stu-id="98bf4-245">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CreateMLContext)]

### <a name="create-a-struct-for-default-parameters"></a><span data-ttu-id="98bf4-246">Crie um struct para os parâmetros padrão</span><span class="sxs-lookup"><span data-stu-id="98bf4-246">Create a struct for default parameters</span></span>

<span data-ttu-id="98bf4-247">O modelo Concepção possui vários parâmetros padrão que você precisa verificar.</span><span class="sxs-lookup"><span data-stu-id="98bf4-247">The Inception model has several default parameters you need to pass in.</span></span> <span data-ttu-id="98bf4-248">Crie um struct para mapear os valores de parâmetros padrão para nomes amigáveis com o seguinte código, logo após o método `Main()`:</span><span class="sxs-lookup"><span data-stu-id="98bf4-248">Create a struct to map the default parameter values to friendly names with the following code, just after the `Main()` method:</span></span>

[!code-csharp[InceptionSettings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#InceptionSettings)]

### <a name="create-a-display-utility-method"></a><span data-ttu-id="98bf4-249">Criar um método de utilitário de exibição</span><span class="sxs-lookup"><span data-stu-id="98bf4-249">Create a display utility method</span></span>

<span data-ttu-id="98bf4-250">Emparelhe e exiba os dados da imagem e as previsões relacionadas mais de uma vez, e você não deseja duplicar o código.</span><span class="sxs-lookup"><span data-stu-id="98bf4-250">Pair and display the image data and the related predictions more than once, and you don't want to duplicate code.</span></span> <span data-ttu-id="98bf4-251">Crie um método de utilitário de exibição para manipular o pareamento e exibir a imagem e os resultados de previsão.</span><span class="sxs-lookup"><span data-stu-id="98bf4-251">Create a display utility method to handle pairing and displaying the image and prediction results.</span></span>

<span data-ttu-id="98bf4-252">O método `PairAndDisplayResults()` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="98bf4-252">The `PairAndDisplayResults()` method executes the following tasks:</span></span>

* <span data-ttu-id="98bf4-253">Combina dados e previsões para relatórios.</span><span class="sxs-lookup"><span data-stu-id="98bf4-253">Combines data and predictions for reporting.</span></span>
* <span data-ttu-id="98bf4-254">Exibe os resultados previstos.</span><span class="sxs-lookup"><span data-stu-id="98bf4-254">Displays the predicted results.</span></span>

<span data-ttu-id="98bf4-255">Crie o método `PairAndDisplayResults()`, logo após o struct `InceptionSettings`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="98bf4-255">Create the `PairAndDisplayResults()` method, just after the `InceptionSettings` struct, using the following code:</span></span>

```csharp
private static void PairAndDisplayResults(IEnumerable<ImageNetData> imageData, IEnumerable<ImageNetPrediction> imagePredictionData)
{

}
```

<span data-ttu-id="98bf4-256">Antes de exibir os resultados previstos, combine `imageData` e `imagePrediction` juntos para ver o `Image Path` original com a categoria prevista.</span><span class="sxs-lookup"><span data-stu-id="98bf4-256">Before displaying the predicted results, combine the `imageData` and `imagePrediction` together to see the original `Image Path` with its predicted category.</span></span> <span data-ttu-id="98bf4-257">O código a seguir usa o método <xref:System.Linq.Enumerable.Zip%2A?displayProperty=nameWithType> para que isso aconteça, então adicione-o como a primeira linha do método `PairAndDisplayResults()`:</span><span class="sxs-lookup"><span data-stu-id="98bf4-257">The following code uses the <xref:System.Linq.Enumerable.Zip%2A?displayProperty=nameWithType> method to make that happen, so add it as the first line of the `PairAndDisplayResults()` method:</span></span>

[!code-csharp[BuildImagePredictionPairs](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#BuildImagePredictionPairs)]

<span data-ttu-id="98bf4-258">Agora que você combinou `imageData` e `imageData` em uma classe, você pode exibir os resultados usando o método <xref:System.Console.WriteLine?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="98bf4-258">Now that you've combined the `imageData` and `imageData` into a class, you can display the results using the <xref:System.Console.WriteLine?displayProperty=nameWithType> method:</span></span>

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPredictions)]

<span data-ttu-id="98bf4-259">Você chamará o método `PairAndDisplayResults()` nos próximos dois métodos.</span><span class="sxs-lookup"><span data-stu-id="98bf4-259">You'll call the `PairAndDisplayResults()` method in the next two methods.</span></span>

### <a name="create-a-tsv-file-utility-method"></a><span data-ttu-id="98bf4-260">Criar um método de utilitário de arquivo .tsv</span><span class="sxs-lookup"><span data-stu-id="98bf4-260">Create a .tsv file utility method</span></span>

<span data-ttu-id="98bf4-261">O método `ReadFromTsv()` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="98bf4-261">The `ReadFromTsv()` method executes the following tasks:</span></span>

* <span data-ttu-id="98bf4-262">Lê o arquivo de dados de imagem `tags.tsv`.</span><span class="sxs-lookup"><span data-stu-id="98bf4-262">Reads the image data `tags.tsv` file.</span></span>
* <span data-ttu-id="98bf4-263">Adiciona o demarcador do arquivo ao nome do arquivo de imagem.</span><span class="sxs-lookup"><span data-stu-id="98bf4-263">Adds the file path to the image file name.</span></span>
* <span data-ttu-id="98bf4-264">Carrega os dados do arquivo em um objeto IEnumerable`ImageData`.</span><span class="sxs-lookup"><span data-stu-id="98bf4-264">Loads the file data into an IEnumerable`ImageData` object.</span></span>

<span data-ttu-id="98bf4-265">Crie o método `ReadFromTsv()`, logo após o método `PairAndDisplayResults()`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="98bf4-265">Create the `ReadFromTsv()` method, just after the `PairAndDisplayResults()` method, using the following code:</span></span>

```csharp
public static IEnumerable<ImageData> ReadFromTsv(string file, string folder)
{

}
```

<span data-ttu-id="98bf4-266">O código a seguir analisa o arquivo `tags.tsv` para adicionar o demarcador do arquivo ao nome do arquivo de imagem para a propriedade `ImagePath` e o carregá-lo e o `Label` em um objeto `ImageData`.</span><span class="sxs-lookup"><span data-stu-id="98bf4-266">The following code parses through the `tags.tsv` file to add the file path to the image file name for the `ImagePath` property and load it and the `Label` into an `ImageData` object.</span></span> <span data-ttu-id="98bf4-267">Adicione-o como a primeira linha do método `ReadFromTsv()`.</span><span class="sxs-lookup"><span data-stu-id="98bf4-267">Add it as the first line of the `ReadFromTsv()` method.</span></span>  <span data-ttu-id="98bf4-268">Você precisa do demarcador completo do arquivo para exibir os resultados da previsão.</span><span class="sxs-lookup"><span data-stu-id="98bf4-268">You need the fully qualified file path to display the prediction results.</span></span>

[!code-csharp[ReadFromTsv](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReadFromTsv)]
<span data-ttu-id="98bf4-269">Há três conceitos principais no ML.NET: [Dados](../basic-concepts-model-training-in-mldotnet.md#data), [Transformadores](../basic-concepts-model-training-in-mldotnet.md#transformer) e [Avaliadores](../basic-concepts-model-training-in-mldotnet.md#estimator).</span><span class="sxs-lookup"><span data-stu-id="98bf4-269">There are three major concepts in ML.NET: [Data](../basic-concepts-model-training-in-mldotnet.md#data), [Transformers](../basic-concepts-model-training-in-mldotnet.md#transformer), and [Estimators](../basic-concepts-model-training-in-mldotnet.md#estimator).</span></span>

## <a name="reuse-and-tune-pre-trained-model"></a><span data-ttu-id="98bf4-270">Reutilizar e ajustar um modelo pré-treinado</span><span class="sxs-lookup"><span data-stu-id="98bf4-270">Reuse and tune pre-trained model</span></span>

<span data-ttu-id="98bf4-271">Adicione a seguinte chamada ao método `ReuseAndTuneInceptionModel()` como a próxima linha de código no método `Main()`:</span><span class="sxs-lookup"><span data-stu-id="98bf4-271">Add the following call to the `ReuseAndTuneInceptionModel()`method as the next line of code in the `Main()` method:</span></span>

[!code-csharp[CallReuseAndTuneInceptionModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallReuseAndTuneInceptionModel)]

<span data-ttu-id="98bf4-272">O método `ReuseAndTuneInceptionModel()` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="98bf4-272">The `ReuseAndTuneInceptionModel()` method executes the following tasks:</span></span>

* <span data-ttu-id="98bf4-273">Carrega os dados.</span><span class="sxs-lookup"><span data-stu-id="98bf4-273">Loads the data</span></span>
* <span data-ttu-id="98bf4-274">Extrai e transforma os dados.</span><span class="sxs-lookup"><span data-stu-id="98bf4-274">Extracts and transforms the data.</span></span>
* <span data-ttu-id="98bf4-275">Pontua o modelo do TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="98bf4-275">Scores the TensorFlow model.</span></span>
* <span data-ttu-id="98bf4-276">Ajusta (readapta) o modelo.</span><span class="sxs-lookup"><span data-stu-id="98bf4-276">Tunes (retrains) the model.</span></span>
* <span data-ttu-id="98bf4-277">Exibe os resultados do modelo.</span><span class="sxs-lookup"><span data-stu-id="98bf4-277">Displays model results.</span></span>
* <span data-ttu-id="98bf4-278">Avalia o modelo.</span><span class="sxs-lookup"><span data-stu-id="98bf4-278">Evaluates the model.</span></span>
* <span data-ttu-id="98bf4-279">Salva o modelo.</span><span class="sxs-lookup"><span data-stu-id="98bf4-279">Saves the model.</span></span>

<span data-ttu-id="98bf4-280">Crie o método `ReuseAndTuneInceptionModel()` logo após o struct `InceptionSettings` e antes do método `PairAndDisplayResults()`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="98bf4-280">Create the `ReuseAndTuneInceptionModel()` method, just after the `InceptionSettings` struct and just before the `PairAndDisplayResults()` method, using the following code:</span></span>

```csharp
public static void ReuseAndTuneInceptionModel(MLContext mlContext, string dataLocation, string imagesFolder, string inputModelLocation, string outputModelLocation)
{

}
```

### <a name="load-the-data"></a><span data-ttu-id="98bf4-281">Carregar os dados</span><span class="sxs-lookup"><span data-stu-id="98bf4-281">Load the data</span></span>

<span data-ttu-id="98bf4-282">Os dados do ML.NET são representados como uma [classe IDataView](xref:Microsoft.Data.DataView.IDataView).</span><span class="sxs-lookup"><span data-stu-id="98bf4-282">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.Data.DataView.IDataView).</span></span> <span data-ttu-id="98bf4-283">`IDataView` é uma maneira flexível e eficiente de descrever dados tabulares (numéricos e texto).</span><span class="sxs-lookup"><span data-stu-id="98bf4-283">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="98bf4-284">Os dados podem ser carregados de um arquivo de texto ou em tempo real (por exemplo, banco de dados SQL ou arquivos de log) para um objeto `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="98bf4-284">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

<span data-ttu-id="98bf4-285">Carregue os dados usando o wrapper `MLContext.Data.ReadFromTextFile`.</span><span class="sxs-lookup"><span data-stu-id="98bf4-285">Load the data using the `MLContext.Data.ReadFromTextFile` wrapper.</span></span> <span data-ttu-id="98bf4-286">Adicione o seguinte código ao método `ReuseAndTuneInceptionModel()` como a linha seguinte:</span><span class="sxs-lookup"><span data-stu-id="98bf4-286">Add the following code as the next line in the `ReuseAndTuneInceptionModel()` method:</span></span>

[!code-csharp[LoadData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadData "Load the data")]

### <a name="extract-features-and-transform-the-data"></a><span data-ttu-id="98bf4-287">Extrair recursos e transformar os dados</span><span class="sxs-lookup"><span data-stu-id="98bf4-287">Extract Features and transform the data</span></span>

<span data-ttu-id="98bf4-288">O pré-processamento e a limpeza de dados são tarefas importantes que ocorrem antes de um conjunto de dados ser usado efetivamente para o aprendizado de máquina.</span><span class="sxs-lookup"><span data-stu-id="98bf4-288">Pre-processing and cleaning data are important tasks that occur before a dataset is used effectively for machine learning.</span></span>  <span data-ttu-id="98bf4-289">Usar dados sem essas tarefas de modelagem pode produzir resultados enganosos.</span><span class="sxs-lookup"><span data-stu-id="98bf4-289">Using data without these modeling tasks can produce misleading results.</span></span>

<span data-ttu-id="98bf4-290">Algoritmos de aprendizado de máquina entendem [dados caracterizados](../resources/glossary.md#feature), e ao lidar com redes neurais profundas você deve adaptar as imagens ao formato esperado pela rede.</span><span class="sxs-lookup"><span data-stu-id="98bf4-290">Machine learning algorithms understand [featurized](../resources/glossary.md#feature) data, and when dealing with deep neural networks you must adapt the images to the format expected by the network.</span></span> <span data-ttu-id="98bf4-291">Esse formato é um [vetor numérico](../resources/glossary.md#numerical-feature-vector).</span><span class="sxs-lookup"><span data-stu-id="98bf4-291">That format is a [numeric vector](../resources/glossary.md#numerical-feature-vector).</span></span>

<span data-ttu-id="98bf4-292">Após o treinamento e a avaliação, faça a previsão com os valores da coluna **Rótulo**.</span><span class="sxs-lookup"><span data-stu-id="98bf4-292">After training and evaluation, predict with the **Label** column values.</span></span> <span data-ttu-id="98bf4-293">Ao usar um modelo pré-treinado, mapeie os campos para o novo modelo com o método [MapValueToKey ()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A).</span><span class="sxs-lookup"><span data-stu-id="98bf4-293">As you're using a pre-trained model, map fields to the new model with the [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) method.</span></span> <span data-ttu-id="98bf4-294">Este método transforma a coluna `Label` em um tipo de chave numérica (`LabelTokey`) e a adiciona como nova coluna do conjunto de dados:  Dê um nome a este `estimator` porque você também adicionará o treinador a ele.</span><span class="sxs-lookup"><span data-stu-id="98bf4-294">This method transforms the `Label` into a numeric key type (`LabelTokey`) column and add it as new dataset column:  Name this `estimator` as you'll also add the trainer to it.</span></span> <span data-ttu-id="98bf4-295">Adicione a seguinte linha de código:</span><span class="sxs-lookup"><span data-stu-id="98bf4-295">Add the next line of code:</span></span>

[!code-csharp[MapValueToKey1](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey1)]

<span data-ttu-id="98bf4-296">O seu estimador de processamento de imagens usa recursos de recursos para extração de recursos pré-treinados [Deep Neural Network (DNN)](https://en.wikipedia.org/wiki/Deep_learning#Deep_neural_networks).</span><span class="sxs-lookup"><span data-stu-id="98bf4-296">Your image processing estimator uses pre-trained [Deep Neural Network(DNN)](https://en.wikipedia.org/wiki/Deep_learning#Deep_neural_networks) featurizers for feature extraction.</span></span> <span data-ttu-id="98bf4-297">Ao lidar com redes neurais profundas, você adapta as imagens ao formato de rede esperado.</span><span class="sxs-lookup"><span data-stu-id="98bf4-297">When dealing with deep neural networks, you  adapt the images to the expected network format.</span></span> <span data-ttu-id="98bf4-298">Essa é a razão pela qual você usa várias transformações de imagem para obter os dados da imagem no formato esperado do modelo:</span><span class="sxs-lookup"><span data-stu-id="98bf4-298">This is the reason you use several image transforms to get the image data into the model's expected form:</span></span>

1. <span data-ttu-id="98bf4-299">As imagens de transformação `LoadImages` são carregadas na memória como um tipo de bitmap.</span><span class="sxs-lookup"><span data-stu-id="98bf4-299">The `LoadImages`transform images are loaded in memory as a Bitmap type.</span></span>
2. <span data-ttu-id="98bf4-300">A transformação `Resize` redimensiona as imagens porque o modelo pré-treinado tem uma largura e altura de imagem de entrada definidas.</span><span class="sxs-lookup"><span data-stu-id="98bf4-300">The `Resize` transform resizes the images as the pre-trained model has a defined input image width and height.</span></span>
3. <span data-ttu-id="98bf4-301">A transformação `ImagePixelExtractingEstimator` extrai os pixels das imagens de entrada e os converte em um vetor numérico.</span><span class="sxs-lookup"><span data-stu-id="98bf4-301">The `ImagePixelExtractingEstimator` transform extracts the pixels from the input images and converts them into a numeric vector.</span></span>

<span data-ttu-id="98bf4-302">Adicione essas transformações de imagem como as próximas linhas de código:</span><span class="sxs-lookup"><span data-stu-id="98bf4-302">Add these image transforms as the next lines of code:</span></span>

[!code-csharp[ImageTransforms](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ImageTransforms)]

<span data-ttu-id="98bf4-303">O `TensorFlowTransform` extrai as saídas especificadas (os recursos da imagem do `Inception model``softmax2_pre_activation`) e marca um conjunto de dados usando o model o`TensorFlow` pré-treinado.</span><span class="sxs-lookup"><span data-stu-id="98bf4-303">The `TensorFlowTransform` extracts specified outputs (the `Inception model`'s image features `softmax2_pre_activation`), and scores a dataset using the pre-trained `TensorFlow` model.</span></span>

<span data-ttu-id="98bf4-304">`softmax2_pre_activation` auxilia o modelo a determinar a qual classe as imagens pertencem.</span><span class="sxs-lookup"><span data-stu-id="98bf4-304">`softmax2_pre_activation` assists the model with determining which class the images belongs to.</span></span> <span data-ttu-id="98bf4-305">`softmax2_pre_activation` retorna uma probabilidade para cada uma das categorias para uma imagem, e todas essas probabilidades devem somar 1.</span><span class="sxs-lookup"><span data-stu-id="98bf4-305">`softmax2_pre_activation` returns a probability for each of the categories for an image, and all of those probabilities must add up to 1.</span></span> <span data-ttu-id="98bf4-306">Ele pressupõe que uma imagem pertencerá a apenas uma categoria, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="98bf4-306">It assumes that an image will belong to only one category, as shown in the following example:</span></span>

| <span data-ttu-id="98bf4-307">Classe</span><span class="sxs-lookup"><span data-stu-id="98bf4-307">Class</span></span>         | <span data-ttu-id="98bf4-308">Probabilidade</span><span class="sxs-lookup"><span data-stu-id="98bf4-308">Probability</span></span>   |
| ------------- | ------------- |
| `Food`        |  <span data-ttu-id="98bf4-309">0.001</span><span class="sxs-lookup"><span data-stu-id="98bf4-309">0.001</span></span>        |
| `Toy`         |  <span data-ttu-id="98bf4-310">0.95</span><span class="sxs-lookup"><span data-stu-id="98bf4-310">0.95</span></span>         |
| `Appliance`   |  <span data-ttu-id="98bf4-311">0.06</span><span class="sxs-lookup"><span data-stu-id="98bf4-311">0.06</span></span>         |

<span data-ttu-id="98bf4-312">Adicione `TensorFlowTransform` ao `estimator` com a seguinte linha de código:</span><span class="sxs-lookup"><span data-stu-id="98bf4-312">Append the `TensorFlowTransform` to the `estimator` with the following line of code:</span></span>

[!code-csharp[ScoreTensorFlowModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ScoreTensorFlowModel)]

### <a name="choose-a-training-algorithm"></a><span data-ttu-id="98bf4-313">Escolher um algoritmo de treinamento</span><span class="sxs-lookup"><span data-stu-id="98bf4-313">Choose a training algorithm</span></span>

<span data-ttu-id="98bf4-314">Para adicionar o algoritmo de treinamento, chame o método wrapper `mlContext.MulticlassClassification.Trainers.LogisticRegression()`.</span><span class="sxs-lookup"><span data-stu-id="98bf4-314">To add the training algorithm, call the `mlContext.MulticlassClassification.Trainers.LogisticRegression()` wrapper method.</span></span>  <span data-ttu-id="98bf4-315">O `LogisticRegression` é anexado ao `estimator` e aceita os recursos da imagem Concepção (`softmax2_pre_activation`) e os parâmetros de entrada `Label` para aprender com os dados históricos.</span><span class="sxs-lookup"><span data-stu-id="98bf4-315">The `LogisticRegression` is appended to the `estimator` and accepts the Inception image features (`softmax2_pre_activation`) and the `Label` input parameters to learn from the historic data.</span></span>  <span data-ttu-id="98bf4-316">Adicione o treinador com o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="98bf4-316">Add the trainer with the following code:</span></span>

[!code-csharp[AddTrainer](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddTrainer)]

<span data-ttu-id="98bf4-317">Você também precisa mapear o `predictedlabel` para o `predictedlabelvalue`:</span><span class="sxs-lookup"><span data-stu-id="98bf4-317">You also need to map the `predictedlabel` to the `predictedlabelvalue`:</span></span>

[!code-csharp[MapValueToKey2](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey2)]

<span data-ttu-id="98bf4-318">O método `Fit()` treina o modelo com o conjunto de dados de treinamento fornecido.</span><span class="sxs-lookup"><span data-stu-id="98bf4-318">The `Fit()` method trains your model with the provided training dataset.</span></span> <span data-ttu-id="98bf4-319">Ele executa as definições `Estimator` transformando os dados e aplicando o treinamento e retorna o modelo treinado, que é um `Transformer`.</span><span class="sxs-lookup"><span data-stu-id="98bf4-319">It executes the `Estimator` definitions by transforming the data and applying the training, and it returns back the trained model, which is a `Transformer`.</span></span> <span data-ttu-id="98bf4-320">Ajuste o modelo aos dados `Train` e retorne o modelo treinado adicionando o seguinte como a próxima linha de código no método `ReuseAndTuneInceptionModel()`:</span><span class="sxs-lookup"><span data-stu-id="98bf4-320">Fit the model to the `Train` data and return the trained model by adding the following as the next line of code in the `ReuseAndTuneInceptionModel()` method:</span></span>

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TrainModel)]

<span data-ttu-id="98bf4-321">O método [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) faz previsões para várias linhas de entrada fornecidas de um conjunto de dados de teste.</span><span class="sxs-lookup"><span data-stu-id="98bf4-321">The [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method makes predictions for multiple provided input rows of a test dataset.</span></span>  <span data-ttu-id="98bf4-322">Transforme os dados `Training` adicionando o seguinte código a `ReuseAndTuneInceptionModel()`:</span><span class="sxs-lookup"><span data-stu-id="98bf4-322">Transform the `Training` data by adding the following code to `ReuseAndTuneInceptionModel()`:</span></span>

[!code-csharp[TransformData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TransformData)]

<span data-ttu-id="98bf4-323">Converta seus dados de imagem e previsão `DataViews` em `IEnumerables` fortemente tipados para emparelhar para exibição mais fácil.</span><span class="sxs-lookup"><span data-stu-id="98bf4-323">Convert your image data and prediction `DataViews` into strongly-typed `IEnumerables` to pair for easier display.</span></span> <span data-ttu-id="98bf4-324">Use o método `MLContext.CreateEnumerable()` para fazer isso, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="98bf4-324">Use the `MLContext.CreateEnumerable()` method to do that, using the following code:</span></span>

[!code-csharp[EnumerateDataViews](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#EnumerateDataViews)]

<span data-ttu-id="98bf4-325">Chame o método `PairAndDisplayResults()` para parear e exibir seus dados e previsões como a próxima linha no método `ReuseAndTuneInceptionModel()`:</span><span class="sxs-lookup"><span data-stu-id="98bf4-325">Call the `PairAndDisplayResults()` method to pair and display your data and predictions as the next line in the `ReuseAndTuneInceptionModel()` method:</span></span>

[!code-csharp[CallPairAndDisplayResults1](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallPairAndDisplayResults1)]

<span data-ttu-id="98bf4-326">Depois de determinar a previsão, o método [Evaluate ()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A):</span><span class="sxs-lookup"><span data-stu-id="98bf4-326">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) method:</span></span>

* <span data-ttu-id="98bf4-327">Avalia o modelo (compara os valores previstos com o conjunto de dados real `Labels`).</span><span class="sxs-lookup"><span data-stu-id="98bf4-327">Assesses the model (compares the predicted values with the actual dataset `Labels`).</span></span>

* <span data-ttu-id="98bf4-328">Retorna as métricas de desempenho do modelo.</span><span class="sxs-lookup"><span data-stu-id="98bf4-328">Returns the model performance metrics.</span></span> 

<span data-ttu-id="98bf4-329">Adicione o seguinte código ao método `ReuseAndTuneInceptionModel()` como a linha seguinte:</span><span class="sxs-lookup"><span data-stu-id="98bf4-329">Add the following code to the `ReuseAndTuneInceptionModel()` method as the next line:</span></span>

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Evaluate)]

<span data-ttu-id="98bf4-330">As seguintes métricas são avaliadas para classificação de imagem:</span><span class="sxs-lookup"><span data-stu-id="98bf4-330">The following metrics are evaluated for image classification:</span></span>

* <span data-ttu-id="98bf4-331">`Log-loss` - confira [Perda de log](../resources/glossary.md#log-loss).</span><span class="sxs-lookup"><span data-stu-id="98bf4-331">`Log-loss` - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="98bf4-332">Convém que a Perda de log seja tão próxima de zero quanto possível.</span><span class="sxs-lookup"><span data-stu-id="98bf4-332">You want Log-loss to be as close to zero as possible.</span></span>

* <span data-ttu-id="98bf4-333">`Per class Log-loss`.</span><span class="sxs-lookup"><span data-stu-id="98bf4-333">`Per class Log-loss`.</span></span> <span data-ttu-id="98bf4-334">Convém que a Perda de log por classe seja tão próxima de zero quanto possível.</span><span class="sxs-lookup"><span data-stu-id="98bf4-334">You want per class Log-loss to be as close to zero as possible.</span></span>

<span data-ttu-id="98bf4-335">Use o código a seguir para exibir as métricas, compartilhar os resultados e, em seguida, agir com relação a eles:</span><span class="sxs-lookup"><span data-stu-id="98bf4-335">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayMetrics)]

<span data-ttu-id="98bf4-336">`mlContext.Model.Save` salva o modelo treinado em um arquivo .zip (na pasta "ativos/saídas"), que pode ser usado em outros aplicativos .NET para fazer previsões.</span><span class="sxs-lookup"><span data-stu-id="98bf4-336">`mlContext.Model.Save` saves your trained model to a .zip file (in the "assets/outputs" folder), which can be used in other .NET applications to make predictions.</span></span> <span data-ttu-id="98bf4-337">Adicione o seguinte código ao método `ReuseAndTuneInceptionModel()` como a linha seguinte:</span><span class="sxs-lookup"><span data-stu-id="98bf4-337">Add the following code to the `ReuseAndTuneInceptionModel()` method as the next line:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#SaveModel)]

## <a name="classify-images-with-a-loaded-model"></a><span data-ttu-id="98bf4-338">Classificar imagens com um modelo carregado</span><span class="sxs-lookup"><span data-stu-id="98bf4-338">Classify images with a loaded model</span></span>

<span data-ttu-id="98bf4-339">Adicione a seguinte chamada ao método `ClassifyImages()` como a próxima linha de código no método `Main`:</span><span class="sxs-lookup"><span data-stu-id="98bf4-339">Add the following call to the `ClassifyImages()` method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallClassifyImages](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifyImages)]

<span data-ttu-id="98bf4-340">O método `ClassifyImages()` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="98bf4-340">The `ClassifyImages()` method executes the following tasks:</span></span>

* <span data-ttu-id="98bf4-341">Aplica o modelo.</span><span class="sxs-lookup"><span data-stu-id="98bf4-341">Loads the model.</span></span>
* <span data-ttu-id="98bf4-342">Lê o arquivo .TSV em `IEnumerable`.</span><span class="sxs-lookup"><span data-stu-id="98bf4-342">Reads .TSV file into `IEnumerable`.</span></span>
* <span data-ttu-id="98bf4-343">Prevê as classificações de imagens com base nos dados de teste.</span><span class="sxs-lookup"><span data-stu-id="98bf4-343">Predicts image classifications based on test data.</span></span>

<span data-ttu-id="98bf4-344">Crie o método `ClassifyImages()` logo após o método `ReuseAndTuneInceptionModel()` (e antes do método `PairAndDisplayResults()`) usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="98bf4-344">Create the `ClassifyImages()` method, just after the `ReuseAndTuneInceptionModel()` method and just before the `PairAndDisplayResults()` method, using the following code:</span></span>

```csharp
public static void ClassifyImages(MLContext mlContext, string dataLocation, string imagesFolder, string outputModelLocation)
{

}
```

<span data-ttu-id="98bf4-345">Primeiro, carregue o modelo que você salvou anteriormente com o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="98bf4-345">First, load the model that you saved previously with the following code:</span></span>

[!code-csharp[LoadModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadModel)]

<span data-ttu-id="98bf4-346">Chame o método `ReadFromTsv()` para criar uma classe `IEnumerable<ImageData>` que contenha o caminho absoluto para cada `ImagePath`.</span><span class="sxs-lookup"><span data-stu-id="98bf4-346">Call the `ReadFromTsv()` method to create an `IEnumerable<ImageData>` class that contains the fully qualified path for each `ImagePath`.</span></span> <span data-ttu-id="98bf4-347">Você precisa desse caminho de arquivo para parear seus dados e resultados de previsão.</span><span class="sxs-lookup"><span data-stu-id="98bf4-347">You need that file path to pair your data and prediction results.</span></span> <span data-ttu-id="98bf4-348">Você também precisa converter a classe `IEnumerable<ImageData>` para uma `IDataView` que você usará para fazer a previsão.</span><span class="sxs-lookup"><span data-stu-id="98bf4-348">You also need to convert the `IEnumerable<ImageData>` class to an `IDataView` that you will use to predict.</span></span> <span data-ttu-id="98bf4-349">Adicione o seguinte código como as próximas duas linhas no método `ClassifyImages()`:</span><span class="sxs-lookup"><span data-stu-id="98bf4-349">Add the following code as the next two lines in the `ClassifyImages()` method:</span></span>

[!code-csharp[ReadFromTSV](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReadFromTSV)]

<span data-ttu-id="98bf4-350">Como você fez anteriormente com os dados da imagem de treinamento, preveja a categoria dos dados da imagem de teste usando o método [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A).</span><span class="sxs-lookup"><span data-stu-id="98bf4-350">As you did previously with the training image data, predict the category of the test image data using the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method.</span></span> <span data-ttu-id="98bf4-351">Adicione o seguinte código ao método `ClassifyImages()` para as previsões e converta `predictions``IDataView` em um `IEnumerable` para parear e exibir:</span><span class="sxs-lookup"><span data-stu-id="98bf4-351">Add the following code to the `ClassifyImages()` method for the predictions and to convert the `predictions` `IDataView` into an `IEnumerable` for pairing and display:</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Predict)]

<span data-ttu-id="98bf4-352">Para parear e exibir os dados e as previsões da sua imagem de teste, adicione o código a seguir para chamar o método `PairAndDisplayResults()` criado anteriormente como a próxima linha no método `ClassifyImages()`:</span><span class="sxs-lookup"><span data-stu-id="98bf4-352">To pair and display your test image data and predictions, add the following code to call the `PairAndDisplayResults()` method previously created as the next line in the `ClassifyImages()` method:</span></span>

[!code-csharp[CallPairAndDisplayResults2](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallPairAndDisplayResults2)]

## <a name="classify-a-single-image-with-a-loaded-model"></a><span data-ttu-id="98bf4-353">Classifique uma única imagem com um modelo carregado</span><span class="sxs-lookup"><span data-stu-id="98bf4-353">Classify a single image with a loaded model</span></span>

<span data-ttu-id="98bf4-354">Adicione a seguinte chamada ao método `ClassifySingleImage()` como a próxima linha de código no método `Main`:</span><span class="sxs-lookup"><span data-stu-id="98bf4-354">Add the following call to the `ClassifySingleImage()` method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallClassifySingleImage](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifySingleImage)]

<span data-ttu-id="98bf4-355">O método `ClassifyImages()` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="98bf4-355">The `ClassifyImages()` method executes the following tasks:</span></span>

* <span data-ttu-id="98bf4-356">Aplica o modelo.</span><span class="sxs-lookup"><span data-stu-id="98bf4-356">Loads the model.</span></span>
* <span data-ttu-id="98bf4-357">Carrega uma instância `ImageData`.</span><span class="sxs-lookup"><span data-stu-id="98bf4-357">Loads an `ImageData` instance.</span></span>
* <span data-ttu-id="98bf4-358">Prevê a classificação de imagens com base nos dados de teste.</span><span class="sxs-lookup"><span data-stu-id="98bf4-358">Predicts image classification based on test data.</span></span>

<span data-ttu-id="98bf4-359">Crie o método `ClassifySingleImage()` logo após o método `ClassifyImages()` (e antes do método `PairAndDisplayResults()`) usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="98bf4-359">Create the `ClassifySingleImage()` method, just after the `ClassifyImages()` method and just before the `PairAndDisplayResults()` method, using the following code:</span></span>

```csharp
public static void ClassifySingleImage(MLContext mlContext, string imagePath, string outputModelLocation)
{

}
```

<span data-ttu-id="98bf4-360">Primeiro, carregue o modelo que você salvou anteriormente com o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="98bf4-360">First, load the model that you saved previously with the following code:</span></span>

[!code-csharp[LoadModel2](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadModel2)]

<span data-ttu-id="98bf4-361">Crie uma classe `ImageData` que contenha o caminho completo e o nome do arquivo de imagem para o único `ImagePath`.</span><span class="sxs-lookup"><span data-stu-id="98bf4-361">Create an `ImageData` class that contains the fully qualified path and image file name for the single `ImagePath`.</span></span> <span data-ttu-id="98bf4-362">Adicione o seguinte código como as próximas linhas no método `ClassifySingleImage()`:</span><span class="sxs-lookup"><span data-stu-id="98bf4-362">Add the following code as the next  lines in the `ClassifySingleImage()` method:</span></span>

[!code-csharp[LoadImageData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadImageData)]

<span data-ttu-id="98bf4-363">A classe [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) é uma API de conveniência que executa uma previsão em uma única instância de dados.</span><span class="sxs-lookup"><span data-stu-id="98bf4-363">The [PredictionEngine class](xref:Microsoft.ML.PredictionEngine%602) is a convenience API that performs a prediction on a single instance of data.</span></span> <span data-ttu-id="98bf4-364">A função [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) faz uma previsão sobre uma única coluna de dados.</span><span class="sxs-lookup"><span data-stu-id="98bf4-364">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single column of data.</span></span> <span data-ttu-id="98bf4-365">Passe `imageData` para `PredictionEngine` para prever a categoria da imagem adicionando o seguinte código a `ClassifySingleImage()`:</span><span class="sxs-lookup"><span data-stu-id="98bf4-365">Pass `imageData` to the `PredictionEngine` to predict the image category by adding the following code to `ClassifySingleImage()`:</span></span>

[!code-csharp[PredictSingle](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#PredictSingle)]

<span data-ttu-id="98bf4-366">Exiba o resultado da previsão como a próxima linha de código no método `ClassifySingleImage()`:</span><span class="sxs-lookup"><span data-stu-id="98bf4-366">Display the prediction result as the next line of code in the `ClassifySingleImage()` method:</span></span>

[!code-csharp[DisplayPrediction](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPrediction)]

## <a name="results"></a><span data-ttu-id="98bf4-367">Resultados</span><span class="sxs-lookup"><span data-stu-id="98bf4-367">Results</span></span>

<span data-ttu-id="98bf4-368">Depois de seguir as etapas anteriores, execute o aplicativo de console (Ctrl+F5).</span><span class="sxs-lookup"><span data-stu-id="98bf4-368">After following the previous steps, run your console app (Ctrl + F5).</span></span> <span data-ttu-id="98bf4-369">O resultado deverá ser semelhante à seguinte saída.</span><span class="sxs-lookup"><span data-stu-id="98bf4-369">Your results should be similar to the following output.</span></span>  <span data-ttu-id="98bf4-370">Você poderá ver avisos ou mensagens de processamento, mas essas mensagens foram removidas dos resultados a seguir para maior clareza.</span><span class="sxs-lookup"><span data-stu-id="98bf4-370">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

```console
=============== Training classification model ===============
Image: broccoli.jpg predicted as: food with score: 0.976743
Image: pizza.jpg predicted as: food with score: 0.9751652
Image: pizza2.jpg predicted as: food with score: 0.9660203
Image: teddy2.jpg predicted as: toy with score: 0.9748783
Image: teddy3.jpg predicted as: toy with score: 0.9829691
Image: teddy4.jpg predicted as: toy with score: 0.9868168
Image: toaster.jpg predicted as: appliance with score: 0.9769174
Image: toaster2.png predicted as: appliance with score: 0.9800823
=============== Classification metrics ===============
LogLoss is: 0.0228266745633507
PerClassLogLoss is: 0.0277501705149937 , 0.0186303530571291 , 0.0217359128952187
=============== Save model to local file ===============
Model saved: C:\Tutorials\TransferLearningTF\bin\Debug\netcoreapp2.2\assets\outputs\imageClassifier.zip
=============== Loading model ===============
Model loaded: C:\Tutorials\TransferLearningTF\bin\Debug\netcoreapp2.2\assets\outputs\imageClassifier.zip
=============== Making classifications ===============
Image: broccoli.png predicted as: food with score: 0.905548
Image: pizza3.jpg predicted as: food with score: 0.9709008
Image: teddy6.jpg predicted as: toy with score: 0.9750155
=============== Loading model ===============
Model loaded: C:\Tutorials\TransferLearningTF\bin\Debug\netcoreapp2.2\assets\outputs\imageClassifier.zip
=============== Making single image classification ===============
Image: toaster3.jpg predicted as: appliance with score: 0.9625379
Press any key to continue . . .
```

<span data-ttu-id="98bf4-371">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="98bf4-371">Congratulations!</span></span> <span data-ttu-id="98bf4-372">Agora você criou com sucesso um modelo de aprendizado de máquina para classificação de imagem reutilizando um modelo `TensorFlow` pré-treinado no ML.NET.</span><span class="sxs-lookup"><span data-stu-id="98bf4-372">You've now successfully built a machine learning model for image classification by reusing a pre-trained `TensorFlow` model in ML.NET.</span></span>

<span data-ttu-id="98bf4-373">Você pode encontrar o código-fonte para este tutorial no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF).</span><span class="sxs-lookup"><span data-stu-id="98bf4-373">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repository.</span></span>

<span data-ttu-id="98bf4-374">Neste tutorial, você aprendeu como:</span><span class="sxs-lookup"><span data-stu-id="98bf4-374">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="98bf4-375">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="98bf4-375">Understand the problem</span></span>
> * <span data-ttu-id="98bf4-376">Reutilizar e ajustar o modelo pré-treinado</span><span class="sxs-lookup"><span data-stu-id="98bf4-376">Reuse and tune the pre-trained model</span></span>
> * <span data-ttu-id="98bf4-377">Classificar imagens com um modelo carregado</span><span class="sxs-lookup"><span data-stu-id="98bf4-377">Classify images with a loaded model</span></span>

<span data-ttu-id="98bf4-378">Conferir o repositório GitHub de Amostras de Aprendizado de Máquina para explorar uma amostra de classificação de imagem expandida.</span><span class="sxs-lookup"><span data-stu-id="98bf4-378">Check out the Machine Learning samples GitHub repository to explore an expanded image classification sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="98bf4-379">dotnet/machinelearning-samples GitHub repository</span><span class="sxs-lookup"><span data-stu-id="98bf4-379">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/)
