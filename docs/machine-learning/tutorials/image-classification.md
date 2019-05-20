---
title: 'Tutorial: Criar um classificador de imagens personalizadas do ML.NET com o TensorFlow'
description: Descubra como criar um classificador de imagens personalizadas do ML.NET em um cenário de aprendizado de transferência do TensorFlow para classificar imagens reutilizando um modelo do TensorFlow pré-treinado.
ms.date: 05/06/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: f7fddc2d6c60a719090af36b7fe91919bfbd115c
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063624"
---
# <a name="tutorial-build-an-mlnet-custom-image-classifier-with-tensorflow"></a><span data-ttu-id="616f6-103">Tutorial: Criar um classificador de imagens personalizadas do ML.NET com o TensorFlow</span><span class="sxs-lookup"><span data-stu-id="616f6-103">Tutorial: Build an ML.NET custom image classifier with TensorFlow</span></span>

<span data-ttu-id="616f6-104">Este tutorial de amostra ilustra como você pode usar um modelo de Classificador de Imagens `TensorFlow` já treinado para criar um novo modelo customizado para classificar imagens em algumas categorias.</span><span class="sxs-lookup"><span data-stu-id="616f6-104">This sample tutorial illustrates how you can use an already trained Image Classifier `TensorFlow` model to build a new custom model to classify images into a few categories.</span></span>

<span data-ttu-id="616f6-105">E se você pudesse reutilizar um modelo que já tenha sido pré-treinado para resolver um problema semelhante e treinar novamente todas ou algumas das camadas desse modelo para resolvê-lo?</span><span class="sxs-lookup"><span data-stu-id="616f6-105">What if you could reuse a model that's already been pre trained to solve a similar problem and retrain either all or some of the layers of that model to make it solve your problem?</span></span> <span data-ttu-id="616f6-106">Essa técnica de reutilizar parte de um modelo já treinado para construir um novo modelo é conhecida como [aprendizado de transferência](https://en.wikipedia.org/wiki/Transfer_learning).</span><span class="sxs-lookup"><span data-stu-id="616f6-106">This technique of reusing part of an already trained model to build a new model is known as [transfer learning](https://en.wikipedia.org/wiki/Transfer_learning).</span></span>

<span data-ttu-id="616f6-107">Treinar um modelo de [Classificação de Imagens](https://en.wikipedia.org/wiki/Outline_of_object_recognition) do zero requer a configuração de milhões de parâmetros, uma tonelada de dados de treinamento rotulados e uma grande quantidade de recursos de computação (centenas de horas de GPU).</span><span class="sxs-lookup"><span data-stu-id="616f6-107">Training an [Image Classification](https://en.wikipedia.org/wiki/Outline_of_object_recognition) model from scratch requires setting millions of parameters, a ton of labeled training data and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="616f6-108">Embora não seja tão eficaz quanto treinar um modelo personalizado do zero, o aprendizado de transferência permite que você ative esse processo trabalhando com milhares de imagens em comparação com milhões de imagens rotuladas e crie um modelo personalizado rapidamente (em uma hora em uma máquina sem GPU).</span><span class="sxs-lookup"><span data-stu-id="616f6-108">While not as effective as training a custom model from scratch, transfer learning allows you to shortcut this process by working with thousands of images vs. millions of labeled images and build a customized model fairly quickly (within an hour on a machine without a GPU).</span></span>

<span data-ttu-id="616f6-109">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="616f6-109">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="616f6-110">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="616f6-110">Understand the problem</span></span>
> * <span data-ttu-id="616f6-111">Reutilizar e ajustar o modelo pré-treinado</span><span class="sxs-lookup"><span data-stu-id="616f6-111">Reuse and tune the pre-trained model</span></span>
> * <span data-ttu-id="616f6-112">Classificar imagens</span><span class="sxs-lookup"><span data-stu-id="616f6-112">Classify Images</span></span>

## <a name="image-classification-sample-overview"></a><span data-ttu-id="616f6-113">Visão geral da amostra de classificação de imagens</span><span class="sxs-lookup"><span data-stu-id="616f6-113">Image classification sample overview</span></span>

<span data-ttu-id="616f6-114">O exemplo é um aplicativo de console que usa o ML.NET para criar um classificador de imagens reutilizando um modelo pré-treinado para classificar imagens com uma pequena quantidade de dados de treinamento.</span><span class="sxs-lookup"><span data-stu-id="616f6-114">The sample is a console application that uses ML.NET to build an image classifier by reusing a pre-trained model to classify images with a small amount of training data.</span></span>

<span data-ttu-id="616f6-115">Você pode encontrar o código-fonte para este tutorial no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF).</span><span class="sxs-lookup"><span data-stu-id="616f6-115">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="616f6-116">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="616f6-116">Prerequisites</span></span>

