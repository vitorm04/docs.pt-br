---
title: ConfigurationCodeGenerator
ms.date: 03/30/2017
ms.assetid: 3913aae8-165f-4014-9262-7fe426f90cb2
ms.openlocfilehash: eb547c89dc5d4af9330a6881d64f433de9bdad94
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54669075"
---
# <a name="configurationcodegenerator"></a><span data-ttu-id="0477c-102">ConfigurationCodeGenerator</span><span class="sxs-lookup"><span data-stu-id="0477c-102">ConfigurationCodeGenerator</span></span>
<span data-ttu-id="0477c-103">O ConfigurationCodeGenerator é uma ferramenta que você pode usar para expor suas implementações de canal personalizado para o sistema de configuração.</span><span class="sxs-lookup"><span data-stu-id="0477c-103">The ConfigurationCodeGenerator is a tool that you can use to expose your custom channel implementations to the configuration system.</span></span> <span data-ttu-id="0477c-104">Isso permite que os usuários do seu canal personalizado configurar seu canal usando um arquivo. config exatamente como eles configuraria uma fornecida pelo sistema de associação, como `NetTcpBinding` ou um personalizado de associação usando o `TcpTransportBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="0477c-104">This allows users of your custom channel to configure your channel by using a .config file just as they would configure a system-provided binding such as `NetTcpBinding` or a custom binding using the `TcpTransportBindingElement`.</span></span>  
  
 <span data-ttu-id="0477c-105">Quando você escrever um canal personalizado e expô-lo para o modelo de programação usando uma nova `BindingElement` ou `Binding`, você deve criar um conjunto de classes para tornar o `BindingElement` ou `Binding` configurável usando um arquivo. config.</span><span class="sxs-lookup"><span data-stu-id="0477c-105">When you write a custom channel and expose it to the programming model by using a new `BindingElement` or `Binding`, you must create a set of classes to make the `BindingElement` or `Binding` configurable using a .config file.</span></span> <span data-ttu-id="0477c-106">Você pode usar a ferramenta ConfigurationCodeGenerator para gerar essas classes e aprimorar a experiência do cliente.</span><span class="sxs-lookup"><span data-stu-id="0477c-106">You can use the ConfigurationCodeGenerator tool to generate these classes and enhance your customer's experience.</span></span>  
  
### <a name="to-build-the-tool"></a><span data-ttu-id="0477c-107">Para a ferramenta de compilação</span><span class="sxs-lookup"><span data-stu-id="0477c-107">To build the tool</span></span>  
  
1.  <span data-ttu-id="0477c-108">Para criar a solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0477c-108">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="0477c-109">Compilando a solução gera um arquivo: ConfigurationCodeGenerator.exe.</span><span class="sxs-lookup"><span data-stu-id="0477c-109">Building the solution generates one file: ConfigurationCodeGenerator.exe.</span></span> <span data-ttu-id="0477c-110">O arquivo SampleRun.cmd tem uma linha de comando de exemplo que mostra como usar essa ferramenta para gerar as classes para o [transporte: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="0477c-110">The file SampleRun.cmd has a sample command line that shows how to use this tool to generate the classes for the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span>  
  
### <a name="to-run-the-tool"></a><span data-ttu-id="0477c-111">Para executar a ferramenta</span><span class="sxs-lookup"><span data-stu-id="0477c-111">To run the tool</span></span>  
  
1.  <span data-ttu-id="0477c-112">No prompt de comando, digite o seguinte se você tiver uma personalizadas `BindingElement` personalizado e tipo `Binding` tipo:</span><span class="sxs-lookup"><span data-stu-id="0477c-112">At the command prompt type the following if you have both a custom `BindingElement` type and a custom `Binding` type:</span></span>  
  
    ```  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereTheseTypesAreDefined  
    ```  
  
     <span data-ttu-id="0477c-113">Ou digite o seguinte se você tiver apenas um personalizado `BindingElement` tipo:</span><span class="sxs-lookup"><span data-stu-id="0477c-113">Or type the following if you have only a custom `BindingElement` type:</span></span>  
  
    ```  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /dll: TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     <span data-ttu-id="0477c-114">Ou digite o seguinte se você tiver apenas um personalizado `Binding` tipo:</span><span class="sxs-lookup"><span data-stu-id="0477c-114">Or type the following if you have only a custom `Binding` type:</span></span>  
  
    ```  
    ConfigurationCodeGenerator.exe /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     <span data-ttu-id="0477c-115">O comando gera três arquivos. cs para o `BindingElement` (se você tiver especificado a ser: opção), cinco arquivos. cs para o padrão `Binding` (se você tiver especificado o /sb: opção) e um arquivo. XML.</span><span class="sxs-lookup"><span data-stu-id="0477c-115">The command generates three .cs files for the `BindingElement` (if you specified the /be: option), five .cs files for the standard `Binding` (if you specified the /sb: option), and a .xml file.</span></span>  
  
    1.  <span data-ttu-id="0477c-116">Se você usou a opção /be, uma da. cs arquivos implementa o `BindingElementExtensionSection` para seu elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="0477c-116">If you used the /be option, one of the .cs files implements the `BindingElementExtensionSection` for your binding element.</span></span> <span data-ttu-id="0477c-117">Este código expõe seu `BindingElement` ao sistema de configuração, para que os outros ligações personalizadas podem usar o elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="0477c-117">This code exposes your `BindingElement` to the configuration system, so that other custom bindings can use your binding element.</span></span> <span data-ttu-id="0477c-118">Os outros arquivos têm classes que representam os padrões e constantes.</span><span class="sxs-lookup"><span data-stu-id="0477c-118">The other files have classes that represent defaults and constants.</span></span> <span data-ttu-id="0477c-119">Os arquivos têm `//TODO` comentários para lembrá-lo para atualizar os valores padrão.</span><span class="sxs-lookup"><span data-stu-id="0477c-119">The files have `//TODO` comments to remind you to update the default values.</span></span>  
  
    2.  <span data-ttu-id="0477c-120">Se você especificou a opção /sb, dois dos arquivos. cs implementam uma `StandardBindingElement` e um `StandardBindingCollectionElement` respectivamente, que expõe a associação padrão para o sistema de configuração.</span><span class="sxs-lookup"><span data-stu-id="0477c-120">If you specified the /sb option, two of the .cs files implement a `StandardBindingElement` and a `StandardBindingCollectionElement` respectively, which exposes your standard binding to the configuration system.</span></span> <span data-ttu-id="0477c-121">Os outros arquivos têm classes que representam os padrões e constantes.</span><span class="sxs-lookup"><span data-stu-id="0477c-121">The other files have classes that represent defaults and constants.</span></span> <span data-ttu-id="0477c-122">Os arquivos têm `//TODO` comentários para lembrá-lo para atualizar os valores padrão.</span><span class="sxs-lookup"><span data-stu-id="0477c-122">The files have `//TODO` comments to remind you to update the default values.</span></span>  
  
         <span data-ttu-id="0477c-123">Se você tiver especificado o /sb: opção de CodeToAddTo\<*YourStdBinding*>. cs tem código que você deve adicionar manualmente para a classe que implementa a associação padrão.</span><span class="sxs-lookup"><span data-stu-id="0477c-123">If you specified the /sb: option the CodeToAddTo\<*YourStdBinding*>.cs has code that you must manually add into the class that implements your standard binding.</span></span>  
  
     <span data-ttu-id="0477c-124">O arquivo de SampleConfig.xml contém o código de configuração que você deve adicionar ao arquivo de configuração que registra os manipuladores definidos na etapa anterior 1 ou 2.</span><span class="sxs-lookup"><span data-stu-id="0477c-124">The SampleConfig.xml file contains the configuration code that you must add to the configuration file that registers the handlers defined in the previous step 1 or 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0477c-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0477c-125">See also</span></span>
