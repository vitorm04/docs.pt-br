---
title: ConfigurationCodeGenerator
ms.date: 03/30/2017
ms.assetid: 3913aae8-165f-4014-9262-7fe426f90cb2
ms.openlocfilehash: d64be95f71f840e08ede63e1c1f14ee08e52ce97
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84592470"
---
# <a name="configurationcodegenerator"></a><span data-ttu-id="2a059-102">ConfigurationCodeGenerator</span><span class="sxs-lookup"><span data-stu-id="2a059-102">ConfigurationCodeGenerator</span></span>
<span data-ttu-id="2a059-103">O ConfigurationCodeGenerator é uma ferramenta que você pode usar para expor suas implementações de canal personalizadas para o sistema de configuração.</span><span class="sxs-lookup"><span data-stu-id="2a059-103">The ConfigurationCodeGenerator is a tool that you can use to expose your custom channel implementations to the configuration system.</span></span> <span data-ttu-id="2a059-104">Isso permite que os usuários do seu canal personalizado configurem seu canal usando um arquivo. config, assim como configurariam uma associação fornecida pelo sistema, como `NetTcpBinding` ou uma ligação personalizada usando o `TcpTransportBindingElement` .</span><span class="sxs-lookup"><span data-stu-id="2a059-104">This allows users of your custom channel to configure your channel by using a .config file just as they would configure a system-provided binding such as `NetTcpBinding` or a custom binding using the `TcpTransportBindingElement`.</span></span>  
  
 <span data-ttu-id="2a059-105">Quando você escreve um canal personalizado e o expõe para o modelo de programação usando um novo `BindingElement` ou `Binding` , você deve criar um conjunto de classes para tornar o `BindingElement` ou `Binding` configurável usando um arquivo. config.</span><span class="sxs-lookup"><span data-stu-id="2a059-105">When you write a custom channel and expose it to the programming model by using a new `BindingElement` or `Binding`, you must create a set of classes to make the `BindingElement` or `Binding` configurable using a .config file.</span></span> <span data-ttu-id="2a059-106">Você pode usar a ferramenta ConfigurationCodeGenerator para gerar essas classes e aprimorar a experiência do cliente.</span><span class="sxs-lookup"><span data-stu-id="2a059-106">You can use the ConfigurationCodeGenerator tool to generate these classes and enhance your customer's experience.</span></span>  
  
### <a name="to-build-the-tool"></a><span data-ttu-id="2a059-107">Para criar a ferramenta</span><span class="sxs-lookup"><span data-stu-id="2a059-107">To build the tool</span></span>  
  
1. <span data-ttu-id="2a059-108">Para compilar a solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2a059-108">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="2a059-109">A criação da solução gera um arquivo: ConfigurationCodeGenerator. exe.</span><span class="sxs-lookup"><span data-stu-id="2a059-109">Building the solution generates one file: ConfigurationCodeGenerator.exe.</span></span> <span data-ttu-id="2a059-110">O arquivo SampleRun. cmd tem uma linha de comando de exemplo que mostra como usar essa ferramenta para gerar as classes para o exemplo de [transporte: UDP](transport-udp.md) .</span><span class="sxs-lookup"><span data-stu-id="2a059-110">The file SampleRun.cmd has a sample command line that shows how to use this tool to generate the classes for the [Transport: UDP](transport-udp.md) sample.</span></span>  
  
### <a name="to-run-the-tool"></a><span data-ttu-id="2a059-111">Para executar a ferramenta</span><span class="sxs-lookup"><span data-stu-id="2a059-111">To run the tool</span></span>  
  