* <span data-ttu-id="616f6-117">[Visual Studio 2017 15.6 ou posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" instalada.</span><span class="sxs-lookup"><span data-stu-id="616f6-117">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

* <span data-ttu-id="616f6-118">Pacote do Nuget Microsoft.ML 1.0.0</span><span class="sxs-lookup"><span data-stu-id="616f6-118">Microsoft.ML 1.0.0 Nuget package</span></span>
* <span data-ttu-id="616f6-119">Pacote do Nuget Microsoft.ML.ImageAnalytics 1.0.0</span><span class="sxs-lookup"><span data-stu-id="616f6-119">Microsoft.ML.ImageAnalytics 1.0.0 Nuget package</span></span>
* <span data-ttu-id="616f6-120">Pacote do Nuget Microsoft.ML.TensorFlow 0.12.0</span><span class="sxs-lookup"><span data-stu-id="616f6-120">Microsoft.ML.TensorFlow 0.12.0 Nuget package</span></span>

* [<span data-ttu-id="616f6-121">O arquivo .ZIP do diretório de recursos do tutorial</span><span class="sxs-lookup"><span data-stu-id="616f6-121">The tutorial assets directory .ZIP file</span></span>](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip)

* [<span data-ttu-id="616f6-122">O modelo de aprendizado de máquina InceptionV3</span><span class="sxs-lookup"><span data-stu-id="616f6-122">The InceptionV3 machine learning model</span></span>](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="616f6-123">Selecionar a tarefa de aprendizado de máquina apropriada</span><span class="sxs-lookup"><span data-stu-id="616f6-123">Select the appropriate machine learning task</span></span>

<span data-ttu-id="616f6-124">[Aprendizado profundo](https://en.wikipedia.org/wiki/Deep_learning) é um subconjunto do aprendizado de máquina, que está revolucionando áreas como Pesquisa Visual Computacional e Reconhecimento de Fala.</span><span class="sxs-lookup"><span data-stu-id="616f6-124">[Deep learning](https://en.wikipedia.org/wiki/Deep_learning) is a subset of Machine Learning, which is revolutionizing areas like Computer Vision and Speech Recognition.</span></span>

<span data-ttu-id="616f6-125">Os modelos de aprendizado profundo são treinados usando grandes conjuntos de [dados rotulados](https://en.wikipedia.org/wiki/Labeled_data) e [redes neurais](https://en.wikipedia.org/wiki/Artificial_neural_network) que contêm várias camadas de aprendizado.</span><span class="sxs-lookup"><span data-stu-id="616f6-125">Deep learning models are trained by using large sets of [labeled data](https://en.wikipedia.org/wiki/Labeled_data) and [neural networks](https://en.wikipedia.org/wiki/Artificial_neural_network) that contain multiple learning layers.</span></span> <span data-ttu-id="616f6-126">Aprendizado profundo:</span><span class="sxs-lookup"><span data-stu-id="616f6-126">Deep learning:</span></span>

* <span data-ttu-id="616f6-127">Funciona melhor em algumas tarefas como a Pesquisa Visual Computacional.</span><span class="sxs-lookup"><span data-stu-id="616f6-127">Performs better on some tasks like Computer Vision.</span></span>

* <span data-ttu-id="616f6-128">Funciona bem em enormes quantidades de dados.</span><span class="sxs-lookup"><span data-stu-id="616f6-128">Performs well on huge data amounts.</span></span>

<span data-ttu-id="616f6-129">A classificação de imagens é uma tarefa comum de aprendizado de máquina que nos permite classificar automaticamente as imagens em várias categorias, como:</span><span class="sxs-lookup"><span data-stu-id="616f6-129">Image Classification is a common Machine Learning task that allows us to automatically classify images into multiple categories such as:</span></span>

* <span data-ttu-id="616f6-130">Detectar uma face humana em uma imagem ou não.</span><span class="sxs-lookup"><span data-stu-id="616f6-130">Detecting a human face in an image or not.</span></span>
* <span data-ttu-id="616f6-131">Detectar gatos e cachorros.</span><span class="sxs-lookup"><span data-stu-id="616f6-131">Detecting Cats vs. dogs.</span></span>

 <span data-ttu-id="616f6-132">Ou, como nas imagens a seguir, que determinar se uma imagem é um alimento, brinquedo ou dispositivo:</span><span class="sxs-lookup"><span data-stu-id="616f6-132">Or as in the following images determining if an image is a(n)  food, toy, or appliance:</span></span>

<span data-ttu-id="616f6-133">![imagem de pizza](./media/image-classification/220px-Pepperoni_pizza.jpg)
![imagem de ursinho de pelúcia](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![imagem de torradeira](./media/image-classification/193px-Broodrooster.jpg)</span><span class="sxs-lookup"><span data-stu-id="616f6-133">![pizza image](./media/image-classification/220px-Pepperoni_pizza.jpg)
![teddy bear image](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![toaster image](./media/image-classification/193px-Broodrooster.jpg)</span></span>

>[!Note]
> <span data-ttu-id="616f6-134">As imagens anteriores pertencem ao Wikimedia Commons e são atribuídas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="616f6-134">The preceding images belong to Wikimedia Commons and are attributed as follows:</span></span>
>
> * <span data-ttu-id="616f6-135">"220px-Pepperoni_pizza.jpg" Public Domain, https://commons.wikimedia.org/w/index.php?curid=79505,</span><span class="sxs-lookup"><span data-stu-id="616f6-135">"220px-Pepperoni_pizza.jpg" Public Domain, https://commons.wikimedia.org/w/index.php?curid=79505,</span></span>
> * <span data-ttu-id="616f6-136">"119px-Nalle_-_a_small_brown_teddy_bear.jpg" By [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) - Self-photographed, CC BY-SA 2.0, https://commons.wikimedia.org/w/index.php?curid=48166.</span><span class="sxs-lookup"><span data-stu-id="616f6-136">"119px-Nalle_-_a_small_brown_teddy_bear.jpg" By [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) - Self-photographed, CC BY-SA 2.0, https://commons.wikimedia.org/w/index.php?curid=48166.</span></span>
> * <span data-ttu-id="616f6-137">"193px-Broodrooster.jpg" By [M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) - Own work, CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=27403</span><span class="sxs-lookup"><span data-stu-id="616f6-137">"193px-Broodrooster.jpg" By [M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) - Own work, CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=27403</span></span>

<span data-ttu-id="616f6-138">O aprendizado de transferência inclui algumas estratégias, como *readaptar todas as camadas* e a *penúltima camada*.</span><span class="sxs-lookup"><span data-stu-id="616f6-138">Transfer learning includes a few strategies, such as *retrain all layers* and *penultimate layer*.</span></span> <span data-ttu-id="616f6-139">Esse tutorial explicará e mostrará como usar a *estratégia de penúltima camada*.</span><span class="sxs-lookup"><span data-stu-id="616f6-139">This tutorial will explain and show how to use the *penultimate layer strategy*.</span></span> <span data-ttu-id="616f6-140">A *estratégia de penúltima camada* reutiliza um modelo que já foi pré-treinado para resolver um problema específico.</span><span class="sxs-lookup"><span data-stu-id="616f6-140">The *penultimate layer strategy* reuses a model that's already been pre-trained to solve a specific problem.</span></span> <span data-ttu-id="616f6-141">A estratégia, em seguida, treina novamente a camada final desse modelo para resolver um novo problema.</span><span class="sxs-lookup"><span data-stu-id="616f6-141">The strategy then retrains the final layer of that model to make it solve a new problem.</span></span> <span data-ttu-id="616f6-142">Reutilizar o modelo pré-treinado como parte de seu novo modelo economizará tempo e recursos significativos.</span><span class="sxs-lookup"><span data-stu-id="616f6-142">Reusing the pre-trained model as part of your new model will save significant time and resources.</span></span>

<span data-ttu-id="616f6-143">Seu modelo de classificação de imagens reutiliza o modelo [Concepção](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), um popular modelo de reconhecimento de imagens treinado no conjunto de dados `ImageNet` em que o modelo TensorFlow tenta classificar imagens inteiras em mil classes, como “guarda-chuva”, “camiseta” e “lava-louças”.</span><span class="sxs-lookup"><span data-stu-id="616f6-143">Your image classification model reuses the [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), a popular image recognition model trained on the `ImageNet` dataset where the TensorFlow model tries to classify entire images into a thousand classes, like “Umbrella”, “Jersey”, and “Dishwasher”.</span></span>

<span data-ttu-id="616f6-144">O `Inception v3 model` pode ser classificado como uma [rede neural convolucional profunda](https://en.wikipedia.org/wiki/Convolutional_neural_network) e pode alcançar um desempenho razoável em tarefas de reconhecimento visual, combinando ou excedendo o desempenho humano em alguns domínios.</span><span class="sxs-lookup"><span data-stu-id="616f6-144">The `Inception v3 model` can be classified as a [deep convolutional neural network](https://en.wikipedia.org/wiki/Convolutional_neural_network) and can achieve reasonable performance on hard visual recognition tasks, matching or exceeding human performance in some domains.</span></span> <span data-ttu-id="616f6-145">O modelo/algoritmo foi desenvolvido por múltiplos pesquisadores e baseado no artigo original: ["Reformulação da arquitetura de concepção para pesquisa visual computacional" por Szegedy, et. Al.](https://arxiv.org/abs/1512.00567)</span><span class="sxs-lookup"><span data-stu-id="616f6-145">The model/algorithm was developed by multiple researchers and based on the original paper: ["Rethinking the Inception Architecture for Computer Vision” by Szegedy, et. al.](https://arxiv.org/abs/1512.00567)</span></span>

<span data-ttu-id="616f6-146">Como o `Inception model` já foi pré-treinado em milhares de imagens diferentes, ele contém os [recursos de imagem](https://en.wikipedia.org/wiki/Feature_(computer_vision)) necessários para a identificação da imagem.</span><span class="sxs-lookup"><span data-stu-id="616f6-146">Because the `Inception model` has already been pre trained on thousands of different images, it contains the [image features](https://en.wikipedia.org/wiki/Feature_(computer_vision)) needed for image identification.</span></span> <span data-ttu-id="616f6-147">As camadas de recurso de imagens inferiores reconhecem recursos simples (como bordas), e as camadas superiores reconhecem recursos mais complexos (como formas).</span><span class="sxs-lookup"><span data-stu-id="616f6-147">The lower image feature layers recognize simple features (such as edges) and the higher layers recognize more complex features (such as shapes).</span></span> <span data-ttu-id="616f6-148">A camada final é treinada contra um conjunto muito menor de dados porque você está começando com um modelo pré-treinado que já entende como classificar imagens.</span><span class="sxs-lookup"><span data-stu-id="616f6-148">The final layer is trained against a much smaller set of data because you're starting with a pre trained model that already understands how to classify images.</span></span> <span data-ttu-id="616f6-149">Como seu modelo permite classificar mais de duas categorias, este é um exemplo de um [classificador multiclasse](../resources/tasks.md#multiclass-classification).</span><span class="sxs-lookup"><span data-stu-id="616f6-149">As your model allows you to classify more than two categories, this is an example of a [multi-class classifier](../resources/tasks.md#multiclass-classification).</span></span> 

<span data-ttu-id="616f6-150">`TensorFlow` é um popular kit de ferramentas de aprendizado profundo e aprendizado de máquina que permite o treinamento de redes neurais profundas (e cálculos numéricos gerais) e é implementado como um `transformer` no ML.NET.</span><span class="sxs-lookup"><span data-stu-id="616f6-150">`TensorFlow` is a popular deep learning and machine learning toolkit that enables training deep neural networks (and general numeric computations), and is implemented as a `transformer` in ML.NET.</span></span> <span data-ttu-id="616f6-151">Para este tutorial, é usado para reutilizar o `Inception model`.</span><span class="sxs-lookup"><span data-stu-id="616f6-151">For this tutorial, it's used to reuse the `Inception model`.</span></span>

<span data-ttu-id="616f6-152">Conforme mostrado no diagrama a seguir, você adiciona uma referência aos pacotes ML.NET NuGet em seus aplicativos .NET Core ou .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="616f6-152">As shown in the following diagram, you add a reference to the ML.NET NuGet packages in your .NET Core or .NET Framework applications.</span></span> <span data-ttu-id="616f6-153">Nos bastidores, o ML.NET inclui e faz referência à biblioteca `TensorFlow` nativa que permite escrever código que carrega um arquivo de modelo `TensorFlow` existente e treinado para pontuação.</span><span class="sxs-lookup"><span data-stu-id="616f6-153">Under the covers, ML.NET includes and references the native `TensorFlow` library that allows you to write code that loads an existing trained `TensorFlow` model file for scoring.</span></span>  

![Diagrama de arco da transformação do TensorFlow do ML.NET](./media/image-classification/tensorflow-mlnet.png)

<span data-ttu-id="616f6-155">O `Inception model` é treinado para classificar imagens em mil categorias, mas é necessário classificar imagens em um conjunto de categorias menor e apenas nessas categorias.</span><span class="sxs-lookup"><span data-stu-id="616f6-155">The `Inception model` is trained to classify images into a thousand categories, but you need to classify images in a smaller category set, and only those categories.</span></span> <span data-ttu-id="616f6-156">Digite a parte `transfer` de `transfer learning`.</span><span class="sxs-lookup"><span data-stu-id="616f6-156">Enter the `transfer` part of `transfer learning`.</span></span> <span data-ttu-id="616f6-157">Você pode transferir a capacidade de `Inception model` de reconhecer e classificar imagens para as novas categorias limitadas do seu classificador de imagens personalizadas.</span><span class="sxs-lookup"><span data-stu-id="616f6-157">You can transfer the `Inception model`'s ability to recognize and classify images to the new limited categories of your custom image classifier.</span></span>  

 <span data-ttu-id="616f6-158">Você vai treinar novamente a camada final desse modelo usando um conjunto de três categorias:</span><span class="sxs-lookup"><span data-stu-id="616f6-158">You're going to retrain the final layer of that model using a set of three categories:</span></span>

* <span data-ttu-id="616f6-159">Alimentação</span><span class="sxs-lookup"><span data-stu-id="616f6-159">Food</span></span>
* <span data-ttu-id="616f6-160">Brinquedos</span><span class="sxs-lookup"><span data-stu-id="616f6-160">Toy</span></span>
* <span data-ttu-id="616f6-161">Dispositivos</span><span class="sxs-lookup"><span data-stu-id="616f6-161">Appliance</span></span>

<span data-ttu-id="616f6-162">Sua camada usa um [algoritmo de regressão logística multinomial](https://en.wikipedia.org/wiki/Multinomial_logistic_regression) para encontrar a categoria correta o mais rápido possível.</span><span class="sxs-lookup"><span data-stu-id="616f6-162">Your layer uses a [multinomial logistic regression algorithm](https://en.wikipedia.org/wiki/Multinomial_logistic_regression) to find the correct category as quickly as possible.</span></span> <span data-ttu-id="616f6-163">Esse algoritmo classifica usando probabilidades para determinar a resposta, dando um valor para a categoria correta e um valor zero para os outros.</span><span class="sxs-lookup"><span data-stu-id="616f6-163">This algorithm classifies using probabilities to determine the answer, giving a one value to the correct category and a zero value to the others.</span></span>  

### <a name="dataset"></a><span data-ttu-id="616f6-164">DataSet</span><span class="sxs-lookup"><span data-stu-id="616f6-164">DataSet</span></span>

<span data-ttu-id="616f6-165">Há duas fontes de dados: o arquivo `.tsv` e os arquivos de imagem.</span><span class="sxs-lookup"><span data-stu-id="616f6-165">There are two data sources: the `.tsv` file, and the image files.</span></span>  <span data-ttu-id="616f6-166">O arquivo `tags.tsv` contém duas colunas: a primeira é definida como `ImagePath` e a segunda é a `Label` correspondente à imagem.</span><span class="sxs-lookup"><span data-stu-id="616f6-166">The `tags.tsv` file contains two columns: the first one is defined as `ImagePath` and the second one is the `Label` corresponding to the image.</span></span> <span data-ttu-id="616f6-167">O arquivo de exemplo a seguir não possui uma linha de cabeçalho e tem a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="616f6-167">The following example file doesn't have a header row, and looks like this:</span></span>

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

<span data-ttu-id="616f6-168">As imagens de treinamento e teste estão localizadas nas pastas de recursos que você baixará em um arquivo zip.</span><span class="sxs-lookup"><span data-stu-id="616f6-168">The training and testing images are located in the assets folders that you'll download in a zip file.</span></span> <span data-ttu-id="616f6-169">Essas imagens pertencem ao Wikimedia Commons.</span><span class="sxs-lookup"><span data-stu-id="616f6-169">These images belong to Wikimedia Commons.</span></span>
> <span data-ttu-id="616f6-170">*[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), o repositório de mídia gratuito.*</span><span class="sxs-lookup"><span data-stu-id="616f6-170">*[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), the free media repository.*</span></span> <span data-ttu-id="616f6-171">Recuperado em 10:48, 17 de outubro de 2018 de:</span><span class="sxs-lookup"><span data-stu-id="616f6-171">Retrieved 10:48, October 17, 2018 from:</span></span>  
> https://commons.wikimedia.org/wiki/Pizza  
> https://commons.wikimedia.org/wiki/Toaster  
> https://commons.wikimedia.org/wiki/Teddy_bear  

## <a name="create-a-console-application"></a><span data-ttu-id="616f6-172">Criar um aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="616f6-172">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="616f6-173">Criar um projeto</span><span class="sxs-lookup"><span data-stu-id="616f6-173">Create a project</span></span>

1. <span data-ttu-id="616f6-174">Criar um **Aplicativo de Console .NET Core** chamado "TransferLearningTF".</span><span class="sxs-lookup"><span data-stu-id="616f6-174">Create a **.NET Core Console Application** called "TransferLearningTF".</span></span>

2. <span data-ttu-id="616f6-175">Instalar o **Pacote NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="616f6-175">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="616f6-176">No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="616f6-176">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="616f6-177">Escolha "nuget.org" como a fonte do pacote, selecione a guia Browse, procure por **Microsoft.ML**.</span><span class="sxs-lookup"><span data-stu-id="616f6-177">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**.</span></span> <span data-ttu-id="616f6-178">Clique na lista suspensa **Versão**, selecione o pacote **1.0.0** na lista e selecione o botão **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="616f6-178">Click on the **Version** drop-down, select the **1.0.0** package in the list, and select the **Install** button.</span></span> <span data-ttu-id="616f6-179">Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados.</span><span class="sxs-lookup"><span data-stu-id="616f6-179">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="616f6-180">Repita essas etapas para **Microsoft.ML.ImageAnalytics v1.0.0** e **Microsoft.ML.TensorFlow v0.12.0**.</span><span class="sxs-lookup"><span data-stu-id="616f6-180">Repeat these steps for **Microsoft.ML.ImageAnalytics v1.0.0** and **Microsoft.ML.TensorFlow v0.12.0**.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="616f6-181">Preparar seus dados</span><span class="sxs-lookup"><span data-stu-id="616f6-181">Prepare your data</span></span>

1. <span data-ttu-id="616f6-182">Baixe o [arquivo zip do diretório de materiais do projeto](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip) e descompacte.</span><span class="sxs-lookup"><span data-stu-id="616f6-182">Download [The project assets directory zip file](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip), and unzip.</span></span>

2. <span data-ttu-id="616f6-183">Copie o diretório`assets` no diretório do projeto *TransferLearningTF*.</span><span class="sxs-lookup"><span data-stu-id="616f6-183">Copy the `assets` directory into your *TransferLearningTF* project directory.</span></span> <span data-ttu-id="616f6-184">Este diretório e seus subdiretórios contêm os arquivos de dados e de suporte (exceto o modelo Concepção, que você irá baixar e adicionar na próxima etapa) necessários para este tutorial.</span><span class="sxs-lookup"><span data-stu-id="616f6-184">This directory and its subdirectories contain the data and support files (except for the Inception model, which you'll download and add in the next step) needed for this tutorial.</span></span>

3. <span data-ttu-id="616f6-185">Baixe o [modelo Concepção](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) e descompacte-o.</span><span class="sxs-lookup"><span data-stu-id="616f6-185">Download the [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), and unzip.</span></span>

4. <span data-ttu-id="616f6-186">Copie o conteúdo do diretório `inception5h` apenas descompactado em seu diretório de projeto *TransferLearningTF*`assets\inputs-train\inception`.</span><span class="sxs-lookup"><span data-stu-id="616f6-186">Copy the contents of the `inception5h` directory just unzipped into your *TransferLearningTF* project `assets\inputs-train\inception` directory.</span></span> <span data-ttu-id="616f6-187">Este diretório contém o modelo e os arquivos de suporte adicionais necessários para este tutorial, conforme mostrado na imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="616f6-187">This directory contains the model and additional support files needed for this tutorial, as shown in the following image:</span></span>

   ![Conteúdo do diretório de concepção](./media/image-classification/inception-files.png)

5. <span data-ttu-id="616f6-189">No Gerenciador de Soluções, clique com o botão direito do mouse em cada um dos arquivos no diretório e nos subdiretórios do ativo e selecione**Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="616f6-189">In Solution Explorer, right-click each of the files in the asset directory and subdirectories and select **Properties**.</span></span> <span data-ttu-id="616f6-190">Em **Avançado**, altere o valor de **Copiar para Diretório de Saída** para **Copiar se for mais novo**.</span><span class="sxs-lookup"><span data-stu-id="616f6-190">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="616f6-191">Criar classes e definir demarcadores</span><span class="sxs-lookup"><span data-stu-id="616f6-191">Create classes and define paths</span></span>

<span data-ttu-id="616f6-192">Adicione as seguintes instruções `using` adicionais ao início do arquivo *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="616f6-192">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddUsings)]

<span data-ttu-id="616f6-193">Crie campos globais para manter os caminhos para os vários ativos e variáveis globais para `LabelTokey`, `ImageReal` e `PredictedLabelValue`:</span><span class="sxs-lookup"><span data-stu-id="616f6-193">Create global fields to hold the paths to the various assets, and global variables for the `LabelTokey`,`ImageReal`, and  `PredictedLabelValue`:</span></span>

* <span data-ttu-id="616f6-194">`_assetsPath` tem o demarcador para os ativos.</span><span class="sxs-lookup"><span data-stu-id="616f6-194">`_assetsPath` has the path to the assets.</span></span>
* <span data-ttu-id="616f6-195">`_trainTagsTsv` tem o demarcador para o arquivo tsv de tags de dados de imagem de treinamento.</span><span class="sxs-lookup"><span data-stu-id="616f6-195">`_trainTagsTsv` has the path to the training image data tags tsv file.</span></span>
* <span data-ttu-id="616f6-196">`_predictTagsTsv` tem o demarcador para o arquivo tsv de tags de dados de imagem de previsão.</span><span class="sxs-lookup"><span data-stu-id="616f6-196">`_predictTagsTsv` has the path to the prediction image data tags tsv file.</span></span>
* <span data-ttu-id="616f6-197">`_trainImagesFolder` tem o demarcador para as imagens usadas para treinar o modelo.</span><span class="sxs-lookup"><span data-stu-id="616f6-197">`_trainImagesFolder` has the path to the images used to train the model.</span></span>
* <span data-ttu-id="616f6-198">`_predictImagesFolder` tem o demarcador para as imagens a serem classificadas pelo modelo treinado.</span><span class="sxs-lookup"><span data-stu-id="616f6-198">`_predictImagesFolder` has the path to the images to be classified by the trained model.</span></span>
* <span data-ttu-id="616f6-199">`_inceptionPb`tem o demarcador para o modelo Concepção pré-treinado para ser reutilizado para treinar seu modelo.</span><span class="sxs-lookup"><span data-stu-id="616f6-199">`_inceptionPb` has the path to the pre-trained Inception model to be reused to retrain your model.</span></span>
* <span data-ttu-id="616f6-200">`_inputImageClassifierZip` tem o demarcador de onde o modelo treinado é carregado.</span><span class="sxs-lookup"><span data-stu-id="616f6-200">`_inputImageClassifierZip` has the path where the trained model is loaded from.</span></span>
* <span data-ttu-id="616f6-201">`_outputImageClassifierZip` tem o demarcador em que o modelo treinado é salvo.</span><span class="sxs-lookup"><span data-stu-id="616f6-201">`_outputImageClassifierZip` has the path where the trained model is saved.</span></span>
* <span data-ttu-id="616f6-202">`LabelTokey` é o `Label` valor mapeado para uma chave.</span><span class="sxs-lookup"><span data-stu-id="616f6-202">`LabelTokey` is the `Label` value mapped to a key.</span></span>
* <span data-ttu-id="616f6-203">`ImageReal` é a coluna que contém o valor da imagem prevista.</span><span class="sxs-lookup"><span data-stu-id="616f6-203">`ImageReal`  is the column containing the predicted image value.</span></span>
* <span data-ttu-id="616f6-204">`PredictedLabelValue` é a coluna que contém o valor do rótulo previsto.</span><span class="sxs-lookup"><span data-stu-id="616f6-204">`PredictedLabelValue` is the column containing the predicted label value.</span></span>

<span data-ttu-id="616f6-205">Adicione o seguinte código à linha logo acima do método `Main` para especificar estes caminhos e as outras variáveis:</span><span class="sxs-lookup"><span data-stu-id="616f6-205">Add the following code to the line right above the `Main` method to specify those paths and the other variables:</span></span>

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareGlobalVariables)]

<span data-ttu-id="616f6-206">Crie algumas classes para os dados de entrada e as previsões.</span><span class="sxs-lookup"><span data-stu-id="616f6-206">Create some classes for your input data, and predictions.</span></span> <span data-ttu-id="616f6-207">Adicione uma nova classe ao seu projeto:</span><span class="sxs-lookup"><span data-stu-id="616f6-207">Add a new class to your project:</span></span>

1. <span data-ttu-id="616f6-208">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="616f6-208">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="616f6-209">Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *ImageData.cs*.</span><span class="sxs-lookup"><span data-stu-id="616f6-209">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *ImageData.cs*.</span></span> <span data-ttu-id="616f6-210">Em seguida, selecione o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="616f6-210">Then, select the **Add** button.</span></span>

    <span data-ttu-id="616f6-211">O arquivo *ImageData.cs* é aberto no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="616f6-211">The *ImageData.cs* file opens in the code editor.</span></span> <span data-ttu-id="616f6-212">Adicione a seguinte instrução `using` à parte superior do *ImageData.cs*:</span><span class="sxs-lookup"><span data-stu-id="616f6-212">Add the following `using` statement to the top of *ImageData.cs*:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/ImageData.cs#AddUsings)]

<span data-ttu-id="616f6-213">Remova a definição de classe existente e adicione o seguinte código para a classe `ImageData` do arquivo *ImageData.cs*:</span><span class="sxs-lookup"><span data-stu-id="616f6-213">Remove the existing class definition and add the following code for the `ImageData` class to the *ImageData.cs* file:</span></span>

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/TransferLearningTF/ImageData.cs#DeclareTypes)]

<span data-ttu-id="616f6-214">`ImageData` é a classe de conjunto de dados de entrada e tem os seguintes campos <xref:System.String>:</span><span class="sxs-lookup"><span data-stu-id="616f6-214">`ImageData` is the input image data class and has the following <xref:System.String> fields:</span></span>

* <span data-ttu-id="616f6-215">`ImagePath` contém o nome do arquivo de imagem.</span><span class="sxs-lookup"><span data-stu-id="616f6-215">`ImagePath` contains the image file name.</span></span>
* <span data-ttu-id="616f6-216">`Label` contém um valor para o rótulo da imagem.</span><span class="sxs-lookup"><span data-stu-id="616f6-216">`Label` contains a value for the image label.</span></span>

<span data-ttu-id="616f6-217">Adicione uma nova classe ao seu projeto para `ImagePrediction`:</span><span class="sxs-lookup"><span data-stu-id="616f6-217">Add a new class to your project for `ImagePrediction`:</span></span>

1. <span data-ttu-id="616f6-218">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="616f6-218">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="616f6-219">Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *ImagePrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="616f6-219">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *ImagePrediction.cs*.</span></span> <span data-ttu-id="616f6-220">Em seguida, selecione o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="616f6-220">Then, select the **Add** button.</span></span>

    <span data-ttu-id="616f6-221">O arquivo *ImagePrediction.cs* é aberto no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="616f6-221">The *ImagePrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="616f6-222">Remova as instruções `System.Collections.Generic` e `System.Text` `using` na parte superior do *ImagePrediction.cs*:</span><span class="sxs-lookup"><span data-stu-id="616f6-222">Remove both the `System.Collections.Generic` and the `System.Text` `using` statements at the top of *ImagePrediction.cs*:</span></span>

<span data-ttu-id="616f6-223">Remova a definição de classe existente e adicione o seguinte código, que tem a classe `ImagePrediction`, ao arquivo *ImagePrediction.cs*:</span><span class="sxs-lookup"><span data-stu-id="616f6-223">Remove the existing class definition and add the following code, which has the `ImagePrediction` class, to the *ImagePrediction.cs* file:</span></span>

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/ImagePrediction.cs#DeclareTypes)]

<span data-ttu-id="616f6-224">`ImagePrediction` é a classe de previsão de imagem e possui os seguintes campos:</span><span class="sxs-lookup"><span data-stu-id="616f6-224">`ImagePrediction` is the image prediction class and has the following fields:</span></span>

* <span data-ttu-id="616f6-225">`Score` contém a porcentagem de confiança para uma determinada classificação de imagem.</span><span class="sxs-lookup"><span data-stu-id="616f6-225">`Score` contains the confidence percentage for a given image classification.</span></span>
* <span data-ttu-id="616f6-226">`PredictedLabelValue` contém um valor para o rótulo de classificação de imagem previsto.</span><span class="sxs-lookup"><span data-stu-id="616f6-226">`PredictedLabelValue` contains a value for the predicted image classification label.</span></span>

<span data-ttu-id="616f6-227">`ImagePrediction` é a classe usada para previsão depois que o modelo foi treinado.</span><span class="sxs-lookup"><span data-stu-id="616f6-227">`ImagePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="616f6-228">Tem um `string` (`ImagePath`) para o demarcador da imagem.</span><span class="sxs-lookup"><span data-stu-id="616f6-228">It has a `string` (`ImagePath`) for the image path.</span></span> <span data-ttu-id="616f6-229">O `Label` é usado para reutilizar e treinar novamente o modelo.</span><span class="sxs-lookup"><span data-stu-id="616f6-229">The `Label` is used to reuse and retrain the model.</span></span> <span data-ttu-id="616f6-230">O `PredictedLabelValue` é usado durante a previsão e avaliação.</span><span class="sxs-lookup"><span data-stu-id="616f6-230">The `PredictedLabelValue` is used during prediction and evaluation.</span></span> <span data-ttu-id="616f6-231">Para avaliação, uma entrada com dados de treinamento, os valores previstos e o modelo são usados.</span><span class="sxs-lookup"><span data-stu-id="616f6-231">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="616f6-232">A [classe MLContext](xref:Microsoft.ML.MLContext) é um ponto de partida para todas as operações do ML.NET e a inicialização do `mlContext` cria um ambiente do ML.NET que pode ser compartilhado entre os objetos de fluxo de trabalho da criação de modelo.</span><span class="sxs-lookup"><span data-stu-id="616f6-232">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="616f6-233">Ele é semelhante, conceitualmente, a `DBContext` no Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="616f6-233">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="616f6-234">Inicializar variáveis em Main</span><span class="sxs-lookup"><span data-stu-id="616f6-234">Initialize variables in Main</span></span>

<span data-ttu-id="616f6-235">Inicialize a variável `mlContext` com uma nova instância de `MLContext`.</span><span class="sxs-lookup"><span data-stu-id="616f6-235">Initialize the `mlContext` variable with a new instance of `MLContext`.</span></span>  <span data-ttu-id="616f6-236">Substitua a linha `Console.WriteLine("Hello World!")` pelo seguinte código no método `Main`:</span><span class="sxs-lookup"><span data-stu-id="616f6-236">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CreateMLContext)]

### <a name="create-a-struct-for-default-parameters"></a><span data-ttu-id="616f6-237">Crie um struct para os parâmetros padrão</span><span class="sxs-lookup"><span data-stu-id="616f6-237">Create a struct for default parameters</span></span>

<span data-ttu-id="616f6-238">O modelo Concepção possui vários parâmetros padrão que você precisa verificar.</span><span class="sxs-lookup"><span data-stu-id="616f6-238">The Inception model has several default parameters you need to pass in.</span></span> <span data-ttu-id="616f6-239">Crie um struct para mapear os valores de parâmetros padrão para nomes amigáveis com o seguinte código, logo após o método `Main()`:</span><span class="sxs-lookup"><span data-stu-id="616f6-239">Create a struct to map the default parameter values to friendly names with the following code, just after the `Main()` method:</span></span>

[!code-csharp[InceptionSettings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#InceptionSettings)]

### <a name="create-a-display-utility-method"></a><span data-ttu-id="616f6-240">Criar um método de utilitário de exibição</span><span class="sxs-lookup"><span data-stu-id="616f6-240">Create a display utility method</span></span>

<span data-ttu-id="616f6-241">Uma vez que você exibirá os dados de imagem e as previsões relacionadas mais de uma vez, crie um método de utilitário de exibição para lidar com a exibição dos resultados de imagem e previsão.</span><span class="sxs-lookup"><span data-stu-id="616f6-241">Since you'll display the image data and the related predictions more than once, create a display utility method to handle displaying the image and prediction results.</span></span>

<span data-ttu-id="616f6-242">O método `DisplayResults()` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="616f6-242">The `DisplayResults()` method executes the following tasks:</span></span>

* <span data-ttu-id="616f6-243">Exibe os resultados previstos.</span><span class="sxs-lookup"><span data-stu-id="616f6-243">Displays the predicted results.</span></span>

<span data-ttu-id="616f6-244">Crie o método `DisplayResults()`, logo após o struct `InceptionSettings`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="616f6-244">Create the `DisplayResults()` method, just after the `InceptionSettings` struct, using the following code:</span></span>

```csharp
private static void DisplayResults(IEnumerable<ImagePrediction> imagePredictionData)
{

}
```

<span data-ttu-id="616f6-245">O método `Transform()` preencheu `ImagePath` no `ImagePrediction` juntamente com os campos previstos.</span><span class="sxs-lookup"><span data-stu-id="616f6-245">The `Transform()` method populated `ImagePath` in `ImagePrediction` along with the predicted fields.</span></span> <span data-ttu-id="616f6-246">Conforme o processo do ML.NET progride, cada componente adiciona colunas e isso facilita a exibição dos resultados:</span><span class="sxs-lookup"><span data-stu-id="616f6-246">As the ML.NET process progresses, each component adds columns, and this makes it easy to display the results:</span></span>

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPredictions)]

<span data-ttu-id="616f6-247">Você chamará o método `DisplayResults()` nos dois métodos de classificação de imagem.</span><span class="sxs-lookup"><span data-stu-id="616f6-247">You'll call the `DisplayResults()` method in the two image classification methods.</span></span>

### <a name="create-a-tsv-file-utility-method"></a><span data-ttu-id="616f6-248">Criar um método de utilitário de arquivo .tsv</span><span class="sxs-lookup"><span data-stu-id="616f6-248">Create a .tsv file utility method</span></span>

<span data-ttu-id="616f6-249">O método `ReadFromTsv()` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="616f6-249">The `ReadFromTsv()` method executes the following tasks:</span></span>

* <span data-ttu-id="616f6-250">Lê o arquivo de dados de imagem `tags.tsv`.</span><span class="sxs-lookup"><span data-stu-id="616f6-250">Reads the image data `tags.tsv` file.</span></span>
* <span data-ttu-id="616f6-251">Adiciona o demarcador do arquivo ao nome do arquivo de imagem.</span><span class="sxs-lookup"><span data-stu-id="616f6-251">Adds the file path to the image file name.</span></span>
* <span data-ttu-id="616f6-252">Carrega os dados do arquivo em um objeto IEnumerable`ImageData`.</span><span class="sxs-lookup"><span data-stu-id="616f6-252">Loads the file data into an IEnumerable`ImageData` object.</span></span>

<span data-ttu-id="616f6-253">Crie o método `ReadFromTsv()`, logo após o método `PairAndDisplayResults()`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="616f6-253">Create the `ReadFromTsv()` method, just after the `PairAndDisplayResults()` method, using the following code:</span></span>

```csharp
public static IEnumerable<ImageData> ReadFromTsv(string file, string folder)
{

}
```

<span data-ttu-id="616f6-254">O código a seguir analisa o arquivo `tags.tsv` para adicionar o demarcador do arquivo ao nome do arquivo de imagem para a propriedade `ImagePath` e o carregá-lo e o `Label` em um objeto `ImageData`.</span><span class="sxs-lookup"><span data-stu-id="616f6-254">The following code parses through the `tags.tsv` file to add the file path to the image file name for the `ImagePath` property and load it and the `Label` into an `ImageData` object.</span></span> <span data-ttu-id="616f6-255">Adicione-o como a primeira linha do método `ReadFromTsv()`.</span><span class="sxs-lookup"><span data-stu-id="616f6-255">Add it as the first line of the `ReadFromTsv()` method.</span></span>  <span data-ttu-id="616f6-256">Você precisa do demarcador completo do arquivo para exibir os resultados da previsão.</span><span class="sxs-lookup"><span data-stu-id="616f6-256">You need the fully qualified file path to display the prediction results.</span></span>

[!code-csharp[ReadFromTsv](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReadFromTsv)]
<span data-ttu-id="616f6-257">Há três conceitos principais no ML.NET: [Dados](../resources/glossary.md#data), [Transformadores](../resources/glossary.md#transformer) e [Avaliadores](../resources/glossary.md#estimator).</span><span class="sxs-lookup"><span data-stu-id="616f6-257">There are three major concepts in ML.NET: [Data](../resources/glossary.md#data), [Transformers](../resources/glossary.md#transformer), and [Estimators](../resources/glossary.md#estimator).</span></span>

## <a name="reuse-and-tune-pre-trained-model"></a><span data-ttu-id="616f6-258">Reutilizar e ajustar um modelo pré-treinado</span><span class="sxs-lookup"><span data-stu-id="616f6-258">Reuse and tune pre-trained model</span></span>

<span data-ttu-id="616f6-259">Adicione a seguinte chamada ao método `ReuseAndTuneInceptionModel()` como a próxima linha de código no método `Main()`:</span><span class="sxs-lookup"><span data-stu-id="616f6-259">Add the following call to the `ReuseAndTuneInceptionModel()`method as the next line of code in the `Main()` method:</span></span>

[!code-csharp[CallReuseAndTuneInceptionModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallReuseAndTuneInceptionModel)]

<span data-ttu-id="616f6-260">O método `ReuseAndTuneInceptionModel()` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="616f6-260">The `ReuseAndTuneInceptionModel()` method executes the following tasks:</span></span>

* <span data-ttu-id="616f6-261">Carrega os dados.</span><span class="sxs-lookup"><span data-stu-id="616f6-261">Loads the data</span></span>
* <span data-ttu-id="616f6-262">Extrai e transforma os dados.</span><span class="sxs-lookup"><span data-stu-id="616f6-262">Extracts and transforms the data.</span></span>
* <span data-ttu-id="616f6-263">Pontua o modelo do TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="616f6-263">Scores the TensorFlow model.</span></span>
* <span data-ttu-id="616f6-264">Ajusta (readapta) o modelo.</span><span class="sxs-lookup"><span data-stu-id="616f6-264">Tunes (retrains) the model.</span></span>
* <span data-ttu-id="616f6-265">Exibe os resultados do modelo.</span><span class="sxs-lookup"><span data-stu-id="616f6-265">Displays model results.</span></span>
* <span data-ttu-id="616f6-266">Avalia o modelo.</span><span class="sxs-lookup"><span data-stu-id="616f6-266">Evaluates the model.</span></span>
* <span data-ttu-id="616f6-267">Retorna o modelo.</span><span class="sxs-lookup"><span data-stu-id="616f6-267">Returns the model.</span></span>

<span data-ttu-id="616f6-268">Crie o método `ReuseAndTuneInceptionModel()` logo após o struct `InceptionSettings` e antes do método `DisplayResults()`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="616f6-268">Create the `ReuseAndTuneInceptionModel()` method, just after the `InceptionSettings` struct and just before the `DisplayResults()` method, using the following code:</span></span>

```csharp
public static ITransformer ReuseAndTuneInceptionModel(MLContext mlContext, string dataLocation, string imagesFolder, string inputModelLocation, string outputModelLocation)
{

}
```

### <a name="load-the-data"></a><span data-ttu-id="616f6-269">Carregar os dados</span><span class="sxs-lookup"><span data-stu-id="616f6-269">Load the data</span></span>

<span data-ttu-id="616f6-270">Os dados do ML.NET são representados como uma [classe IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="616f6-270">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="616f6-271">`IDataView` é uma maneira flexível e eficiente de descrever dados tabulares (numéricos e texto).</span><span class="sxs-lookup"><span data-stu-id="616f6-271">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="616f6-272">Os dados podem ser carregados de um arquivo de texto ou em tempo real (por exemplo, banco de dados SQL ou arquivos de log) para um objeto `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="616f6-272">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

<span data-ttu-id="616f6-273">Carregue os dados usando o wrapper `MLContext.Data.LoadFromTextFile`.</span><span class="sxs-lookup"><span data-stu-id="616f6-273">Load the data using the `MLContext.Data.LoadFromTextFile` wrapper.</span></span> <span data-ttu-id="616f6-274">Adicione o seguinte código ao método `ReuseAndTuneInceptionModel()` como a linha seguinte:</span><span class="sxs-lookup"><span data-stu-id="616f6-274">Add the following code as the next line in the `ReuseAndTuneInceptionModel()` method:</span></span>

[!code-csharp[LoadData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadData "Load the data")]

### <a name="extract-features-and-transform-the-data"></a><span data-ttu-id="616f6-275">Extrair recursos e transformar os dados</span><span class="sxs-lookup"><span data-stu-id="616f6-275">Extract Features and transform the data</span></span>

<span data-ttu-id="616f6-276">O pré-processamento e a limpeza de dados são tarefas importantes que ocorrem antes de um conjunto de dados ser usado efetivamente para o aprendizado de máquina.</span><span class="sxs-lookup"><span data-stu-id="616f6-276">Pre-processing and cleaning data are important tasks that occur before a dataset is used effectively for machine learning.</span></span>  <span data-ttu-id="616f6-277">Usar dados sem essas tarefas de modelagem pode produzir resultados enganosos.</span><span class="sxs-lookup"><span data-stu-id="616f6-277">Using data without these modeling tasks can produce misleading results.</span></span>

<span data-ttu-id="616f6-278">Algoritmos de aprendizado de máquina entendem [dados caracterizados](../resources/glossary.md#feature), e ao lidar com redes neurais profundas você deve adaptar as imagens ao formato esperado pela rede.</span><span class="sxs-lookup"><span data-stu-id="616f6-278">Machine learning algorithms understand [featurized](../resources/glossary.md#feature) data, and when dealing with deep neural networks you must adapt the images to the format expected by the network.</span></span> <span data-ttu-id="616f6-279">Esse formato é um [vetor numérico](../resources/glossary.md#numerical-feature-vector).</span><span class="sxs-lookup"><span data-stu-id="616f6-279">That format is a [numeric vector](../resources/glossary.md#numerical-feature-vector).</span></span>

<span data-ttu-id="616f6-280">Após o treinamento e a avaliação, faça a previsão com os valores da coluna **Rótulo**.</span><span class="sxs-lookup"><span data-stu-id="616f6-280">After training and evaluation, predict with the **Label** column values.</span></span> <span data-ttu-id="616f6-281">Ao usar um modelo pré-treinado, mapeie os campos para o novo modelo com o método [MapValueToKey ()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A).</span><span class="sxs-lookup"><span data-stu-id="616f6-281">As you're using a pre-trained model, map fields to the new model with the [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) method.</span></span> <span data-ttu-id="616f6-282">Este método transforma a coluna `Label` em um tipo de chave numérica (`LabelTokey`) e a adiciona como nova coluna do conjunto de dados:  Dê um nome a este `estimator` porque você também adicionará o treinador a ele.</span><span class="sxs-lookup"><span data-stu-id="616f6-282">This method transforms the `Label` into a numeric key type (`LabelTokey`) column and add it as new dataset column:  Name this `estimator` as you'll also add the trainer to it.</span></span> <span data-ttu-id="616f6-283">Adicione a seguinte linha de código:</span><span class="sxs-lookup"><span data-stu-id="616f6-283">Add the next line of code:</span></span>

[!code-csharp[MapValueToKey1](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey1)]

<span data-ttu-id="616f6-284">O seu estimador de processamento de imagens usa recursos de recursos para extração de recursos pré-treinados [Deep Neural Network (DNN)](https://en.wikipedia.org/wiki/Deep_learning#Deep_neural_networks).</span><span class="sxs-lookup"><span data-stu-id="616f6-284">Your image processing estimator uses pre-trained [Deep Neural Network(DNN)](https://en.wikipedia.org/wiki/Deep_learning#Deep_neural_networks) featurizers for feature extraction.</span></span> <span data-ttu-id="616f6-285">Ao lidar com redes neurais profundas, você adapta as imagens ao formato de rede esperado.</span><span class="sxs-lookup"><span data-stu-id="616f6-285">When dealing with deep neural networks, you  adapt the images to the expected network format.</span></span> <span data-ttu-id="616f6-286">Essa é a razão pela qual você usa várias transformações de imagem para obter os dados da imagem no formato esperado do modelo:</span><span class="sxs-lookup"><span data-stu-id="616f6-286">This is the reason you use several image transforms to get the image data into the model's expected form:</span></span>

1. <span data-ttu-id="616f6-287">As imagens de transformação `LoadImages` são carregadas na memória como um tipo de bitmap.</span><span class="sxs-lookup"><span data-stu-id="616f6-287">The `LoadImages`transform images are loaded in memory as a Bitmap type.</span></span>
2. <span data-ttu-id="616f6-288">A transformação `ResizeImages` redimensiona as imagens porque o modelo pré-treinado tem uma largura e altura de imagem de entrada definidas.</span><span class="sxs-lookup"><span data-stu-id="616f6-288">The `ResizeImages` transform resizes the images as the pre-trained model has a defined input image width and height.</span></span>
3. <span data-ttu-id="616f6-289">A transformação `ExtractPixels` extrai os pixels das imagens de entrada e os converte em um vetor numérico.</span><span class="sxs-lookup"><span data-stu-id="616f6-289">The `ExtractPixels` transform extracts the pixels from the input images and converts them into a numeric vector.</span></span>

<span data-ttu-id="616f6-290">Adicione essas transformações de imagem como as próximas linhas de código:</span><span class="sxs-lookup"><span data-stu-id="616f6-290">Add these image transforms as the next lines of code:</span></span>

[!code-csharp[ImageTransforms](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ImageTransforms)]

<span data-ttu-id="616f6-291">O `LoadTensorFlowModel` é um método de conveniência que permite que o modelo `TensorFlow` seja carregado uma vez e então cria `TensorFlowEstimator` usando `ScoreTensorFlowModel`.</span><span class="sxs-lookup"><span data-stu-id="616f6-291">The `LoadTensorFlowModel` is a convenience method that allows the `TensorFlow` model to be loaded once and then creates the `TensorFlowEstimator` using `ScoreTensorFlowModel`.</span></span> <span data-ttu-id="616f6-292">O `ScoreTensorFlowModel` extrai as saídas especificadas (os recursos da imagem do `Inception model``softmax2_pre_activation`) e marca um conjunto de dados usando o model o`TensorFlow` pré-treinado.</span><span class="sxs-lookup"><span data-stu-id="616f6-292">The `ScoreTensorFlowModel` extracts specified outputs (the `Inception model`'s image features `softmax2_pre_activation`), and scores a dataset using the pre-trained `TensorFlow` model.</span></span>

<span data-ttu-id="616f6-293">`softmax2_pre_activation` auxilia o modelo a determinar a qual classe as imagens pertencem.</span><span class="sxs-lookup"><span data-stu-id="616f6-293">`softmax2_pre_activation` assists the model with determining which class the images belongs to.</span></span> <span data-ttu-id="616f6-294">`softmax2_pre_activation` retorna uma probabilidade para cada uma das categorias para uma imagem, e todas essas probabilidades devem somar 1.</span><span class="sxs-lookup"><span data-stu-id="616f6-294">`softmax2_pre_activation` returns a probability for each of the categories for an image, and all of those probabilities must add up to 1.</span></span> <span data-ttu-id="616f6-295">Ele pressupõe que uma imagem pertencerá a apenas uma categoria, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="616f6-295">It assumes that an image will belong to only one category, as shown in the following example:</span></span>

| <span data-ttu-id="616f6-296">Classe</span><span class="sxs-lookup"><span data-stu-id="616f6-296">Class</span></span>         | <span data-ttu-id="616f6-297">Probabilidade</span><span class="sxs-lookup"><span data-stu-id="616f6-297">Probability</span></span>   |
| ------------- | ------------- |
| `Food`        |  <span data-ttu-id="616f6-298">0.001</span><span class="sxs-lookup"><span data-stu-id="616f6-298">0.001</span></span>        |
| `Toy`         |  <span data-ttu-id="616f6-299">0.95</span><span class="sxs-lookup"><span data-stu-id="616f6-299">0.95</span></span>         |
| `Appliance`   |  <span data-ttu-id="616f6-300">0.06</span><span class="sxs-lookup"><span data-stu-id="616f6-300">0.06</span></span>         |

<span data-ttu-id="616f6-301">Adicione `TensorFlowTransform` ao `estimator` com a seguinte linha de código:</span><span class="sxs-lookup"><span data-stu-id="616f6-301">Append the `TensorFlowTransform` to the `estimator` with the following line of code:</span></span>

[!code-csharp[ScoreTensorFlowModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ScoreTensorFlowModel)]

### <a name="choose-a-training-algorithm"></a><span data-ttu-id="616f6-302">Escolher um algoritmo de treinamento</span><span class="sxs-lookup"><span data-stu-id="616f6-302">Choose a training algorithm</span></span>

<span data-ttu-id="616f6-303">Para adicionar o algoritmo de treinamento, chame o método wrapper `mlContext.MulticlassClassification.Trainers.LbfgsMaximumEntropy()`.</span><span class="sxs-lookup"><span data-stu-id="616f6-303">To add the training algorithm, call the `mlContext.MulticlassClassification.Trainers.LbfgsMaximumEntropy()` wrapper method.</span></span>  <span data-ttu-id="616f6-304">O [LbfgsMaximumEntropy](xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer) é anexado ao `estimator` e aceita os recursos da imagem Concepção (`softmax2_pre_activation`) e os parâmetros de entrada `Label` para aprender com os dados históricos.</span><span class="sxs-lookup"><span data-stu-id="616f6-304">The [LbfgsMaximumEntropy](xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer) is appended to the `estimator` and accepts the Inception image features (`softmax2_pre_activation`) and the `Label` input parameters to learn from the historic data.</span></span>  <span data-ttu-id="616f6-305">Adicione o treinador com o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="616f6-305">Add the trainer with the following code:</span></span>

[!code-csharp[AddTrainer](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddTrainer)]

<span data-ttu-id="616f6-306">Você também precisa mapear o `predictedlabel` para o `predictedlabelvalue`:</span><span class="sxs-lookup"><span data-stu-id="616f6-306">You also need to map the `predictedlabel` to the `predictedlabelvalue`:</span></span>

[!code-csharp[MapValueToKey2](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey2)]

<span data-ttu-id="616f6-307">O método `Fit()` treina o modelo transformando o conjunto de dados e aplicando o treinamento.</span><span class="sxs-lookup"><span data-stu-id="616f6-307">The `Fit()` method trains your model by transforming the dataset and applying the training.</span></span> <span data-ttu-id="616f6-308">Ajuste o modelo ao conjunto de dados de treinamento e retorne o modelo treinado adicionando o seguinte como a próxima linha de código no método `ReuseAndTuneInceptionModel()`:</span><span class="sxs-lookup"><span data-stu-id="616f6-308">Fit the model to the training dataset and return the trained model by adding the following as the next line of code in the `ReuseAndTuneInceptionModel()` method:</span></span>

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TrainModel)]

<span data-ttu-id="616f6-309">O método [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) faz previsões para várias linhas de entrada fornecidas de um conjunto de dados de teste.</span><span class="sxs-lookup"><span data-stu-id="616f6-309">The [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method makes predictions for multiple provided input rows of a test dataset.</span></span>  <span data-ttu-id="616f6-310">Transforme os dados `Training` adicionando o seguinte código a `ReuseAndTuneInceptionModel()`:</span><span class="sxs-lookup"><span data-stu-id="616f6-310">Transform the `Training` data by adding the following code to `ReuseAndTuneInceptionModel()`:</span></span>

[!code-csharp[TransformData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TransformData)]

<span data-ttu-id="616f6-311">Converta seus dados de imagem e previsão `DataViews` em `IEnumerables` fortemente tipados para emparelhar para exibição mais fácil.</span><span class="sxs-lookup"><span data-stu-id="616f6-311">Convert your image data and prediction `DataViews` into strongly-typed `IEnumerables` to pair for easier display.</span></span> <span data-ttu-id="616f6-312">Use o método `MLContext.CreateEnumerable()` para fazer isso, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="616f6-312">Use the `MLContext.CreateEnumerable()` method to do that, using the following code:</span></span>

[!code-csharp[EnumerateDataViews](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#EnumerateDataViews)]

<span data-ttu-id="616f6-313">Chame o método `DisplayResults()` para exibir seus dados e previsões como a próxima linha no método `ReuseAndTuneInceptionModel()`:</span><span class="sxs-lookup"><span data-stu-id="616f6-313">Call the `DisplayResults()` method to display your data and predictions as the next line in the `ReuseAndTuneInceptionModel()` method:</span></span>

[!code-csharp[CallDisplayResults1](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallDisplayResults1)]

<span data-ttu-id="616f6-314">Depois de determinar a previsão, o método [Evaluate ()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A):</span><span class="sxs-lookup"><span data-stu-id="616f6-314">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) method:</span></span>

* <span data-ttu-id="616f6-315">Avalia o modelo (compara os valores previstos com o conjunto de dados real `Labels`).</span><span class="sxs-lookup"><span data-stu-id="616f6-315">Assesses the model (compares the predicted values with the actual dataset `Labels`).</span></span>

* <span data-ttu-id="616f6-316">Retorna as métricas de desempenho do modelo.</span><span class="sxs-lookup"><span data-stu-id="616f6-316">Returns the model performance metrics.</span></span>

<span data-ttu-id="616f6-317">Adicione o seguinte código ao método `ReuseAndTuneInceptionModel()` como a linha seguinte:</span><span class="sxs-lookup"><span data-stu-id="616f6-317">Add the following code to the `ReuseAndTuneInceptionModel()` method as the next line:</span></span>

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Evaluate)]

<span data-ttu-id="616f6-318">As seguintes métricas são avaliadas para classificação de imagem:</span><span class="sxs-lookup"><span data-stu-id="616f6-318">The following metrics are evaluated for image classification:</span></span>

* <span data-ttu-id="616f6-319">`Log-loss` - confira [Perda de log](../resources/glossary.md#log-loss).</span><span class="sxs-lookup"><span data-stu-id="616f6-319">`Log-loss` - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="616f6-320">Convém que a Perda de log seja tão próxima de zero quanto possível.</span><span class="sxs-lookup"><span data-stu-id="616f6-320">You want Log-loss to be as close to zero as possible.</span></span>

* <span data-ttu-id="616f6-321">`Per class Log-loss`.</span><span class="sxs-lookup"><span data-stu-id="616f6-321">`Per class Log-loss`.</span></span> <span data-ttu-id="616f6-322">Convém que a Perda de log por classe seja tão próxima de zero quanto possível.</span><span class="sxs-lookup"><span data-stu-id="616f6-322">You want per class Log-loss to be as close to zero as possible.</span></span>

<span data-ttu-id="616f6-323">Use o código a seguir para exibir as métricas, compartilhar os resultados e, em seguida, agir com relação a eles:</span><span class="sxs-lookup"><span data-stu-id="616f6-323">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayMetrics)]

 <span data-ttu-id="616f6-324">Adicione o seguinte código para retornar o modelo treinado como a próxima linha:</span><span class="sxs-lookup"><span data-stu-id="616f6-324">Add the following code to return the trained model as the next line:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReturnModel)]

## <a name="classify-images-with-a-loaded-model"></a><span data-ttu-id="616f6-325">Classificar imagens com um modelo carregado</span><span class="sxs-lookup"><span data-stu-id="616f6-325">Classify images with a loaded model</span></span>

<span data-ttu-id="616f6-326">Adicione a seguinte chamada ao método `ClassifyImages()` como a próxima linha de código no método `Main`:</span><span class="sxs-lookup"><span data-stu-id="616f6-326">Add the following call to the `ClassifyImages()` method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallClassifyImages](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifyImages)]

<span data-ttu-id="616f6-327">O método `ClassifyImages()` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="616f6-327">The `ClassifyImages()` method executes the following tasks:</span></span>

* <span data-ttu-id="616f6-328">Lê o arquivo .TSV em `IEnumerable`.</span><span class="sxs-lookup"><span data-stu-id="616f6-328">Reads .TSV file into `IEnumerable`.</span></span>
* <span data-ttu-id="616f6-329">Prevê as classificações de imagens com base nos dados de teste.</span><span class="sxs-lookup"><span data-stu-id="616f6-329">Predicts image classifications based on test data.</span></span>

<span data-ttu-id="616f6-330">Crie o método `ClassifyImages()` logo após o método `ReuseAndTuneInceptionModel()` (e antes do método `PairAndDisplayResults()`) usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="616f6-330">Create the `ClassifyImages()` method, just after the `ReuseAndTuneInceptionModel()` method and just before the `PairAndDisplayResults()` method, using the following code:</span></span>

```csharp
public static void ClassifyImages(MLContext mlContext, string dataLocation, string imagesFolder, string outputModelLocation, ITransformer model)
{

}
```

<span data-ttu-id="616f6-331">Primeiro, chame o método `ReadFromTsv()` para criar uma classe `IEnumerable<ImageData>` que contenha o caminho totalmente qualificado para cada `ImagePath`.</span><span class="sxs-lookup"><span data-stu-id="616f6-331">First, call the `ReadFromTsv()` method to create an `IEnumerable<ImageData>` class that contains the fully qualified path for each `ImagePath`.</span></span> <span data-ttu-id="616f6-332">Você precisa desse caminho de arquivo para parear seus dados e resultados de previsão.</span><span class="sxs-lookup"><span data-stu-id="616f6-332">You need that file path to pair your data and prediction results.</span></span> <span data-ttu-id="616f6-333">Você também precisa converter a classe `IEnumerable<ImageData>` para uma `IDataView` que você usará para fazer a previsão.</span><span class="sxs-lookup"><span data-stu-id="616f6-333">You also need to convert the `IEnumerable<ImageData>` class to an `IDataView` that you will use to predict.</span></span> <span data-ttu-id="616f6-334">Adicione o seguinte código como as próximas duas linhas no método `ClassifyImages()`:</span><span class="sxs-lookup"><span data-stu-id="616f6-334">Add the following code as the next two lines in the `ClassifyImages()` method:</span></span>

[!code-csharp[CallReadFromTSV](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallReadFromTSV)]

<span data-ttu-id="616f6-335">Como você fez anteriormente com os dados da imagem de treinamento, preveja a categoria dos dados da imagem de teste usando o método [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) do modelo passado.</span><span class="sxs-lookup"><span data-stu-id="616f6-335">As you did previously with the training image data, predict the category of the test image data using the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method of the model passed in.</span></span> <span data-ttu-id="616f6-336">Adicione o seguinte código ao método `ClassifyImages()` para as previsões e converta `predictions``IDataView` em um `IEnumerable` para parear e exibir:</span><span class="sxs-lookup"><span data-stu-id="616f6-336">Add the following code to the `ClassifyImages()` method for the predictions and to convert the `predictions` `IDataView` into an `IEnumerable` for pairing and display:</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Predict)]

