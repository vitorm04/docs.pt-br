---
title: 'Tutorial: Detectar objetos usando o aprendizado profundo com ONNX e ML.NET'
description: Este tutorial mostra como usar um modelo de aprendizado profundo ONNX pré-treinado no ML.NET para detectar objetos em imagens.
author: luisquintanilla
ms.author: luquinta
ms.date: 08/27/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: a5a11bc49fa834ebd6945e47767deb559244b459
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2019
ms.locfileid: "70374510"
---
# <a name="tutorial-detect-objects-using-onnx-in-mlnet"></a><span data-ttu-id="7ee7a-103">Tutorial: Detectar objetos usando ONNX no ML.NET</span><span class="sxs-lookup"><span data-stu-id="7ee7a-103">Tutorial: Detect objects using ONNX in ML.NET</span></span>

<span data-ttu-id="7ee7a-104">Saiba como usar um modelo ONNX pré-treinado no ML.NET para detectar objetos em imagens.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-104">Learn how to use a pre-trained ONNX model in ML.NET to detect objects in images.</span></span>

<span data-ttu-id="7ee7a-105">Treinar um modelo de detecção de objetos do zero requer a configuração de milhões de parâmetros, uma grande quantidade de dados de treinamento rotulados e uma grande quantidade de recursos de computação (centenas de horas de GPU).</span><span class="sxs-lookup"><span data-stu-id="7ee7a-105">Training an object detection model from scratch requires setting millions of parameters, a large amount of labeled training data and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="7ee7a-106">Usar um modelo pré-treinado permite que você reduza o processo de treinamento.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-106">Using a pre-trained model allows you to shortcut the training process.</span></span>

<span data-ttu-id="7ee7a-107">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="7ee7a-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="7ee7a-108">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="7ee7a-108">Understand the problem</span></span>
> - <span data-ttu-id="7ee7a-109">Saiba o que é o ONNX e como ele funciona com o ML.NET</span><span class="sxs-lookup"><span data-stu-id="7ee7a-109">Learn what ONNX is and how it works with ML.NET</span></span>
> - <span data-ttu-id="7ee7a-110">Entender o modelo</span><span class="sxs-lookup"><span data-stu-id="7ee7a-110">Understand the model</span></span>
> - <span data-ttu-id="7ee7a-111">Reutilizar o modelo pré-treinado</span><span class="sxs-lookup"><span data-stu-id="7ee7a-111">Reuse the pre-trained model</span></span>
> - <span data-ttu-id="7ee7a-112">Detectar objetos com um modelo carregado</span><span class="sxs-lookup"><span data-stu-id="7ee7a-112">Detect objects with a loaded model</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="7ee7a-113">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="7ee7a-113">Pre-requisites</span></span>