1. <span data-ttu-id="2a059-112">No prompt de comando, digite o seguinte se você tiver um `BindingElement` tipo personalizado e um `Binding` tipo personalizado:</span><span class="sxs-lookup"><span data-stu-id="2a059-112">At the command prompt type the following if you have both a custom `BindingElement` type and a custom `Binding` type:</span></span>  
  
    ```console  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereTheseTypesAreDefined  
    ```  
  
     <span data-ttu-id="2a059-113">Ou digite o seguinte se você tiver apenas um `BindingElement` tipo personalizado:</span><span class="sxs-lookup"><span data-stu-id="2a059-113">Or type the following if you have only a custom `BindingElement` type:</span></span>  
  
    ```console  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /dll: TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     <span data-ttu-id="2a059-114">Ou digite o seguinte se você tiver apenas um `Binding` tipo personalizado:</span><span class="sxs-lookup"><span data-stu-id="2a059-114">Or type the following if you have only a custom `Binding` type:</span></span>  
  
    ```console  
    ConfigurationCodeGenerator.exe /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     <span data-ttu-id="2a059-115">O comando gera três arquivos. cs para o `BindingElement` (se você especificou a opção/be:), cinco arquivos. cs para o padrão `Binding` (se você especificou a opção/SB:) e um arquivo. xml.</span><span class="sxs-lookup"><span data-stu-id="2a059-115">The command generates three .cs files for the `BindingElement` (if you specified the /be: option), five .cs files for the standard `Binding` (if you specified the /sb: option), and a .xml file.</span></span>  
  
    1. <span data-ttu-id="2a059-116">Se você usou a opção/be, um dos arquivos. cs implementa o `BindingElementExtensionSection` para seu elemento Binding.</span><span class="sxs-lookup"><span data-stu-id="2a059-116">If you used the /be option, one of the .cs files implements the `BindingElementExtensionSection` for your binding element.</span></span> <span data-ttu-id="2a059-117">Esse código expõe seu `BindingElement` para o sistema de configuração, para que outras associações personalizadas possam usar seu elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="2a059-117">This code exposes your `BindingElement` to the configuration system, so that other custom bindings can use your binding element.</span></span> <span data-ttu-id="2a059-118">Os outros arquivos têm classes que representam padrões e constantes.</span><span class="sxs-lookup"><span data-stu-id="2a059-118">The other files have classes that represent defaults and constants.</span></span> <span data-ttu-id="2a059-119">Os arquivos têm `//TODO` comentários para lembrá-lo de atualizar os valores padrão.</span><span class="sxs-lookup"><span data-stu-id="2a059-119">The files have `//TODO` comments to remind you to update the default values.</span></span>  
  
    2. <span data-ttu-id="2a059-120">Se você especificou a opção/SB, dois dos arquivos. cs implementam um `StandardBindingElement` e um `StandardBindingCollectionElement` , respectivamente, que expõem a ligação padrão com o sistema de configuração.</span><span class="sxs-lookup"><span data-stu-id="2a059-120">If you specified the /sb option, two of the .cs files implement a `StandardBindingElement` and a `StandardBindingCollectionElement` respectively, which exposes your standard binding to the configuration system.</span></span> <span data-ttu-id="2a059-121">Os outros arquivos têm classes que representam padrões e constantes.</span><span class="sxs-lookup"><span data-stu-id="2a059-121">The other files have classes that represent defaults and constants.</span></span> <span data-ttu-id="2a059-122">Os arquivos têm `//TODO` comentários para lembrá-lo de atualizar os valores padrão.</span><span class="sxs-lookup"><span data-stu-id="2a059-122">The files have `//TODO` comments to remind you to update the default values.</span></span>  
  
         <span data-ttu-id="2a059-123">Se você especificou a opção/SB: o CodeToAddTo \<*YourStdBinding*> . cs tem código que você deve adicionar manualmente à classe que implementa sua associação padrão.</span><span class="sxs-lookup"><span data-stu-id="2a059-123">If you specified the /sb: option the CodeToAddTo\<*YourStdBinding*>.cs has code that you must manually add into the class that implements your standard binding.</span></span>  
  
     <span data-ttu-id="2a059-124">O arquivo SampleConfig. xml contém o código de configuração que você deve adicionar ao arquivo de configuração que registra os manipuladores definidos na etapa 1 ou 2 anterior.</span><span class="sxs-lookup"><span data-stu-id="2a059-124">The SampleConfig.xml file contains the configuration code that you must add to the configuration file that registers the handlers defined in the previous step 1 or 2.</span></span>  