<span data-ttu-id="616f6-337">Para parear e exibir os dados e as previsões da sua imagem de teste, adicione o código a seguir para chamar o método `DisplayResults()` criado anteriormente como a próxima linha no método `ClassifyImages()`:</span><span class="sxs-lookup"><span data-stu-id="616f6-337">To pair and display your test image data and predictions, add the following code to call the `DisplayResults()` method previously created as the next line in the `ClassifyImages()` method:</span></span>

[!code-csharp[CallDisplayResults2](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallDisplayResults2)]

## <a name="classify-a-single-image-with-a-loaded-model"></a><span data-ttu-id="616f6-338">Classifique uma única imagem com um modelo carregado</span><span class="sxs-lookup"><span data-stu-id="616f6-338">Classify a single image with a loaded model</span></span>

<span data-ttu-id="616f6-339">Adicione a seguinte chamada ao método `ClassifySingleImage()` como a próxima linha de código no método `Main`:</span><span class="sxs-lookup"><span data-stu-id="616f6-339">Add the following call to the `ClassifySingleImage()` method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallClassifySingleImage](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifySingleImage)]

<span data-ttu-id="616f6-340">O método `ClassifySingleImage()` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="616f6-340">The `ClassifySingleImage()` method executes the following tasks:</span></span>