- <span data-ttu-id="7ee7a-114">[Visual Studio 2017 15.6 ou posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" instalada.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-114">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>
- [<span data-ttu-id="7ee7a-115">Pacote NuGet do Microsoft.ML</span><span class="sxs-lookup"><span data-stu-id="7ee7a-115">Microsoft.ML NuGet Package</span></span>](https://www.nuget.org/packages/Microsoft.ML/)
- [<span data-ttu-id="7ee7a-116">Pacote NuGet Microsoft.ML.ImageAnalytics</span><span class="sxs-lookup"><span data-stu-id="7ee7a-116">Microsoft.ML.ImageAnalytics NuGet Package</span></span>](https://www.nuget.org/packages/Microsoft.ML.ImageAnalytics/)
- [<span data-ttu-id="7ee7a-117">Pacote NuGet Microsoft.ML.OnnxTransformer</span><span class="sxs-lookup"><span data-stu-id="7ee7a-117">Microsoft.ML.OnnxTransformer NuGet Package</span></span>](https://www.nuget.org/packages/Microsoft.ML.OnnxTransformer/)
- [<span data-ttu-id="7ee7a-118">Modelo pré-treinado Tiny YOLOv2</span><span class="sxs-lookup"><span data-stu-id="7ee7a-118">Tiny YOLOv2 pre-trained model</span></span>](https://github.com/onnx/models/tree/master/tiny_yolov2)
- <span data-ttu-id="7ee7a-119">[Netron](https://github.com/lutzroeder/netron) (opcional)</span><span class="sxs-lookup"><span data-stu-id="7ee7a-119">[Netron](https://github.com/lutzroeder/netron) (optional)</span></span>

## <a name="onnx-object-detection-sample-overview"></a><span data-ttu-id="7ee7a-120">Visão geral do exemplo de detecção de objetos ONNX</span><span class="sxs-lookup"><span data-stu-id="7ee7a-120">ONNX object detection sample overview</span></span>

<span data-ttu-id="7ee7a-121">Este exemplo cria um aplicativo de console .NET Core que detecta objetos em uma imagem usando um modelo ONNX de aprendizado profundo pré-treinado.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-121">This sample creates a .NET core console application that detects objects within an image using a pre-trained deep learning ONNX model.</span></span> <span data-ttu-id="7ee7a-122">O código para este exemplo pode ser encontrado no [repositório dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) no GitHub.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-122">The code for this sample can be found on the [dotnet/machinelearning-samples repository](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) on GitHub.</span></span>

## <a name="what-is-object-detection"></a><span data-ttu-id="7ee7a-123">O que é a detecção de objetos?</span><span class="sxs-lookup"><span data-stu-id="7ee7a-123">What is object detection?</span></span>

<span data-ttu-id="7ee7a-124">A detecção de objetos é um problema da pesquisa visual computacional.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-124">Object detection is a computer vision problem.</span></span> <span data-ttu-id="7ee7a-125">Embora esteja bem relacionada à classificação de imagem, a detecção de objetos executa a classificação de imagem em uma escala mais granular.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-125">While closely related to image classification, object detection performs image classification at a more granular scale.</span></span> <span data-ttu-id="7ee7a-126">A detecção de objetos localiza _e_ categoriza entidades dentro de imagens.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-126">Object detection both locates _and_ categorizes entities within images.</span></span> <span data-ttu-id="7ee7a-127">Use a detecção de objetos quando as imagens contiverem vários objetos de tipos diferentes.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-127">Use object detection when images contain multiple objects of different types.</span></span>

![](./media/object-detection-onnx/img-classification-obj-detection.PNG)

<span data-ttu-id="7ee7a-128">Alguns casos de uso para detecção de objetos incluem:</span><span class="sxs-lookup"><span data-stu-id="7ee7a-128">Some use cases for object detection include:</span></span>

- <span data-ttu-id="7ee7a-129">Carros autônomos</span><span class="sxs-lookup"><span data-stu-id="7ee7a-129">Self-Driving Cars</span></span>
- <span data-ttu-id="7ee7a-130">Robótica</span><span class="sxs-lookup"><span data-stu-id="7ee7a-130">Robotics</span></span>
- <span data-ttu-id="7ee7a-131">Detecção Facial</span><span class="sxs-lookup"><span data-stu-id="7ee7a-131">Face Detection</span></span>
- <span data-ttu-id="7ee7a-132">Segurança do local de trabalho</span><span class="sxs-lookup"><span data-stu-id="7ee7a-132">Workplace Safety</span></span>
- <span data-ttu-id="7ee7a-133">Contagem de objetos</span><span class="sxs-lookup"><span data-stu-id="7ee7a-133">Object Counting</span></span>
- <span data-ttu-id="7ee7a-134">Reconhecimento de atividades</span><span class="sxs-lookup"><span data-stu-id="7ee7a-134">Activity Recognition</span></span>

## <a name="select-a-deep-learning-model"></a><span data-ttu-id="7ee7a-135">Selecionar um modelo de aprendizado profundo</span><span class="sxs-lookup"><span data-stu-id="7ee7a-135">Select a deep learning model</span></span>

<span data-ttu-id="7ee7a-136">O aprendizado profundo é um subconjunto de aprendizado de máquina.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-136">Deep learning is a subset of machine learning.</span></span> <span data-ttu-id="7ee7a-137">Para treinar modelos de aprendizado profundo, grandes quantidades de dados são necessárias.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-137">To train deep learning models, large quantities of data are required.</span></span> <span data-ttu-id="7ee7a-138">Os padrões nos dados são representados por uma série de camadas.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-138">Patterns in the data are represented by a series of layers.</span></span> <span data-ttu-id="7ee7a-139">As relações nos dados são codificadas como conexões entre as camadas que contêm pesos.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-139">The relationships in the data are encoded as connections between the layers containing weights.</span></span> <span data-ttu-id="7ee7a-140">Quanto maior o peso, mais forte a relação.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-140">The higher the weight, the stronger the relationship.</span></span> <span data-ttu-id="7ee7a-141">Coletivamente, essa série de camadas e conexões é conhecida como redes neurais artificiais.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-141">Collectively, this series of layers and connections are known as artificial neural networks.</span></span> <span data-ttu-id="7ee7a-142">Quanto mais camadas em uma rede, "mais profunda" ela será, tornando-a uma rede neural profunda.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-142">The more layers in a network, the "deeper" it is, making it a deep neural network.</span></span>

<span data-ttu-id="7ee7a-143">Há diferentes tipos de redes neurais, as mais comuns são a MLP (Perceptron Multicamadas), a CNN (Rede Neural de Convolução) e a RNN (Rede Neural Recorrente).</span><span class="sxs-lookup"><span data-stu-id="7ee7a-143">There are different types of neural networks, the most common being Multi-Layered Perceptron (MLP), Convolutional Neural Network (CNN) and Recurrent Neural Network (RNN).</span></span> <span data-ttu-id="7ee7a-144">A mais básica é a MLP, que mapeia um conjunto de entradas para um conjunto de saídas.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-144">The most basic is the MLP, which maps a set of inputs to a set of outputs.</span></span> <span data-ttu-id="7ee7a-145">Essa rede neural é boa quando os dados não têm um componente espacial ou de tempo.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-145">This neural network is good when the data does not have a spatial or time component.</span></span> <span data-ttu-id="7ee7a-146">A CNN usa camadas de convolução para processar informações espaciais contidas nos dados.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-146">The CNN makes use of convolutional layers to process spatial information contained in the data.</span></span> <span data-ttu-id="7ee7a-147">Um bom caso de uso para as CNNs é o processamento de imagens para detectar a presença de um recurso em uma região de uma imagem (por exemplo, há um nariz no centro de uma imagem?).</span><span class="sxs-lookup"><span data-stu-id="7ee7a-147">A good use case for CNNs is image processing to detect the presence of a feature in a region of an image (for example, is there a nose in the center of an image?).</span></span> <span data-ttu-id="7ee7a-148">Por fim, as RNNs permitem que a persistência do estado ou da memória seja usada como entrada.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-148">Finally, RNNs allow for the persistence of state or memory to be used as input.</span></span> <span data-ttu-id="7ee7a-149">As RNNs são usadas para análise de série temporal, em que a ordenação sequencial e o contexto dos eventos são importantes.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-149">RNNs are used for time-series analysis, where the sequential ordering and context of events is important.</span></span>

### <a name="understand-the-model"></a><span data-ttu-id="7ee7a-150">Entender o modelo</span><span class="sxs-lookup"><span data-stu-id="7ee7a-150">Understand the model</span></span>

<span data-ttu-id="7ee7a-151">A detecção de objetos é uma tarefa de processamento de imagem.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-151">Object detection is an image processing task.</span></span> <span data-ttu-id="7ee7a-152">Portanto, os modelos de aprendizado profundo mais treinados para resolver esse problema são as CNNs.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-152">Therefore, most deep learning models trained to solve this problem are CNNs.</span></span> <span data-ttu-id="7ee7a-153">O modelo usado neste tutorial é o Tiny YOLOv2, uma versão mais compacta do modelo YOLOv2 descrito no documento: ["YOLO9000: Better, Faster, Stronger" por Redmon e Fadhari](https://arxiv.org/pdf/1612.08242.pdf).</span><span class="sxs-lookup"><span data-stu-id="7ee7a-153">The model used in this tutorial is the Tiny YOLOv2 model, a more compact version of the YOLOv2 model described in the paper: ["YOLO9000: Better, Faster, Stronger" by Redmon and Fadhari](https://arxiv.org/pdf/1612.08242.pdf).</span></span> <span data-ttu-id="7ee7a-154">O Tiny YOLOv2 é treinado no conjunto de dados do Pascal VOC e é composto por 15 camadas que podem prever 20 classes diferentes de objetos.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-154">Tiny YOLOv2 is trained on the Pascal VOC dataset and is made up of 15 layers that can predict 20 different classes of objects.</span></span> <span data-ttu-id="7ee7a-155">Como o Tiny YOLOv2 é uma versão condensada do modelo YOLOv2 original, é feita uma compensação entre velocidade e precisão.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-155">Because Tiny YOLOv2 is a condensed version of the original YOLOv2 model, a tradeoff is made between speed and accuracy.</span></span> <span data-ttu-id="7ee7a-156">As diferentes camadas que compõem o modelo podem ser visualizadas usando ferramentas como o Netron.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-156">The different layers that make up the model can be visualized using tools like Netron.</span></span> <span data-ttu-id="7ee7a-157">Inspecionar o modelo produziria um mapeamento das conexões entre todas as camadas que compõem a rede neural, em que cada camada conteria o nome da camada junto com as dimensões da respectiva entrada/saída.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-157">Inspecting the model would yield a mapping of the connections between all the layers that make up the neural network, where each layer would contain the name of the layer along with the dimensions of the respective input / output.</span></span> <span data-ttu-id="7ee7a-158">As estruturas de dados usadas para descrever as entradas e as saídas do modelo são conhecidas como tensores.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-158">The data structures used to describe the inputs and outputs of the model are known as tensors.</span></span> <span data-ttu-id="7ee7a-159">Os tensores podem ser entendidos como contêineres que armazenam dados em N dimensões.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-159">Tensors can be thought of as containers that store data in N-dimensions.</span></span> <span data-ttu-id="7ee7a-160">No caso do Tiny YOLOv2, o nome da camada de entrada é `image` e ele espera um tensor de dimensões `3 x 416 x 416`.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-160">In the case of Tiny YOLOv2, the name of the input layer is `image` and it expects a tensor of dimensions `3 x 416 x 416`.</span></span> <span data-ttu-id="7ee7a-161">O nome da camada de saída é `grid` e gera um tensor de saída de dimensões `125 x 13 x 13`.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-161">The name of the output layer is `grid` and generates an output tensor of dimensions `125 x 13 x 13`.</span></span>

![](./media/object-detection-onnx/netron-model-map.png)

<span data-ttu-id="7ee7a-162">O modelo YOLO usa uma imagem `3(RGB) x 416px x 416px`.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-162">The YOLO model takes an image `3(RGB) x 416px x 416px`.</span></span> <span data-ttu-id="7ee7a-163">O modelo usa essa entrada e a passa pelas diferentes camadas para produzir uma saída.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-163">The model takes this input and passes it through the different layers to produce an output.</span></span> <span data-ttu-id="7ee7a-164">A saída divide a imagem de entrada em uma grade `13 x 13`, com cada célula na grade consistindo em `125` valores.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-164">The output divides the input image into a `13 x 13` grid, with each cell in the grid consisting of `125` values.</span></span>

### <a name="what-is-an-onnx-model"></a><span data-ttu-id="7ee7a-165">O que é um modelo ONNX?</span><span class="sxs-lookup"><span data-stu-id="7ee7a-165">What is an ONNX model?</span></span>

<span data-ttu-id="7ee7a-166">O ONNX (Open Neural Network Exchange) é um formato de software livre para modelos de IA.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-166">The Open Neural Network Exchange (ONNX) is an open source format for AI models.</span></span> <span data-ttu-id="7ee7a-167">O ONNX é compatível com a interoperabilidade entre estruturas.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-167">ONNX supports interoperability between frameworks.</span></span> <span data-ttu-id="7ee7a-168">Isso significa que você pode treinar um modelo em uma das muitas estruturas de aprendizado de máquina populares, como PyTorch, convertê-la em formato ONNX e consumir o modelo ONNX em uma estrutura diferente, como ML.NET.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-168">This means you can train a model in one of the many popular machine learning frameworks like PyTorch, convert it into ONNX format and consume the ONNX model in a different framework like ML.NET.</span></span> <span data-ttu-id="7ee7a-169">Para saber mais, visite o [site do ONNX](https://onnx.ai/).</span><span class="sxs-lookup"><span data-stu-id="7ee7a-169">To learn more, visit the [ONNX website](https://onnx.ai/).</span></span>

![](./media/object-detection-onnx/onnx-frameworks.png)

<span data-ttu-id="7ee7a-170">O modelo Tiny YOLOv2 pré-treinado é armazenado no formato ONNX, uma representação serializada das camadas e dos padrões aprendidos dessas camadas.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-170">The pre-trained Tiny YOLOv2 model is stored in ONNX format, a serialized representation of the layers and learned patterns of those layers.</span></span> <span data-ttu-id="7ee7a-171">No ML.NET, a interoperabilidade com o ONNX é obtida com os pacotes NuGet [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) e [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer).</span><span class="sxs-lookup"><span data-stu-id="7ee7a-171">In ML.NET, interoperability with ONNX is achieved with the [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) and [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) NuGet packages.</span></span> <span data-ttu-id="7ee7a-172">O pacote [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) contém uma série de transformações que pegam uma imagem e a codificam em valores numéricos que podem ser usados como entrada em um pipeline de previsão ou de treinamento.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-172">The [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) package contains a series of transforms that take an image and encode it into numerical values that can be used as input into a prediction or training pipeline.</span></span> <span data-ttu-id="7ee7a-173">O pacote [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) aproveita o tempo de execução do ONNX para carregar um modelo ONNX e usá-lo para fazer previsões com base na entrada fornecida.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-173">The [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) package leverages the ONNX Runtime to load an ONNX model and use it to make predictions based on input provided.</span></span>

![](./media/object-detection-onnx/onnx-ml-net-integration.png)

## <a name="set-up-the-net-core-project"></a><span data-ttu-id="7ee7a-174">Configurar o projeto do .NET Core</span><span class="sxs-lookup"><span data-stu-id="7ee7a-174">Set up the .NET Core project</span></span>

<span data-ttu-id="7ee7a-175">Agora que você tem um entendimento geral do que é o ONNX e de como o Tiny YOLOv2 funciona, é hora de criar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-175">Now that you have a general understanding of what ONNX is and how Tiny YOLOv2 works, it's time to build the application.</span></span>

### <a name="create-a-console-application"></a><span data-ttu-id="7ee7a-176">Criar um aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="7ee7a-176">Create a console application</span></span>

1. <span data-ttu-id="7ee7a-177">Crie um **Aplicativo de console do .NET Core** chamado "ObjectDetection".</span><span class="sxs-lookup"><span data-stu-id="7ee7a-177">Create a **.NET Core Console Application** called "ObjectDetection".</span></span>

1. <span data-ttu-id="7ee7a-178">Instalar o **Pacote NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="7ee7a-178">Install the **Microsoft.ML NuGet Package**:</span></span>

    - <span data-ttu-id="7ee7a-179">No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-179">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    - <span data-ttu-id="7ee7a-180">Escolha "nuget.org" como a fonte do pacote, selecione a guia Browse, procure por **Microsoft.ML**.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-180">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**.</span></span>
    - <span data-ttu-id="7ee7a-181">Selecione o botão **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-181">Select the **Install** button.</span></span>
    - <span data-ttu-id="7ee7a-182">Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-182">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>
    - <span data-ttu-id="7ee7a-183">Repita essas etapas para **Microsoft.ML.ImageAnalytics** e **Microsoft.ML.OnnxTransformer**.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-183">Repeat these steps for **Microsoft.ML.ImageAnalytics** and **Microsoft.ML.OnnxTransformer**.</span></span>

### <a name="prepare-your-data-and-pre-trained-model"></a><span data-ttu-id="7ee7a-184">Prepare seus dados e um modelo pré-treinado</span><span class="sxs-lookup"><span data-stu-id="7ee7a-184">Prepare your data and pre-trained model</span></span>

1. <span data-ttu-id="7ee7a-185">Baixe o [arquivo zip do diretório de ativos do projeto](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/assets.zip) e descompacte.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-185">Download [The project assets directory zip file](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/assets.zip) and unzip.</span></span>

1. <span data-ttu-id="7ee7a-186">Copie o diretório `assets` no diretório do projeto *ObjectDetection*.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-186">Copy the `assets` directory into your *ObjectDetection* project directory.</span></span> <span data-ttu-id="7ee7a-187">Este diretório e seus subdiretórios contêm os arquivos de imagem (exceto para o modelo Tiny YOLOv2, que você baixará e adicionará na próxima etapa) necessários para este tutorial.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-187">This directory and its subdirectories contain the image files (except for the Tiny YOLOv2 model, which you'll download and add in the next step) needed for this tutorial.</span></span>

1. <span data-ttu-id="7ee7a-188">Baixe o [modelo Tiny YOLOv2](https://onnxzoo.blob.core.windows.net/models/opset_8/tiny_yolov2/tiny_yolov2.tar.gz) de [ONNX Model Zoo](https://github.com/onnx/models/tree/master/vision/object_detection_segmentation/tiny_yolov2) e descompacte.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-188">Download the [Tiny YOLOv2 model](https://onnxzoo.blob.core.windows.net/models/opset_8/tiny_yolov2/tiny_yolov2.tar.gz) from the [ONNX Model Zoo](https://github.com/onnx/models/tree/master/vision/object_detection_segmentation/tiny_yolov2), and unzip.</span></span>

    <span data-ttu-id="7ee7a-189">Abra o prompt de comando e insira o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="7ee7a-189">Open the command prompt and enter the following command:</span></span>

    ```shell
    tar -xvzf tiny_yolov2.tar.gz
    ```

1. <span data-ttu-id="7ee7a-190">Copie o arquivo `model.onnx` extraído do diretório que acabou de descompactar em seu diretório de projeto *ObjectDetection* `assets\Model` e renomeie-o como `TinyYolo2_model.onnx`.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-190">Copy the extracted `model.onnx` file from the directory just unzipped into your *ObjectDetection* project `assets\Model` directory and rename it to `TinyYolo2_model.onnx`.</span></span> <span data-ttu-id="7ee7a-191">Este diretório contém o modelo necessário para este tutorial.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-191">This directory contains the model needed for this tutorial.</span></span>

1. <span data-ttu-id="7ee7a-192">No Gerenciador de Soluções, clique com o botão direito do mouse em cada um dos arquivos no diretório e nos subdiretórios do ativo e selecione**Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-192">In Solution Explorer, right-click each of the files in the asset directory and subdirectories and select **Properties**.</span></span> <span data-ttu-id="7ee7a-193">Em **Avançado**, altere o valor de **Copiar para Diretório de Saída** para **Copiar se for mais novo**.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-193">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="7ee7a-194">Criar classes e definir demarcadores</span><span class="sxs-lookup"><span data-stu-id="7ee7a-194">Create classes and define paths</span></span>

<span data-ttu-id="7ee7a-195">Abra o arquivo *Program.cs* e adicione as seguintes instruções `using` complementares à parte superior do arquivo:</span><span class="sxs-lookup"><span data-stu-id="7ee7a-195">Open the *Program.cs* file and add the following additional `using` statements to the top of the file:</span></span>

[!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L1-L7)]

<span data-ttu-id="7ee7a-196">Em seguida, defina os caminhos dos vários ativos.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-196">Next, define the paths of the various assets.</span></span>

1. <span data-ttu-id="7ee7a-197">Primeiro, adicione o método `GetAbsolutePath` abaixo do método `Main` na classe `Program`.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-197">First, add the `GetAbsolutePath` method below the `Main` method in the `Program` class.</span></span>

    [!code-csharp [GetAbsolutePath](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L66-L74)]

1. <span data-ttu-id="7ee7a-198">Em seguida, dentro do método `Main`, crie campos para armazenar a localização dos ativos.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-198">Then, inside the `Main` method, create fields to store the location of your assets.</span></span>

    [!code-csharp [AssetDefinition](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L17-L21)]

<span data-ttu-id="7ee7a-199">Adicione um novo diretório ao seu projeto para armazenar os dados de entrada e as classes de previsão.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-199">Add a new directory to your project to store your input data and prediction classes.</span></span>

<span data-ttu-id="7ee7a-200">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Nova Pasta**.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-200">In **Solution Explorer**, right-click the project, and then select **Add** > **New Folder**.</span></span> <span data-ttu-id="7ee7a-201">Quando a nova pasta aparecer no Gerenciador de Soluções, nomeie-a como "DataStructures".</span><span class="sxs-lookup"><span data-stu-id="7ee7a-201">When the new folder appears in the Solution Explorer, name it "DataStructures".</span></span>

<span data-ttu-id="7ee7a-202">Crie sua classe de dados de entrada no diretório *DataStructures* recém-criado.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-202">Create your input data class in the newly created *DataStructures* directory.</span></span>

1. <span data-ttu-id="7ee7a-203">No **Gerenciador de Soluções**, clique com o botão direito do mouse no diretório *DataStructures* e, em seguida, selecione **Adicionar** > **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-203">In **Solution Explorer**, right-click the *DataStructures* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="7ee7a-204">Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *ImageNetData.cs*.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-204">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *ImageNetData.cs*.</span></span> <span data-ttu-id="7ee7a-205">Em seguida, selecione o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-205">Then, select the **Add** button.</span></span>

    <span data-ttu-id="7ee7a-206">O arquivo *ImageNetData.cs* é aberto no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-206">The *ImageNetData.cs* file opens in the code editor.</span></span> <span data-ttu-id="7ee7a-207">Adicione a seguinte instrução `using` à parte superior do *ImageNetData.cs*:</span><span class="sxs-lookup"><span data-stu-id="7ee7a-207">Add the following `using` statement to the top of *ImageNetData.cs*:</span></span>

    [!code-csharp [ImageNetDataUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetData.cs#L1-L4)]

    <span data-ttu-id="7ee7a-208">Remova a definição de classe existente e adicione o seguinte código para a classe `ImageNetData` do arquivo *ImageNetData.cs*:</span><span class="sxs-lookup"><span data-stu-id="7ee7a-208">Remove the existing class definition and add the following code for the `ImageNetData` class to the *ImageNetData.cs* file:</span></span>

    [!code-csharp [ImageNetDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetData.cs#L8-L23)]

    <span data-ttu-id="7ee7a-209">`ImageNetData` é a classe de conjunto de dados de entrada e tem os seguintes campos <xref:System.String>:</span><span class="sxs-lookup"><span data-stu-id="7ee7a-209">`ImageNetData` is the input image data class and has the following <xref:System.String> fields:</span></span>

    - <span data-ttu-id="7ee7a-210">Um `ImagePath` que contém o caminho no qual a imagem é armazenada.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-210">`ImagePath` contains the path where the image is stored.</span></span>
    - <span data-ttu-id="7ee7a-211">Um `Label` que contém o nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-211">`Label` contains the name of the file.</span></span>

    <span data-ttu-id="7ee7a-212">Além disso, o `ImageNetData` contém um método `ReadFromFile` que carrega vários arquivos de imagem armazenados no caminho `imageFolder` especificado e os retorna como uma coleção de objetos `ImageNetData`.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-212">Additionally, `ImageNetData` contains a method `ReadFromFile` which loads multiple image files stored in the `imageFolder` path specified and returns them as a collection of `ImageNetData` objects.</span></span>

<span data-ttu-id="7ee7a-213">Crie sua classe de previsão no diretório *DataStructures*.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-213">Create your prediction class in the *DataStructures* directory.</span></span>

1. <span data-ttu-id="7ee7a-214">No **Gerenciador de Soluções**, clique com o botão direito do mouse no diretório *DataStructures* e, em seguida, selecione **Adicionar** > **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-214">In **Solution Explorer**, right-click the *DataStructures* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="7ee7a-215">Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *ImageNetPrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-215">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *ImageNetPrediction.cs*.</span></span> <span data-ttu-id="7ee7a-216">Em seguida, selecione o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-216">Then, select the **Add** button.</span></span>

    <span data-ttu-id="7ee7a-217">O arquivo *ImageNetPrediction.cs* é aberto no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-217">The *ImageNetPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="7ee7a-218">Adicione a seguinte instrução `using` à parte superior do *ImageNetPrediction.cs*:</span><span class="sxs-lookup"><span data-stu-id="7ee7a-218">Add the following `using` statement to the top of *ImageNetPrediction.cs*:</span></span>

    [!code-csharp [ImageNetPredictionUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetPrediction.cs#L1)]

    <span data-ttu-id="7ee7a-219">Remova a definição de classe existente e adicione o seguinte código para a classe `ImageNetPrediction` do arquivo *ImageNetPrediction.cs*:</span><span class="sxs-lookup"><span data-stu-id="7ee7a-219">Remove the existing class definition and add the following code for the `ImageNetPrediction` class to the *ImageNetPrediction.cs* file:</span></span>

    [!code-csharp [ImageNetPredictionClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetPrediction.cs#L5-L9)]

    <span data-ttu-id="7ee7a-220">O `ImageNetPrediction` é a classe de dados de previsão e conta com os seguintes `float[]` campos:</span><span class="sxs-lookup"><span data-stu-id="7ee7a-220">`ImageNetPrediction` is the prediction data class and has the following `float[]` field:</span></span>

    - <span data-ttu-id="7ee7a-221">`PredictedLabel` contém as dimensões, a pontuação de objeções e as probabilidades de classe para cada uma das caixas delimitadoras detectadas em uma imagem.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-221">`PredictedLabel` contains the dimensions, objectness score and class probabilities for each of the bounding boxes detected in an image.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="7ee7a-222">Inicializar variáveis em Main</span><span class="sxs-lookup"><span data-stu-id="7ee7a-222">Initialize variables in Main</span></span>

<span data-ttu-id="7ee7a-223">A [classe MLContext](xref:Microsoft.ML.MLContext) é um ponto de partida para todas as operações do ML.NET e a inicialização do `mlContext` cria um ambiente do ML.NET que pode ser compartilhado entre os objetos de fluxo de trabalho da criação de modelo.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-223">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="7ee7a-224">Ele é semelhante, conceitualmente, a `DBContext` no Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-224">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

<span data-ttu-id="7ee7a-225">Inicialize a variável `mlContext` com uma nova instância de `MLContext` adicionando a linha a seguir ao método `Main` de *Program.cs* abaixo do campo `outputFolder`.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-225">Initialize the `mlContext` variable with a new instance of `MLContext` by adding the following line to the `Main` method of *Program.cs* below the `outputFolder` field.</span></span>

[!code-csharp [InitMLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L24)]

## <a name="create-a-parser-to-post-process-model-outputs"></a><span data-ttu-id="7ee7a-226">Criar um analisador para saídas de modelo de pós-processamento</span><span class="sxs-lookup"><span data-stu-id="7ee7a-226">Create a parser to post-process model outputs</span></span>

<span data-ttu-id="7ee7a-227">O modelo segmenta uma imagem em uma grade `13 x 13`, em que cada célula de grade é `32px x 32px`.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-227">The model segments an image into a `13 x 13` grid, where each grid cell is `32px x 32px`.</span></span> <span data-ttu-id="7ee7a-228">Cada célula de grade contém cinco caixas delimitadoras de objetos potenciais.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-228">Each grid cell contains 5 potential object bounding boxes.</span></span> <span data-ttu-id="7ee7a-229">Uma caixa delimitadora tem 25 elementos:</span><span class="sxs-lookup"><span data-stu-id="7ee7a-229">A bounding box has  25 elements:</span></span>

![](./media/object-detection-onnx/model-output-description.png)

- <span data-ttu-id="7ee7a-230">`x`: a posição x do centro da caixa delimitadora relativa à célula da grade à qual ela está associada.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-230">`x` the x position of the bounding box center relative to the grid cell it's associated with.</span></span>
- <span data-ttu-id="7ee7a-231">`y`: a posição y do centro da caixa delimitadora relativa à célula da grade à qual ela está associada.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-231">`y` the y position of the bounding box center relative to the grid cell it's associated with.</span></span>
- <span data-ttu-id="7ee7a-232">`w`: a largura da caixa delimitadora.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-232">`w` the width of the bounding box.</span></span>
- <span data-ttu-id="7ee7a-233">`h`: a altura da caixa delimitadora.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-233">`h` the height of the bounding box.</span></span>
- <span data-ttu-id="7ee7a-234">`o`: o valor de confiança de que um objeto existe dentro da caixa delimitadora, também conhecido como pontuação de objeções.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-234">`o` the confidence value that an object exists within the bounding box, also known as objectness score.</span></span>
- <span data-ttu-id="7ee7a-235">`p1-p20`: probabilidades de classe para cada uma das 20 classes previstas pelo modelo.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-235">`p1-p20` class probabilities for each of the 20 classes predicted by the model.</span></span>

<span data-ttu-id="7ee7a-236">No total, os 25 elementos que descrevem cada uma das cinco caixas delimitadoras compõem os 125 elementos contidos em cada célula de grade.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-236">In total, the 25 elements describing each of the 5 bounding boxes make up the 125 elements contained in each grid cell.</span></span>

<span data-ttu-id="7ee7a-237">A saída gerada pelo modelo ONNX pré-treinado é uma matriz float de cumprimento `21125`, representando os elementos de um tensor com dimensões `125 x 13 x 13`.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-237">The output generated by the pre-trained ONNX model is a float array of length `21125`, representing the elements of a tensor with dimensions `125 x 13 x 13`.</span></span> <span data-ttu-id="7ee7a-238">Para transformar as previsões geradas pelo modelo em um tensor, é necessário algum trabalho de pós-processamento.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-238">In order to transform the predictions generated by the model into a tensor, some post-processing work is required.</span></span> <span data-ttu-id="7ee7a-239">Para fazer isso, crie um conjunto de classes para ajudar a analisar a saída.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-239">To do so, create a set of classes to help parse the output.</span></span>

<span data-ttu-id="7ee7a-240">Adicione um novo diretório ao seu projeto para organizar o conjunto de classes do analisador.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-240">Add a new directory to your project to organize the set of parser classes.</span></span>

1. <span data-ttu-id="7ee7a-241">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Nova Pasta**.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-241">In **Solution Explorer**, right-click the project, and then select **Add** > **New Folder**.</span></span> <span data-ttu-id="7ee7a-242">Quando a nova pasta aparecer no Gerenciador de Soluções, nomeie-a como "YoloParser".</span><span class="sxs-lookup"><span data-stu-id="7ee7a-242">When the new folder appears in the Solution Explorer, name it "YoloParser".</span></span>

### <a name="create-bounding-boxes-and-dimensions"></a><span data-ttu-id="7ee7a-243">Criar caixas delimitadoras e dimensões</span><span class="sxs-lookup"><span data-stu-id="7ee7a-243">Create bounding boxes and dimensions</span></span>

<span data-ttu-id="7ee7a-244">A saída de dados pelo modelo contém coordenadas e dimensões das caixas delimitadoras de objetos dentro da imagem.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-244">The data output by the model contains coordinates and dimensions of the bounding boxes of objects within the image.</span></span> <span data-ttu-id="7ee7a-245">Criar uma classe base para dimensões.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-245">Create a base class for dimensions.</span></span>

1. <span data-ttu-id="7ee7a-246">No **Gerenciador de Soluções**, clique com o botão direito do mouse no diretório *YoloParser* e, em seguida, selecione **Adicionar** > **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-246">In **Solution Explorer**, right-click the *YoloParser* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="7ee7a-247">Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *DimensionsBase.cs*.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-247">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *DimensionsBase.cs*.</span></span> <span data-ttu-id="7ee7a-248">Em seguida, selecione o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-248">Then, select the **Add** button.</span></span>

    <span data-ttu-id="7ee7a-249">O arquivo *DimensionsBase.cs* é aberto no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-249">The *DimensionsBase.cs* file opens in the code editor.</span></span> <span data-ttu-id="7ee7a-250">Remova todas as instruções `using` e a definição de classe existente.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-250">Remove all `using` statements and existing class definition.</span></span>

    <span data-ttu-id="7ee7a-251">Adicione o seguinte código à classe `DimensionsBase` ao arquivo *DimensionsBase.cs*:</span><span class="sxs-lookup"><span data-stu-id="7ee7a-251">Add the following code for the `DimensionsBase` class to the *DimensionsBase.cs* file:</span></span>

    [!code-csharp [DimensionsBaseClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/DimensionsBase.cs#L3-L9)]

    <span data-ttu-id="7ee7a-252">`DimensionsBase` conta com os seguintes `float` campos:</span><span class="sxs-lookup"><span data-stu-id="7ee7a-252">`DimensionsBase` has the following `float` fields:</span></span>

    - <span data-ttu-id="7ee7a-253">`X` contém a posição do objeto ao longo do eixo x.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-253">`X` contains the position of the object along the x-axis.</span></span>
    - <span data-ttu-id="7ee7a-254">`Y` contém a posição do objeto ao longo do eixo y.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-254">`Y` contains the position of the object along the y-axis.</span></span>
    - <span data-ttu-id="7ee7a-255">`Height` contém a altura do objeto.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-255">`Height` contains the height of the object.</span></span>
    - <span data-ttu-id="7ee7a-256">`Width` contém a largura do objeto.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-256">`Width` contains the width of the object.</span></span>

<span data-ttu-id="7ee7a-257">Em seguida, crie uma classe para suas caixas delimitadoras.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-257">Next, create a class for your bounding boxes.</span></span>

1. <span data-ttu-id="7ee7a-258">No **Gerenciador de Soluções**, clique com o botão direito do mouse no diretório *YoloParser* e, em seguida, selecione **Adicionar** > **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-258">In **Solution Explorer**, right-click the *YoloParser* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="7ee7a-259">Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *YoloBoundingBox.cs*.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-259">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *YoloBoundingBox.cs*.</span></span> <span data-ttu-id="7ee7a-260">Em seguida, selecione o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-260">Then, select the **Add** button.</span></span>

    <span data-ttu-id="7ee7a-261">O arquivo *YoloBoundingBox.cs* é aberto no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-261">The *YoloBoundingBox.cs* file opens in the code editor.</span></span> <span data-ttu-id="7ee7a-262">Adicione a seguinte instrução `using` à parte superior do *YoloBoundingBox.cs*:</span><span class="sxs-lookup"><span data-stu-id="7ee7a-262">Add the following `using` statement to the top of *YoloBoundingBox.cs*:</span></span>

    [!code-csharp [YoloBoundingBoxUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L1)]

    <span data-ttu-id="7ee7a-263">Logo acima da definição de classe existente, adicione uma nova definição de classe chamada `BoundingBoxDimensions`, que herda da classe `DimensionsBase` para conter as dimensões da respectiva caixa delimitadora.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-263">Just above the existing class definition, add a new class definition called `BoundingBoxDimensions` which inherits from the `DimensionsBase` class to contain the dimensions of the respective bounding box.</span></span>

    [!code-csharp [BoundingBoxDimClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L5)]

    <span data-ttu-id="7ee7a-264">Remova a definição de classe `YoloBoundingBox` existente e adicione o seguinte código para a classe `YoloBoundingBox` do arquivo *YoloBoundingBox.cs*:</span><span class="sxs-lookup"><span data-stu-id="7ee7a-264">Remove the existing `YoloBoundingBox` class definition and add the following code for the `YoloBoundingBox` class to the *YoloBoundingBox.cs* file:</span></span>

    [!code-csharp [YoloBoundingBoxClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L7-L21)]

    <span data-ttu-id="7ee7a-265">`YoloBoundingBox` conta com os seguintes campos:</span><span class="sxs-lookup"><span data-stu-id="7ee7a-265">`YoloBoundingBox` has the following fields:</span></span>

    - <span data-ttu-id="7ee7a-266">`Dimensions` contém as dimensões da caixa delimitadora.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-266">`Dimensions` contains dimensions of the bounding box.</span></span>
    - <span data-ttu-id="7ee7a-267">`Label` contém a classe de objeto detectada na caixa delimitadora.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-267">`Label` contains the class of object detected within the bounding box.</span></span>
    - <span data-ttu-id="7ee7a-268">`Confidence` contém a confiança da classe.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-268">`Confidence` contains the confidence of the class.</span></span>
    - <span data-ttu-id="7ee7a-269">`Rect` contém a representação de retângulo das dimensões da caixa delimitadora.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-269">`Rect` contains the rectangle representation of the bounding box's dimensions.</span></span>
    - <span data-ttu-id="7ee7a-270">`BoxColor` contém a cor associada à respectiva classe usada para desenhar na imagem.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-270">`BoxColor` contains the color associated with the respective class used to draw on the image.</span></span>

### <a name="create-the-parser"></a><span data-ttu-id="7ee7a-271">Criar o analisador</span><span class="sxs-lookup"><span data-stu-id="7ee7a-271">Create the parser</span></span>

<span data-ttu-id="7ee7a-272">Agora que as classes para dimensões e caixas delimitadoras estão criadas, é hora de criar o analisador.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-272">Now that the classes for dimensions and bounding boxes are created, it's time to create the parser.</span></span>

1. <span data-ttu-id="7ee7a-273">No **Gerenciador de Soluções**, clique com o botão direito do mouse no diretório *YoloParser* e, em seguida, selecione **Adicionar** > **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-273">In **Solution Explorer**, right-click the *YoloParser* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="7ee7a-274">Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *YoloOutputParser.cs*.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-274">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *YoloOutputParser.cs*.</span></span> <span data-ttu-id="7ee7a-275">Em seguida, selecione o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-275">Then, select the **Add** button.</span></span>

    <span data-ttu-id="7ee7a-276">O arquivo *YoloOutputParser.cs* é aberto no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-276">The *YoloOutputParser.cs* file opens in the code editor.</span></span> <span data-ttu-id="7ee7a-277">Adicione a seguinte instrução `using` à parte superior do *YoloOutputParser.cs*:</span><span class="sxs-lookup"><span data-stu-id="7ee7a-277">Add the following `using` statement to the top of *YoloOutputParser.cs*:</span></span>

    [!code-csharp [YoloParserUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L1-L4)]

    <span data-ttu-id="7ee7a-278">Dentro da definição de classe `YoloOutputParser` existente, adicione uma classe aninhada que contém as dimensões de cada uma das células da imagem.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-278">Inside the existing `YoloOutputParser` class definition, add a nested class that contains the dimensions of each of the cells in the image.</span></span> <span data-ttu-id="7ee7a-279">Adicione o seguinte código para a classe `CellDimensions` que herda da classe `DimensionsBase` na parte superior da definição de classe `YoloOutputParser`.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-279">Add the following code for the `CellDimensions` class which inherits from the `DimensionsBase` class at the top of the `YoloOutputParser` class definition.</span></span>

    [!code-csharp [YoloParserUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L10)]

1. <span data-ttu-id="7ee7a-280">Na definição de classe `YoloOutputParser`, adicione a constante e os campos a seguir.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-280">Inside the `YoloOutputParser` class definition, add the following constant and fields.</span></span>

    [!code-csharp [ParserVarDefinitions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L12-L21)]

    - <span data-ttu-id="7ee7a-281">`ROW_COUNT` é o número de linhas na grade em que a imagem é dividida.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-281">`ROW_COUNT` is the number of rows in the grid the image is divided into.</span></span>
    - <span data-ttu-id="7ee7a-282">`COL_COUNT` é o número de colunas na grade em que a imagem é dividida.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-282">`COL_COUNT` is the number of columns in the grid the image is divided into.</span></span>
    - <span data-ttu-id="7ee7a-283">`CHANNEL_COUNT` é o número total de valores contidos em uma célula da grade.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-283">`CHANNEL_COUNT` is the total number of values contained in one cell of the grid.</span></span>
    - <span data-ttu-id="7ee7a-284">`BOXES_PER_CELL` é o número de caixas delimitadoras em uma célula.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-284">`BOXES_PER_CELL` is the number of bounding boxes in a cell,</span></span>
    - <span data-ttu-id="7ee7a-285">`BOX_INFO_FEATURE_COUNT` é o número de recursos contidos em uma caixa (x, y, altura, largura, confiança).</span><span class="sxs-lookup"><span data-stu-id="7ee7a-285">`BOX_INFO_FEATURE_COUNT` is the number of features contained within a box (x,y,height,width,confidence).</span></span>
    - <span data-ttu-id="7ee7a-286">`CLASS_COUNT` é o número de previsões de classe contidas em cada caixa delimitadora.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-286">`CLASS_COUNT` is the number of class predictions contained in each bounding box.</span></span>
    - <span data-ttu-id="7ee7a-287">`CELL_WIDTH` é a largura de uma célula na grade de imagens.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-287">`CELL_WIDTH` is the width of one cell in the image grid.</span></span>
    - <span data-ttu-id="7ee7a-288">`CELL_HEIGHT` é a altura de uma célula na grade de imagens.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-288">`CELL_HEIGHT` is the height of one cell in the image grid.</span></span>
    - <span data-ttu-id="7ee7a-289">`channelStride` é a posição inicial da célula atual na grade.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-289">`channelStride` is the starting position of the current cell in the grid.</span></span>

    <span data-ttu-id="7ee7a-290">Quando o modelo faz uma previsão, também conhecida como pontuação, ele divide a imagem de entrada `416px x 416px` em uma grade de células com o tamanho `13 x 13`.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-290">When the model makes a prediction, also known as scoring, it divides the `416px x 416px` input image into a grid of cells the size of `13 x 13`.</span></span> <span data-ttu-id="7ee7a-291">O conteúdo de cada célula é `32px x 32px`.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-291">Each cell contains is `32px x 32px`.</span></span> <span data-ttu-id="7ee7a-292">Dentro de cada célula, há cinco caixas delimitadoras que contêm cinco recursos (x, y, largura, altura, confiança).</span><span class="sxs-lookup"><span data-stu-id="7ee7a-292">Within each cell, there are 5 bounding boxes each containing 5 features (x, y, width, height, confidence).</span></span> <span data-ttu-id="7ee7a-293">Além disso, cada caixa delimitadora contém a probabilidade de cada uma das classes que, nesse caso, é 20.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-293">In addition, each bounding box contains the probability of each of the classes which in this case is 20.</span></span> <span data-ttu-id="7ee7a-294">Portanto, cada célula contém 125 partes de informações (cinco recursos + 20 probabilidades de classe).</span><span class="sxs-lookup"><span data-stu-id="7ee7a-294">Therefore, each cell contains 125 pieces of information (5 features + 20 class probabilities).</span></span>

<span data-ttu-id="7ee7a-295">Crie uma lista de âncoras abaixo de `channelStride` para todas as cinco caixas delimitadoras:</span><span class="sxs-lookup"><span data-stu-id="7ee7a-295">Create a list of anchors below `channelStride` for all 5 bounding boxes:</span></span>

[!code-csharp [ParserAnchors](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L23-L26)]

<span data-ttu-id="7ee7a-296">As âncoras são taxas de altura e largura pré-definidas das caixas delimitadoras.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-296">Anchors are pre-defined height and width ratios of bounding boxes.</span></span> <span data-ttu-id="7ee7a-297">A maioria dos objetos ou classes detectadas por um modelo tem taxas semelhantes.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-297">Most object or classes detected by a model have similar ratios.</span></span> <span data-ttu-id="7ee7a-298">Isso é importante quando se trata de criar caixas delimitadoras.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-298">This is valuable when it comes to creating bounding boxes.</span></span> <span data-ttu-id="7ee7a-299">Em vez de prever as caixas delimitadoras, o deslocamento das dimensões pré-definidas é calculado, reduzindo a computação necessária para prever a caixa delimitadora.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-299">Instead of predicting the bounding boxes, the offset from the pre-defined dimensions is calculated therefore reducing the computation required to predict the bounding box.</span></span> <span data-ttu-id="7ee7a-300">Normalmente, essas taxas de âncora são calculadas com base no conjunto de dados usado.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-300">Typically these anchor ratios are calculated based on the dataset used.</span></span> <span data-ttu-id="7ee7a-301">Nesse caso, como o conjunto de dados é conhecido e os valores foram previamente computados, as âncoras podem ser embutidas em código.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-301">In this case because the dataset is known and the values have been pre-computed, the anchors can be hard-coded.</span></span>

<span data-ttu-id="7ee7a-302">Em seguida, defina os rótulos ou as classes que o modelo preverá.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-302">Next, define the labels or classes that the model will predict.</span></span> <span data-ttu-id="7ee7a-303">Esse modelo prevê 20 classes, que é um subconjunto do número total de classes previstas pelo modelo YOLOv2 original.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-303">This model predicts 20 classes which is a subset of the total number of classes predicted by the original YOLOv2 model.</span></span>

<span data-ttu-id="7ee7a-304">Adicione sua lista de rótulos abaixo de `anchors`.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-304">Add your list of labels below the `anchors`.</span></span>

[!code-csharp [ParserLabels](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L28-L34)]

<span data-ttu-id="7ee7a-305">Há cores associadas a cada uma das classes.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-305">There are colors associated with each of the classes.</span></span> <span data-ttu-id="7ee7a-306">Atribua suas cores de classe abaixo de `labels`:</span><span class="sxs-lookup"><span data-stu-id="7ee7a-306">Assign your class colors below your `labels`:</span></span>

[!code-csharp [ParserColors](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L36-L59)]

### <a name="create-helper-functions"></a><span data-ttu-id="7ee7a-307">Criar funções auxiliares</span><span class="sxs-lookup"><span data-stu-id="7ee7a-307">Create helper functions</span></span>

<span data-ttu-id="7ee7a-308">Há uma série de etapas envolvidas na fase de pós-processamento.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-308">There are a series of steps involved in the post-processing phase.</span></span> <span data-ttu-id="7ee7a-309">Para ajudar com isso, vários métodos auxiliares podem ser empregados.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-309">To help with that, several helper methods can be employed.</span></span>

<span data-ttu-id="7ee7a-310">Os métodos auxiliares usados pelo analisador são:</span><span class="sxs-lookup"><span data-stu-id="7ee7a-310">The helper methods used in by the parser are:</span></span>

- <span data-ttu-id="7ee7a-311">`Sigmoid`: aplica a função sigmoide que gera um número entre 0 e 1.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-311">`Sigmoid` applies the sigmoid function that outputs a number between 0 and 1.</span></span>
- <span data-ttu-id="7ee7a-312">`Softmax`: normaliza um vetor de entrada em uma distribuição de probabilidade.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-312">`Softmax` normalizes an input vector into a probability distribution.</span></span>
- <span data-ttu-id="7ee7a-313">`GetOffset`: mapeia elementos na saída de um modelo unidimensional para a posição correspondente em um tensor `125 x 13 x 13`.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-313">`GetOffset` maps elements in the one-dimensional model output to the corresponding position in a `125 x 13 x 13` tensor.</span></span>
- <span data-ttu-id="7ee7a-314">`ExtractBoundingBoxes`: extrai as dimensões da caixa delimitadora usando o método `GetOffset` da saída do modelo.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-314">`ExtractBoundingBoxes` extracts the bounding box dimensions using the `GetOffset` method from the model output.</span></span>
- <span data-ttu-id="7ee7a-315">`GetConfidence`: extrai o valor de confiança que indica a certeza do modelo de que ele detectou um objeto e usa a função `Sigmoid` para transformá-lo em um percentual.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-315">`GetConfidence` extracts the confidence value which states how sure the model is that it has detected an object and uses the `Sigmoid` function to turn it into a percentage.</span></span>
- <span data-ttu-id="7ee7a-316">`MapBoundingBoxToCell`: usa as dimensões da caixa delimitadora e as mapeia para sua respectiva célula na imagem.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-316">`MapBoundingBoxToCell` uses the bounding box dimensions and maps them onto its respective cell within the image.</span></span>
- <span data-ttu-id="7ee7a-317">`ExtractClasses`: extrai as previsões de classe para a caixa delimitadora da saída do modelo usando o método `GetOffset` e as transforma em uma distribuição de probabilidade usando o método `Softmax`.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-317">`ExtractClasses` extracts the class predictions for the bounding box from the model output using the `GetOffset` method and turns them into a probability distribution using the `Softmax` method.</span></span>
- <span data-ttu-id="7ee7a-318">`GetTopResult`: seleciona a classe na lista de classes previstas com a maior probabilidade.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-318">`GetTopResult` selects the class from the list of predicted classes with the highest probability.</span></span>
- <span data-ttu-id="7ee7a-319">`IntersectionOverUnion`: filtra as caixas delimitadoras sobrepostas com probabilidades inferiores.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-319">`IntersectionOverUnion` filters overlapping bounding boxes with lower probabilities.</span></span>

<span data-ttu-id="7ee7a-320">Adicione o código para todos os métodos auxiliares abaixo de sua lista de `classColors`.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-320">Add the code for all the helper methods below your list of `classColors`.</span></span>

[!code-csharp [ParserHelperMethods](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L61-L151)]

<span data-ttu-id="7ee7a-321">Depois de definir todos os métodos auxiliares, é hora de usá-los para processar a saída do modelo.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-321">Once you have defined all of the helper methods, it's time to use them to process the model output.</span></span>

<span data-ttu-id="7ee7a-322">Abaixo do método `IntersectionOverUnion`, crie o método `ParseOutputs` para processar a saída gerada pelo modelo.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-322">Below the `IntersectionOverUnion` method, create the `ParseOutputs` method to process the output generated by the model.</span></span>

```csharp
public IList<YoloBoundingBox> ParseOutputs(float[] yoloModelOutputs, float threshold = .3F)
{

}
```

<span data-ttu-id="7ee7a-323">Crie uma lista para armazenar suas caixas delimitadoras e defina variáveis dentro do método `ParseOutputs`.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-323">Create a list to store your bounding boxes and define variables inside the `ParseOutputs` method.</span></span>

[!code-csharp [BBoxList](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L155)]

<span data-ttu-id="7ee7a-324">Cada imagem é dividida em uma grade de células `13 x 13`.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-324">Each image is divided into a grid of `13 x 13` cells.</span></span> <span data-ttu-id="7ee7a-325">Cada célula contém cinco caixas delimitadoras.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-325">Each cell contains five bounding boxes.</span></span> <span data-ttu-id="7ee7a-326">Abaixo da variável `boxes`, adicione o código para processar todas as caixas em cada uma das células.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-326">Below the `boxes` variable, add code to process all of the boxes in each of the cells.</span></span>

```csharp
for (int row = 0; row < ROW_COUNT; row++)
{
    for (int column = 0; column < COL_COUNT; column++)
    {
        for (int box = 0; box < BOXES_PER_CELL; box++)
        {

        }
    }
}
```

<span data-ttu-id="7ee7a-327">Dentro do loop mais interno, calcule a posição inicial da caixa atual na saída de um modelo unidimensional.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-327">Inside the inner-most loop, calculate the starting position of the current box within the one-dimensional model output.</span></span>

[!code-csharp [ChannelDef](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L163)]

<span data-ttu-id="7ee7a-328">Diretamente abaixo disso, use o método `ExtractBoundingBoxDimensions` para obter as dimensões da caixa delimitadora atual.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-328">Directly below that, use the `ExtractBoundingBoxDimensions` method to get the dimensions of the current bounding box.</span></span>

[!code-csharp [GetBBoxDims](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L165)]

<span data-ttu-id="7ee7a-329">Em seguida, use o método `GetConfidence` para obter a confiança para a caixa delimitadora atual.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-329">Then, use the `GetConfidence` method to get the confidence for the current bounding box.</span></span>

[!code-csharp [GetConfidence](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L167)]

<span data-ttu-id="7ee7a-330">Depois disso, use o método `MapBoundingBoxToCell` para mapear a caixa delimitadora atual para a célula atual que está sendo processada.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-330">After that, use the `MapBoundingBoxToCell` method to map the current bounding box to the current cell being processed.</span></span>

[!code-csharp [MapBoundingBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L169)]

<span data-ttu-id="7ee7a-331">Antes de efetuar qualquer processamento adicional, verifique se seu valor de confiança é maior que o limite fornecido.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-331">Before doing any further processing, check whether your confidence value is greater than the threshold provided.</span></span> <span data-ttu-id="7ee7a-332">Se não for, processe a próxima caixa delimitadora.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-332">If not, process the next bounding box.</span></span>

[!code-csharp [CheckThreshold1](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L171-L172)]

<span data-ttu-id="7ee7a-333">Caso contrário, continue processando a saída.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-333">Otherwise, continue processing the output.</span></span> <span data-ttu-id="7ee7a-334">A próxima etapa é obter a distribuição de probabilidade das classes previstas para a caixa delimitadora atual usando o método `ExtractClasses`.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-334">The next step is to get the probability distribution of the predicted classes for the current bounding box using the `ExtractClasses` method.</span></span>

[!code-csharp [ExtractClasses](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L174)]

<span data-ttu-id="7ee7a-335">Em seguida, use o método `GetTopResult` para obter o valor e o índice da classe com a maior probabilidade para a caixa atual e computar sua pontuação.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-335">Then, use the `GetTopResult` method to get the value and index of the class with the highest probability for the current box and compute its score.</span></span>

[!code-csharp [GetTopResult](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L176-L177)]

<span data-ttu-id="7ee7a-336">Use o `topScore` para novamente manter somente as caixas delimitadoras que estão acima do limite especificado.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-336">Use the `topScore` to once again keep only those bounding boxes that are above the specified threshold.</span></span>

[!code-csharp [CheckThreshold2](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L179-L180)]

<span data-ttu-id="7ee7a-337">Por fim, se a caixa delimitadora atual exceder o limite, crie um objeto `BoundingBox` e adicione-o à lista `boxes`.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-337">Finally, if the current bounding box exceeds the threshold, create a new `BoundingBox` object and add it to the `boxes` list.</span></span>

[!code-csharp [AddBBoxToList](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L182-L194)]

<span data-ttu-id="7ee7a-338">Depois que todas as células da imagem forem processadas, retorne à lista `boxes`.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-338">Once all cells in the image have been processed, return the `boxes` list.</span></span> <span data-ttu-id="7ee7a-339">Adicione a seguinte instrução de retorno abaixo do loop for mais externo no método `ParseOutputs`.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-339">Add the following return statement below the outer-most for-loop in the `ParseOutputs` method.</span></span>

[!code-csharp [ReturnBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L198)]

### <a name="filter-overlapping-boxes"></a><span data-ttu-id="7ee7a-340">Filtrar as caixas sobrepostas</span><span class="sxs-lookup"><span data-stu-id="7ee7a-340">Filter overlapping boxes</span></span>

<span data-ttu-id="7ee7a-341">Agora que todas as caixas delimitadoras altamente confiáveis foram extraídas da saída do modelo, é necessário fazer a filtragem adicional para remover imagens sobrepostas.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-341">Now that all of the highly confident bounding boxes have been extracted from the model output, additional filtering needs to be done to remove overlapping images.</span></span> <span data-ttu-id="7ee7a-342">Adicione um método chamado `FilterBoundingBoxes` abaixo do método `ParseOutputs`:</span><span class="sxs-lookup"><span data-stu-id="7ee7a-342">Add a method called `FilterBoundingBoxes` below the `ParseOutputs` method:</span></span>

```csharp
public IList<YoloBoundingBox> FilterBoundingBoxes(IList<YoloBoundingBox> boxes, int limit, float threshold)
{

}
```

<span data-ttu-id="7ee7a-343">No método `FilterBoundingBoxes`, comece criando uma matriz igual ao tamanho das caixas detectadas e marcando todos os slots como ativos ou prontos para processamento.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-343">Inside the `FilterBoundingBoxes` method, start off by creating an array equal to the size of detected boxes and marking all slots as active or ready for processing.</span></span>

[!code-csharp [InitActiveSlots](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L203-L207)]

<span data-ttu-id="7ee7a-344">Em seguida, classifique a lista que contém as caixas delimitadoras em ordem decrescente com base em confiança.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-344">Then, sort the list containing your bounding boxes in descending order based on confidence.</span></span>

[!code-csharp [SortBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L209-L211)]

<span data-ttu-id="7ee7a-345">Depois disso, crie uma lista para manter os resultados filtrados.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-345">After that, create a list to hold the filtered results.</span></span>

[!code-csharp [InitFilterResult](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L213)]

<span data-ttu-id="7ee7a-346">Comece a processar cada caixa delimitadora fazendo a iteração em cada uma das caixas delimitadoras.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-346">Begin processing each bounding box by iterating over each of the bounding boxes.</span></span>

```csharp
for (int i = 0; i < boxes.Count; i++)
{

}
```

<span data-ttu-id="7ee7a-347">Dentro desse loop for, verifique se a caixa delimitadora atual pode ser processada.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-347">Inside of this for-loop, check whether the current bounding box can be processed.</span></span>

```csharp
if (isActiveBoxes[i])
{

}
```

<span data-ttu-id="7ee7a-348">Se sim, adicione a caixa delimitadora à lista de resultados.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-348">If so, add the bounding box to the list of results.</span></span> <span data-ttu-id="7ee7a-349">Se os resultados excederem o limite especificado de caixas a serem extraídas, interrompa o loop.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-349">If the results exceeds the specified limit of boxes to be extracted, break out of the loop.</span></span> <span data-ttu-id="7ee7a-350">Adicione o seguinte código dentro da instrução if.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-350">Add the following code inside the if-statement.</span></span>

[!code-csharp [AddFirstBBoxToResults](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L219-L223)]

<span data-ttu-id="7ee7a-351">Caso contrário, examine as caixas delimitadoras adjacentes.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-351">Otherwise, look at the adjacent bounding boxes.</span></span> <span data-ttu-id="7ee7a-352">Adicione o código a seguir abaixo da verificação de limite de caixa.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-352">Add the following code below the box limit check.</span></span>

```csharp
for (var j = i + 1; j < boxes.Count; j++)
{

}
```

<span data-ttu-id="7ee7a-353">Como na primeira caixa, se a caixa adjacente estiver ativa ou pronta para ser processada, use o método `IntersectionOverUnion` para verificar se a primeira caixa e a segunda caixa excedem o limite especificado.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-353">Like the first box, if the adjacent box is active or ready to be processed, use the `IntersectionOverUnion` method to check whether the first box and the second box exceed the specified threshold.</span></span> <span data-ttu-id="7ee7a-354">Adicione o código a seguir ao seu loop for mais interno.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-354">Add the following code to your inner-most for-loop.</span></span>

[!code-csharp [IOUBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L227-L239)]

<span data-ttu-id="7ee7a-355">Fora do loop for mais interno que verifica caixas delimitadoras adjacentes, veja se há alguma caixa delimitadora restante a ser processada.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-355">Outside of the inner-most for-loop that checks adjacent bounding boxes, see whether there are any remaining bounding boxes to be processed.</span></span> <span data-ttu-id="7ee7a-356">Se não houver, interrompa o loop for externo.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-356">If not, break out of the outer for-loop.</span></span>

[!code-csharp [CheckActiveSlots](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L242-L243)]

<span data-ttu-id="7ee7a-357">Por fim, fora do loop for inicial do método `FilterBoundingBoxes`, retorne os resultados:</span><span class="sxs-lookup"><span data-stu-id="7ee7a-357">Finally, outside of the initial for-loop of the `FilterBoundingBoxes` method, return the results:</span></span>

[!code-csharp [ReturnFilteredBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L246)]

<span data-ttu-id="7ee7a-358">Legal!</span><span class="sxs-lookup"><span data-stu-id="7ee7a-358">Great!</span></span> <span data-ttu-id="7ee7a-359">Agora é hora de usar esse código junto com o modelo de pontuação.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-359">Now it's time to use this code along with the model for scoring.</span></span>

## <a name="use-the-model-for-scoring"></a><span data-ttu-id="7ee7a-360">Usar o modelo para pontuação</span><span class="sxs-lookup"><span data-stu-id="7ee7a-360">Use the model for scoring</span></span>

<span data-ttu-id="7ee7a-361">Assim como ocorre com o pós-processamento, há algumas etapas nas etapas de pontuação.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-361">Just like with post-processing, there are a few steps in the scoring steps.</span></span> <span data-ttu-id="7ee7a-362">Para ajudar com isso, adicione uma classe que conterá a lógica de pontuação ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-362">To help with this, add a class that will contain the scoring logic to your project.</span></span>

1. <span data-ttu-id="7ee7a-363">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-363">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="7ee7a-364">Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *OnnxModelScorer.cs*.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-364">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *OnnxModelScorer.cs*.</span></span> <span data-ttu-id="7ee7a-365">Em seguida, selecione o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-365">Then, select the **Add** button.</span></span>

    <span data-ttu-id="7ee7a-366">O arquivo *OnnxModelScorer.cs* é aberto no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-366">The *OnnxModelScorer.cs* file opens in the code editor.</span></span> <span data-ttu-id="7ee7a-367">Adicione a seguinte instrução `using` à parte superior do *OnnxModelScorer.cs*:</span><span class="sxs-lookup"><span data-stu-id="7ee7a-367">Add the following `using` statement to the top of *OnnxModelScorer.cs*:</span></span>

    [!code-csharp [ScorerUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L1-L7)]

    <span data-ttu-id="7ee7a-368">Dentro da definição de classe `OnnxModelScorer`, adicione as variáveis a seguir.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-368">Inside the `OnnxModelScorer` class definition, add the following variables.</span></span>

    [!code-csharp [InitScorerVars](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L13-L17)]

    <span data-ttu-id="7ee7a-369">Diretamente abaixo disso, crie um construtor para a classe `OnnxModelScorer` que inicializará as variáveis definidas anteriormente.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-369">Directly below that, create a constructor for the `OnnxModelScorer` class that will initialize the previously defined variables.</span></span>

    [!code-csharp [ScorerCtor](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L19-L24)]

    <span data-ttu-id="7ee7a-370">Depois de criar o construtor, defina algumas structs que contêm variáveis relacionadas às configurações de imagem e modelo.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-370">Once you have created the constructor, define a couple of structs that contain variables related to the image and model settings.</span></span> <span data-ttu-id="7ee7a-371">Crie um struct chamado `ImageNetSettings` para conter a altura e a largura esperadas como entrada para o modelo.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-371">Create a struct called `ImageNetSettings` to contain the height and width expected as input for the model.</span></span>

    [!code-csharp [ImageNetSettingStruct](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L26-L30)]

    <span data-ttu-id="7ee7a-372">Depois disso, crie outro struct chamado `TinyYoloModelSettings`, que contém os nomes das camadas de entrada e saída do modelo.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-372">After that, create another struct called `TinyYoloModelSettings` which contains the names of the input and output layers of the model.</span></span> <span data-ttu-id="7ee7a-373">Para visualizar o nome das camadas de entrada e saída do modelo, você pode usar uma ferramenta como o [Netron.](https://github.com/lutzroeder/netron)</span><span class="sxs-lookup"><span data-stu-id="7ee7a-373">To visualize the name of the input and output layers of the model, you can use a tool like [Netron](https://github.com/lutzroeder/netron).</span></span>

    [!code-csharp [YoloSettingsStruct](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L32-L43)]

    <span data-ttu-id="7ee7a-374">Em seguida, crie o primeiro conjunto de métodos usado para pontuação.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-374">Next, create the first set of methods use for scoring.</span></span> <span data-ttu-id="7ee7a-375">Crie o método `LoadModel` dentro de sua classe `OnnxModelScorer`.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-375">Create the `LoadModel` method inside of your `OnnxModelScorer` class.</span></span>

    ```csharp
    private ITransformer LoadModel(string modelLocation)
    {

    }
    ```

    <span data-ttu-id="7ee7a-376">No método `LoadModel`, adicione o código a seguir para registrar em log.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-376">Inside the `LoadModel` method, add the following code for logging.</span></span>

    [!code-csharp [LoadModelLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L47-L49)]

    <span data-ttu-id="7ee7a-377">Os pipelines do ML.NET precisam conhecer o esquema de dados para operarem quando o método [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) for chamado.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-377">ML.NET pipelines need to know the data schema to operate on when the [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) method is called.</span></span> <span data-ttu-id="7ee7a-378">Nesse caso, um processo semelhante ao treinamento será usado.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-378">In this case, a process similar to training will be used.</span></span> <span data-ttu-id="7ee7a-379">No entanto, como nenhum treinamento real está acontecendo, é aceitável usar um [`IDataView`](xref:Microsoft.ML.IDataView) vazio.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-379">However, because no actual training is happening, it is acceptable to use an empty [`IDataView`](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="7ee7a-380">Crie um novo [`IDataView`](xref:Microsoft.ML.IDataView) para o pipeline de uma lista vazia.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-380">Create a new [`IDataView`](xref:Microsoft.ML.IDataView) for the pipeline from an empty list.</span></span>

    [!code-csharp [LoadEmptyIDV](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L52)]

    <span data-ttu-id="7ee7a-381">Abaixo disso, defina o pipeline.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-381">Below that, define the pipeline.</span></span> <span data-ttu-id="7ee7a-382">O pipeline consistirá em quatro transformações.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-382">The pipeline will consist of four transforms.</span></span>

    - <span data-ttu-id="7ee7a-383">[`LoadImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*) carrega a imagem como um bitmap.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-383">[`LoadImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*) loads the image as a Bitmap.</span></span>
    - <span data-ttu-id="7ee7a-384">[`ResizeImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.ResizeImages*) redimensiona a imagem para o tamanho especificado (nesse caso, `416 x 416`).</span><span class="sxs-lookup"><span data-stu-id="7ee7a-384">[`ResizeImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.ResizeImages*) rescales the image to the size specified (in this case, `416 x 416`).</span></span>
    - <span data-ttu-id="7ee7a-385">[`ExtractPixels`](xref:Microsoft.ML.ImageEstimatorsCatalog.ExtractPixels*) altera a representação de pixel da imagem de um bitmap para um vetor numérico.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-385">[`ExtractPixels`](xref:Microsoft.ML.ImageEstimatorsCatalog.ExtractPixels*) changes the pixel representation of the image from a Bitmap to a numerical vector.</span></span>
    - <span data-ttu-id="7ee7a-386">[`ApplyOnnxModel`](xref:Microsoft.ML.OnnxCatalog.ApplyOnnxModel*) carrega o modelo ONNX e o usa para pontuar os dados fornecidos.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-386">[`ApplyOnnxModel`](xref:Microsoft.ML.OnnxCatalog.ApplyOnnxModel*) loads the ONNX model and uses it to score on the data provided.</span></span>

    <span data-ttu-id="7ee7a-387">Defina o pipeline no método `LoadModel` abaixo da variável `data`.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-387">Define your pipeline in the `LoadModel` method below the `data` variable.</span></span>

    [!code-csharp [ScoringPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L55-L58)]

    <span data-ttu-id="7ee7a-388">Agora é hora de instanciar o modelo para pontuação.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-388">Now it's time to instantiate the model for scoring.</span></span> <span data-ttu-id="7ee7a-389">Chame o método [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) no pipeline e retorne-o para processamento adicional.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-389">Call the [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) method on the pipeline and return it for further processing.</span></span>

    [!code-csharp [FitReturnModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L61-L63)]

<span data-ttu-id="7ee7a-390">Depois que o modelo for carregado, ele poderá ser usado para fazer previsões.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-390">Once the model is loaded, it can then be used to make predictions.</span></span> <span data-ttu-id="7ee7a-391">Para facilitar esse processo, crie um método chamado `PredictDataUsingModel` abaixo do método `LoadModel`.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-391">To facilitate that process, create a method called `PredictDataUsingModel` below the `LoadModel` method.</span></span>

```csharp
private IEnumerable<float[]> PredictDataUsingModel(IDataView testData, ITransformer model)
{

}
```

<span data-ttu-id="7ee7a-392">No `PredictDataUsingModel`, adicione o código a seguir para registrar em log.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-392">Inside the `PredictDataUsingModel`, add the following code for logging.</span></span>

[!code-csharp [PredictDataLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L68-L71)]

<span data-ttu-id="7ee7a-393">Em seguida, use o método [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) para pontuar os dados.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-393">Then, use the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method to score the data.</span></span>

[!code-csharp [ScoreImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L73)]

<span data-ttu-id="7ee7a-394">Extraia as probabilidades previstas e retorne-as para processamento adicional.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-394">Extract the predicted probabilities and return them for additional processing.</span></span>

[!code-csharp [ReturnModelOutput](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L75-L77)]

<span data-ttu-id="7ee7a-395">Agora que ambas as etapas estão configuradas, combine-as em um único método.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-395">Now that both steps are set up, combine them into a single method.</span></span> <span data-ttu-id="7ee7a-396">Abaixo do método `PredictDataUsingModel`, adicione um novo método chamado `Score`.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-396">Below the `PredictDataUsingModel` method, add a new method called `Score`.</span></span>

[!code-csharp [ScoreMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L80-L85)]

<span data-ttu-id="7ee7a-397">Quase lá!</span><span class="sxs-lookup"><span data-stu-id="7ee7a-397">Almost there!</span></span> <span data-ttu-id="7ee7a-398">Agora é hora de colocar tudo em uso.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-398">Now it's time to put it all to use.</span></span>

## <a name="detect-objects"></a><span data-ttu-id="7ee7a-399">Detectar objetos</span><span class="sxs-lookup"><span data-stu-id="7ee7a-399">Detect objects</span></span>

<span data-ttu-id="7ee7a-400">Agora que toda a configuração foi concluída, é hora de detectar alguns objetos.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-400">Now that all of the setup is complete, it's time to detect some objects.</span></span> <span data-ttu-id="7ee7a-401">Comece adicionando referências às pontuações e ao analisador na classe *Program.cs*.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-401">Start off by adding references to the scorer and parser in your *Program.cs* class.</span></span>

[!code-csharp [ReferenceScorerParser](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L8-L9)]

### <a name="score-and-parse-model-outputs"></a><span data-ttu-id="7ee7a-402">Pontuar e analisar saídas do modelo</span><span class="sxs-lookup"><span data-stu-id="7ee7a-402">Score and parse model outputs</span></span>

<span data-ttu-id="7ee7a-403">Dentro do método `Main` da classe *Program.cs*, adicione uma instrução try-catch.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-403">Inside the `Main` method of your *Program.cs* class, add a try-catch statement.</span></span>

```csharp
try
{

}
catch (Exception ex)
{
    Console.WriteLine(ex.ToString());
}
```

<span data-ttu-id="7ee7a-404">Dentro do bloco `try`, comece a implementar a lógica de detecção de objetos.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-404">Inside of the `try` block, start implementing the object detection logic.</span></span> <span data-ttu-id="7ee7a-405">Primeiro, carregue os dados em um [`IDataView`](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="7ee7a-405">First, load the data into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

[!code-csharp [LoadData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L29-L30)]

<span data-ttu-id="7ee7a-406">Em seguida, crie uma instância de `OnnxModelScorer` e use-a para pontuar os dados carregados.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-406">Then, create an instance of `OnnxModelScorer` and use it to score the loaded data.</span></span>

[!code-csharp [ScoreData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L33-L36)]

<span data-ttu-id="7ee7a-407">Agora é hora da etapa de pós-processamento.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-407">Now it's time for the post-processing step.</span></span> <span data-ttu-id="7ee7a-408">Crie uma instância de `YoloOutputParser` e use-a para processar a saída do modelo.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-408">Create an instance of `YoloOutputParser` and use it to process the model output.</span></span>

[!code-csharp [ParsePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L39-L44)]

<span data-ttu-id="7ee7a-409">Após o processamento da saída do modelo, é hora de desenhar as caixas delimitadoras nas imagens.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-409">Once the model output has been processed, it's time to draw the bounding boxes on the images.</span></span>

### <a name="visualize-predictions"></a><span data-ttu-id="7ee7a-410">Visualizar previsões</span><span class="sxs-lookup"><span data-stu-id="7ee7a-410">Visualize predictions</span></span>

<span data-ttu-id="7ee7a-411">Depois que o modelo pontua as imagens e as saídas são processadas, as caixas delimitadoras precisam ser desenhadas na imagem.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-411">After the model has scored the images and the outputs have been processed, the bounding boxes have to be drawn on the image.</span></span> <span data-ttu-id="7ee7a-412">Para fazer isso, adicione um método chamado `DrawBoundingBox` abaixo do método `GetAbsolutePath` dentro de *Program.cs*.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-412">To do so, add a method called `DrawBoundingBox` below the `GetAbsolutePath` method inside of *Program.cs*.</span></span>

```csharp
private static void DrawBoundingBox(string inputImageLocation, string outputImageLocation, string imageName, IList<YoloBoundingBox> filteredBoundingBoxes)
{

}
```

<span data-ttu-id="7ee7a-413">Primeiro, carregue a imagem e obtenha as dimensões de altura e largura no método `DrawBoundingBox`.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-413">First, load the image and get the height and width dimensions in the `DrawBoundingBox` method.</span></span>

[!code-csharp [LoadImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L78-L81)]

<span data-ttu-id="7ee7a-414">Em seguida, crie um loop for-each para iterar sobre cada uma das caixas delimitadoras detectadas pelo modelo.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-414">Then, create a for-each loop to iterate over each of the bounding boxes detected by the model.</span></span>

```csharp
foreach (var box in filteredBoundingBoxes)
{

}
```

<span data-ttu-id="7ee7a-415">Dentro do loop for-each, obtenha as dimensões da caixa delimitadora.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-415">Inside of the for-each loop, get the dimensions of the bounding box.</span></span>

[!code-csharp [GetBBoxDimensions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L86-L89)]

<span data-ttu-id="7ee7a-416">Como as dimensões da caixa delimitadora correspondem à entrada do modelo de `416 x 416`, dimensione as dimensões da caixa delimitadora para corresponder ao tamanho real da imagem.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-416">Because the dimensions of the bounding box correspond to the model input of `416 x 416`, scale the bounding box dimensions to match the actual size of the image.</span></span>

[!code-csharp [ScaleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L92-L95)]

<span data-ttu-id="7ee7a-417">Em seguida, defina um modelo para o texto que será exibido acima de cada caixa delimitadora.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-417">Then, define a template for text that will appear above each bounding box.</span></span> <span data-ttu-id="7ee7a-418">O texto conterá a classe do objeto dentro da respectiva caixa delimitadora, bem como a confiança.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-418">The text will contain the class of the object inside of the respective bounding box as well as the confidence.</span></span>

[!code-csharp [DefineBBoxText](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L98)]

<span data-ttu-id="7ee7a-419">Para desenhar na imagem, converta-a em um objeto [`Graphics`](xref:System.Drawing.Graphics).</span><span class="sxs-lookup"><span data-stu-id="7ee7a-419">In order to draw on the image, convert it to a [`Graphics`](xref:System.Drawing.Graphics) object.</span></span>

```csharp
using (Graphics thumbnailGraphic = Graphics.FromImage(image))
{

}
```

<span data-ttu-id="7ee7a-420">Dentro do bloco de código `using`, ajuste as configurações de objeto [`Graphics`](xref:System.Drawing.Graphics) do gráfico.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-420">Inside the `using` code block, tune the graphic's [`Graphics`](xref:System.Drawing.Graphics) object settings.</span></span>

[!code-csharp [TuneGraphicSettings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L102-L104)]

<span data-ttu-id="7ee7a-421">Abaixo disso, defina as opções de fonte e cor para o texto e a caixa delimitadora.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-421">Below that, set the font and color options for the text and bounding box.</span></span>

[!code-csharp [SetColorOptions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L106-L114)]

<span data-ttu-id="7ee7a-422">Crie e preencha um retângulo acima da caixa delimitadora para conter o texto usando o método [`FillRectangle`](xref:System.Drawing.Graphics.FillRectangle*).</span><span class="sxs-lookup"><span data-stu-id="7ee7a-422">Create and fill a rectangle above the bounding box to contain the text using the [`FillRectangle`](xref:System.Drawing.Graphics.FillRectangle*) method.</span></span> <span data-ttu-id="7ee7a-423">Isso ajudará a comparar o texto e a melhorar a legibilidade.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-423">This will help contrast the text and improve readability.</span></span>

[!code-csharp [DrawTextBackground](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L117)]

<span data-ttu-id="7ee7a-424">Em seguida, desenhe o texto e a caixa delimitadora na imagem usando os métodos [`DrawString`](xref:System.Drawing.Graphics.DrawString*) e [`DrawRectangle`](xref:System.Drawing.Graphics.DrawRectangle*).</span><span class="sxs-lookup"><span data-stu-id="7ee7a-424">Then, Draw the text and bounding box on the image using the [`DrawString`](xref:System.Drawing.Graphics.DrawString*) and [`DrawRectangle`](xref:System.Drawing.Graphics.DrawRectangle*) methods.</span></span>

[!code-csharp [DrawClassAndBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L118-L121)]

<span data-ttu-id="7ee7a-425">Fora do loop for-each, adicione o código para salvar as imagens no `outputDirectory`.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-425">Outside of the for-each loop, add code to save the images in the `outputDirectory`.</span></span>

[!code-csharp [SaveImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L125-L130)]

<span data-ttu-id="7ee7a-426">Para obter comentários adicionais de que o aplicativo está fazendo previsões conforme esperado em runtime, adicione um método chamado `LogDetectedObjects` abaixo do método `DrawBoundingBox` no arquivo *Program.cs* para gerar os objetos detectados no console.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-426">For additional feedback that the application is making predictions as expected at runtime, add a method called `LogDetectedObjects` below the `DrawBoundingBox` method in the *Program.cs* file to output the detected objects to the console.</span></span>

[!code-csharp [LogOutputs](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L133-L143)]

<span data-ttu-id="7ee7a-427">Agora que você tem métodos auxiliares para criar comentários visuais com base nas previsões, adicione um loop for para iterar em cada uma das imagens pontuadas.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-427">Now that you have helper methods to create visual feedback from the predictions, add a for-loop to iterate over each of the scored images.</span></span>

```csharp
for (var i = 0; i < images.Count(); i++)
{

}
```

<span data-ttu-id="7ee7a-428">Dentro do loop for, obtenha o nome do arquivo de imagem e as caixas delimitadoras associadas a ele.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-428">Inside of the for-loop, get the name of the image file and the bounding boxes associated with it.</span></span>

[!code-csharp [GetImageFileName](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L49-L50)]

<span data-ttu-id="7ee7a-429">Abaixo disso, use o método `DrawBoundingBox` para desenhar as caixas delimitadoras na imagem.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-429">Below that, use the `DrawBoundingBox` method to draw the bounding boxes on the image.</span></span>

[!code-csharp [DrawBBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L52)]

<span data-ttu-id="7ee7a-430">Por fim, use o método `LogDetectedObjects` para gerar previsões no console.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-430">Lastly, use the `LogDetectedObjects` method to output predictions to the console.</span></span>

[!code-csharp [LogPredictionsOutput](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L54)]

<span data-ttu-id="7ee7a-431">Após a instrução try-catch, adicione a lógica complementar para indicar que o processo terminou a execução.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-431">After the try-catch statement, add additional logic to indicate the process is done running.</span></span>

[!code-csharp [EndProcessLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L62-L63)]

<span data-ttu-id="7ee7a-432">É só isso!</span><span class="sxs-lookup"><span data-stu-id="7ee7a-432">That's it!</span></span>

## <a name="results"></a><span data-ttu-id="7ee7a-433">Resultados</span><span class="sxs-lookup"><span data-stu-id="7ee7a-433">Results</span></span>

<span data-ttu-id="7ee7a-434">Depois de seguir as etapas anteriores, execute o aplicativo de console (Ctrl+F5).</span><span class="sxs-lookup"><span data-stu-id="7ee7a-434">After following the previous steps, run your console app (Ctrl + F5).</span></span> <span data-ttu-id="7ee7a-435">O resultado deverá ser semelhante à seguinte saída.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-435">Your results should be similar to the following output.</span></span> <span data-ttu-id="7ee7a-436">Você poderá ver avisos ou mensagens de processamento, mas essas mensagens foram removidas dos resultados a seguir para maior clareza.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-436">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

```console
=====Identify the objects in the images=====

.....The objects in the image image1.jpg are detected as below....
car and its Confidence score: 0.9697262
car and its Confidence score: 0.6674225
person and its Confidence score: 0.5226039
car and its Confidence score: 0.5224892
car and its Confidence score: 0.4675332

.....The objects in the image image2.jpg are detected as below....
cat and its Confidence score: 0.6461141
cat and its Confidence score: 0.6400049

.....The objects in the image image3.jpg are detected as below....
chair and its Confidence score: 0.840578
chair and its Confidence score: 0.796363
diningtable and its Confidence score: 0.6056048
diningtable and its Confidence score: 0.3737402

.....The objects in the image image4.jpg are detected as below....
dog and its Confidence score: 0.7608147
person and its Confidence score: 0.6321323
dog and its Confidence score: 0.5967442
person and its Confidence score: 0.5730394
person and its Confidence score: 0.5551759

========= End of Process..Hit any Key ========
```

<span data-ttu-id="7ee7a-437">Para ver as imagens com as caixas delimitadoras, navegue até o diretório `assets/images/output/`.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-437">To see the images with bounding boxes, navigate to the `assets/images/output/` directory.</span></span> <span data-ttu-id="7ee7a-438">Abaixo está um exemplo de uma das imagens processadas.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-438">Below is a sample from one of the processed images.</span></span>

![](./media/object-detection-onnx/image3.jpg)

<span data-ttu-id="7ee7a-439">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="7ee7a-439">Congratulations!</span></span> <span data-ttu-id="7ee7a-440">Você criou com êxito um modelo de machine learning para detecção de objetos reutilizando um modelo `ONNX` pré-treinado no ML.NET.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-440">You've now successfully built a machine learning model for object detection by reusing a pre-trained `ONNX` model in ML.NET.</span></span>

<span data-ttu-id="7ee7a-441">Você pode encontrar o código-fonte para este tutorial no repositório [dotnet/samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx).</span><span class="sxs-lookup"><span data-stu-id="7ee7a-441">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) repository.</span></span>

<span data-ttu-id="7ee7a-442">Neste tutorial, você aprendeu como:</span><span class="sxs-lookup"><span data-stu-id="7ee7a-442">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="7ee7a-443">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="7ee7a-443">Understand the problem</span></span>
> - <span data-ttu-id="7ee7a-444">Saiba o que é o ONNX e como ele funciona com o ML.NET</span><span class="sxs-lookup"><span data-stu-id="7ee7a-444">Learn what ONNX is and how it works with ML.NET</span></span>
> - <span data-ttu-id="7ee7a-445">Entender o modelo</span><span class="sxs-lookup"><span data-stu-id="7ee7a-445">Understand the model</span></span>
> - <span data-ttu-id="7ee7a-446">Reutilizar o modelo pré-treinado</span><span class="sxs-lookup"><span data-stu-id="7ee7a-446">Reuse the pre-trained model</span></span>
> - <span data-ttu-id="7ee7a-447">Detectar objetos com um modelo carregado</span><span class="sxs-lookup"><span data-stu-id="7ee7a-447">Detect objects with a loaded model</span></span>

<span data-ttu-id="7ee7a-448">Confira o repositório GitHub de exemplos de Machine Learning para explorar um exemplo de detecção de objetos expandido.</span><span class="sxs-lookup"><span data-stu-id="7ee7a-448">Check out the Machine Learning samples GitHub repository to explore an expanded object detection sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="7ee7a-449">dotnet/machinelearning-samples GitHub repository</span><span class="sxs-lookup"><span data-stu-id="7ee7a-449">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/DeepLearning_ObjectDetection_Onnx)