* <span data-ttu-id="616f6-341">Carrega uma instância `ImageData`.</span><span class="sxs-lookup"><span data-stu-id="616f6-341">Loads an `ImageData` instance.</span></span>
* <span data-ttu-id="616f6-342">Prevê a classificação de imagens com base nos dados de teste.</span><span class="sxs-lookup"><span data-stu-id="616f6-342">Predicts image classification based on test data.</span></span>

<span data-ttu-id="616f6-343">Crie o método `ClassifySingleImage()` logo após o método `ClassifyImages()` (e antes do método `PairAndDisplayResults()`) usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="616f6-343">Create the `ClassifySingleImage()` method, just after the `ClassifyImages()` method and just before the `PairAndDisplayResults()` method, using the following code:</span></span>

```csharp
public static void ClassifySingleImage(MLContext mlContext, string imagePath, string outputModelLocation, ITransformer model)
{

}
```

<span data-ttu-id="616f6-344">Primeiro, crie uma classe `ImageData` que contenha o caminho totalmente qualificado e o nome do arquivo de imagem para o único `ImagePath`.</span><span class="sxs-lookup"><span data-stu-id="616f6-344">First, create an `ImageData` class that contains the fully qualified path and image file name for the single `ImagePath`.</span></span> <span data-ttu-id="616f6-345">Adicione o seguinte código como as próximas linhas no método `ClassifySingleImage()`:</span><span class="sxs-lookup"><span data-stu-id="616f6-345">Add the following code as the next  lines in the `ClassifySingleImage()` method:</span></span>

[!code-csharp[LoadImageData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadImageData)]

<span data-ttu-id="616f6-346">A classe [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) é uma API de conveniência que executa uma previsão em uma única instância de dados.</span><span class="sxs-lookup"><span data-stu-id="616f6-346">The [PredictionEngine class](xref:Microsoft.ML.PredictionEngine%602) is a convenience API that performs a prediction on a single instance of data.</span></span> <span data-ttu-id="616f6-347">A função [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) faz uma previsão sobre uma única coluna de dados.</span><span class="sxs-lookup"><span data-stu-id="616f6-347">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single column of data.</span></span> <span data-ttu-id="616f6-348">Passe `imageData` para `PredictionEngine` para prever a categoria da imagem adicionando o seguinte código a `ClassifySingleImage()`:</span><span class="sxs-lookup"><span data-stu-id="616f6-348">Pass `imageData` to the `PredictionEngine` to predict the image category by adding the following code to `ClassifySingleImage()`:</span></span>

[!code-csharp[PredictSingle](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#PredictSingle)]

<span data-ttu-id="616f6-349">Exiba o resultado da previsão como a próxima linha de código no método `ClassifySingleImage()`:</span><span class="sxs-lookup"><span data-stu-id="616f6-349">Display the prediction result as the next line of code in the `ClassifySingleImage()` method:</span></span>

[!code-csharp[DisplayPrediction](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPrediction)]

## <a name="results"></a><span data-ttu-id="616f6-350">Resultados</span><span class="sxs-lookup"><span data-stu-id="616f6-350">Results</span></span>

<span data-ttu-id="616f6-351">Depois de seguir as etapas anteriores, execute o aplicativo de console (Ctrl+F5).</span><span class="sxs-lookup"><span data-stu-id="616f6-351">After following the previous steps, run your console app (Ctrl + F5).</span></span> <span data-ttu-id="616f6-352">O resultado deverá ser semelhante à seguinte saída.</span><span class="sxs-lookup"><span data-stu-id="616f6-352">Your results should be similar to the following output.</span></span>  <span data-ttu-id="616f6-353">Você poderá ver avisos ou mensagens de processamento, mas essas mensagens foram removidas dos resultados a seguir para maior clareza.</span><span class="sxs-lookup"><span data-stu-id="616f6-353">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

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
=============== Making classifications ===============
Image: broccoli.png predicted as: food with score: 0.905548
Image: pizza3.jpg predicted as: food with score: 0.9709008
Image: teddy6.jpg predicted as: toy with score: 0.9750155
=============== Making single image classification ===============
Image: toaster3.jpg predicted as: appliance with score: 0.9625379

C:\Program Files\dotnet\dotnet.exe (process 4304) exited with code 0.
Press any key to close this window . . .
```

<span data-ttu-id="616f6-354">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="616f6-354">Congratulations!</span></span> <span data-ttu-id="616f6-355">Agora você criou com sucesso um modelo de aprendizado de máquina para classificação de imagem reutilizando um modelo `TensorFlow` pré-treinado no ML.NET.</span><span class="sxs-lookup"><span data-stu-id="616f6-355">You've now successfully built a machine learning model for image classification by reusing a pre-trained `TensorFlow` model in ML.NET.</span></span>

<span data-ttu-id="616f6-356">Você pode encontrar o código-fonte para este tutorial no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF).</span><span class="sxs-lookup"><span data-stu-id="616f6-356">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repository.</span></span>

<span data-ttu-id="616f6-357">Neste tutorial, você aprendeu como:</span><span class="sxs-lookup"><span data-stu-id="616f6-357">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="616f6-358">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="616f6-358">Understand the problem</span></span>
> * <span data-ttu-id="616f6-359">Reutilizar e ajustar o modelo pré-treinado</span><span class="sxs-lookup"><span data-stu-id="616f6-359">Reuse and tune the pre-trained model</span></span>
> * <span data-ttu-id="616f6-360">Classificar imagens com um modelo carregado</span><span class="sxs-lookup"><span data-stu-id="616f6-360">Classify images with a loaded model</span></span>

<span data-ttu-id="616f6-361">Conferir o repositório GitHub de Amostras de Aprendizado de Máquina para explorar uma amostra de classificação de imagem expandida.</span><span class="sxs-lookup"><span data-stu-id="616f6-361">Check out the Machine Learning samples GitHub repository to explore an expanded image classification sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="616f6-362">dotnet/machinelearning-samples GitHub repository</span><span class="sxs-lookup"><span data-stu-id="616f6-362">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/)
