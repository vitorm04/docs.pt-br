---
title: "Instruções passo a passo - acessando um serviço Web por meio de provedores de tipos (F #)"
description: "Saiba como usar o provedor de tipo WSDL Web Services Description Language (), disponível no F # 3.0 para acessar um serviço em WSDL."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 63374fa9-8fb8-43ac-bcb9-ef2290d9f851
ms.openlocfilehash: 2929198172a4e9f908daa64af19208e07859263f
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2018
---
# <a name="walkthrough-accessing-a-web-service-by-using-type-providers"></a><span data-ttu-id="97987-104">Instruções passo a passo: acessando um serviço Web por meio de provedores de tipos</span><span class="sxs-lookup"><span data-stu-id="97987-104">Walkthrough: Accessing a Web Service by Using Type Providers</span></span>

> [!NOTE]
<span data-ttu-id="97987-105">Este guia foi escrito para F # 3.0 e será atualizado.</span><span class="sxs-lookup"><span data-stu-id="97987-105">This guide was written for F# 3.0 and will be updated.</span></span>  <span data-ttu-id="97987-106">Consulte [FSharp.Data](https://fsharp.github.io/FSharp.Data/) para provedores de tipo de plataforma cruzada atualizados.</span><span class="sxs-lookup"><span data-stu-id="97987-106">See [FSharp.Data](https://fsharp.github.io/FSharp.Data/) for up-to-date, cross-platform type providers.</span></span>

> [!NOTE]
<span data-ttu-id="97987-107">Os links de referência de API levará você para o MSDN.</span><span class="sxs-lookup"><span data-stu-id="97987-107">The API reference links will take you to MSDN.</span></span>  <span data-ttu-id="97987-108">A referência da API docs.microsoft.com não está completa.</span><span class="sxs-lookup"><span data-stu-id="97987-108">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="97987-109">Este passo a passo mostra como usar o provedor de tipos de WSDL Web Services Description Language () está disponível em F # 3.0 para acessar um serviço em WSDL.</span><span class="sxs-lookup"><span data-stu-id="97987-109">This walkthrough shows you how to use the Web Services Description Language (WSDL) type provider that is available in F# 3.0 to access a WSDL service.</span></span> <span data-ttu-id="97987-110">Em outras linguagens .NET, gerar o código para acessar o serviço web por chamada svcutil.exe ou adicionando uma referência da web no, por exemplo, um c# do projeto para obter o Visual Studio para chamar o svcutil.exe para você.</span><span class="sxs-lookup"><span data-stu-id="97987-110">In other .NET languages, you generate the code to access the web service by calling svcutil.exe, or by adding a web reference in, for example, a C# project to get Visual Studio to call svcutil.exe for you.</span></span> <span data-ttu-id="97987-111">Em F #, você tem a opção adicional de usar o provedor de tipo WSDL, portanto, assim que você escreva o código que cria o tipo WsdlService, os tipos são gerados e ficam disponíveis.</span><span class="sxs-lookup"><span data-stu-id="97987-111">In F#, you have the additional option of using the WSDL type provider, so as soon as you write the code that creates the WsdlService type, the types are generated and become available.</span></span> <span data-ttu-id="97987-112">Esse processo depende do serviço está disponível quando você estiver escrevendo o código.</span><span class="sxs-lookup"><span data-stu-id="97987-112">This process relies on the service being available when you are writing the code.</span></span>

<span data-ttu-id="97987-113">Esta explicação passo a passo mostra as seguintes tarefas.</span><span class="sxs-lookup"><span data-stu-id="97987-113">This walkthrough illustrates the following tasks.</span></span> <span data-ttu-id="97987-114">Você deve concluir-os nesta ordem para a passo a passo para ter êxito:</span><span class="sxs-lookup"><span data-stu-id="97987-114">You must complete them in this order for the walkthrough to succeed:</span></span>


- <span data-ttu-id="97987-115">Criando o projeto</span><span class="sxs-lookup"><span data-stu-id="97987-115">Creating the project</span></span>
<br />

- <span data-ttu-id="97987-116">Configurando o provedor de tipos</span><span class="sxs-lookup"><span data-stu-id="97987-116">Configuring the type provider</span></span>
<br />

- <span data-ttu-id="97987-117">Chamar o serviço web e processar os resultados</span><span class="sxs-lookup"><span data-stu-id="97987-117">Calling the web service, and processing the results</span></span>
<br />


## <a name="creating-the-project"></a><span data-ttu-id="97987-118">Criando o projeto</span><span class="sxs-lookup"><span data-stu-id="97987-118">Creating the project</span></span>
<span data-ttu-id="97987-119">Na etapa, você pode cria um projeto e adicionar as referências apropriadas para usar um provedor de tipo WSDL.</span><span class="sxs-lookup"><span data-stu-id="97987-119">In the step, you create a project and add the appropriate references to use a WSDL type provider.</span></span>


#### <a name="to-create-and-set-up-an-f-project"></a><span data-ttu-id="97987-120">Para criar e configurar um projeto de F#</span><span class="sxs-lookup"><span data-stu-id="97987-120">To create and set up an F# project</span></span>

1. <span data-ttu-id="97987-121">Abra um novo projeto de aplicativo de Console em F #.</span><span class="sxs-lookup"><span data-stu-id="97987-121">Open a new F# Console Application project.</span></span>
<br />

2. <span data-ttu-id="97987-122">Em **Solution Explorer**, abra o menu de atalho para o projeto **referência** nó e, em seguida, escolha **adicionar referência**.</span><span class="sxs-lookup"><span data-stu-id="97987-122">In **Solution Explorer**, open the shortcut menu for the project's **Reference** node, and then choose **Add Reference**.</span></span>
<br />

3. <span data-ttu-id="97987-123">No **Assemblies** área, escolha **Framework**e, em seguida, na lista de assemblies disponíveis, escolha **Serialization** e  **System. ServiceModel**.</span><span class="sxs-lookup"><span data-stu-id="97987-123">In the **Assemblies** area, choose **Framework**, and then, in the list of available assemblies, choose **System.Runtime.Serialization** and **System.ServiceModel**.</span></span>
<br />

4. <span data-ttu-id="97987-124">No **Assemblies** área, escolha **extensões**.</span><span class="sxs-lookup"><span data-stu-id="97987-124">In the **Assemblies** area, choose **Extensions**.</span></span>
<br />

5. <span data-ttu-id="97987-125">Na lista de assemblies disponíveis, escolha **FSharp.Data.TypeProviders**e, em seguida, escolha o **Okey** botão para adicionar referências a esses assemblies.</span><span class="sxs-lookup"><span data-stu-id="97987-125">In the list of available assemblies, choose **FSharp.Data.TypeProviders**, and then choose the **OK** button to add references to these assemblies.</span></span>
<br />

## <a name="configuring-the-type-provider"></a><span data-ttu-id="97987-126">Configurando o provedor de tipos</span><span class="sxs-lookup"><span data-stu-id="97987-126">Configuring the type provider</span></span>
<span data-ttu-id="97987-127">Nesta etapa, você pode usar o provedor de tipo WSDL para gerar tipos para o serviço da web TerraServer.</span><span class="sxs-lookup"><span data-stu-id="97987-127">In this step, you use the WSDL type provider to generate types for the TerraServer web service.</span></span>


#### <a name="to-configure-the-type-provider-and-generate-types"></a><span data-ttu-id="97987-128">Para configurar o provedor de tipos e gerar tipos</span><span class="sxs-lookup"><span data-stu-id="97987-128">To configure the type provider and generate types</span></span>

1. <span data-ttu-id="97987-129">Adicione a seguinte linha de código para abrir o namespace do provedor de tipo.</span><span class="sxs-lookup"><span data-stu-id="97987-129">Add the following line of code to open the type provider namespace.</span></span>
<br />

```fsharp
open System
open System.ServiceModel
open Microsoft.FSharp.Linq
open Microsoft.FSharp.Data.TypeProviders
```

2. <span data-ttu-id="97987-130">Adicione a seguinte linha de código para chamar o provedor de tipo com um serviço web.</span><span class="sxs-lookup"><span data-stu-id="97987-130">Add the following line of code to invoke the type provider with a web service.</span></span> <span data-ttu-id="97987-131">Neste exemplo, use o serviço da web TerraServer.</span><span class="sxs-lookup"><span data-stu-id="97987-131">In this example, use the TerraServer web service.</span></span>
<br />

```fsharp
type TerraService = WsdlService<" HYPERLINK "https://terraserver-usa.com/TerraService2.asmx?WSDL" https://msrmaps.com/TerraService2.asmx?WSDL">
```

  <span data-ttu-id="97987-132">Um rabisco vermelho é exibido sob essa linha de código se o URI do serviço está incorreta ou se o próprio serviço está inativo ou não está executando.</span><span class="sxs-lookup"><span data-stu-id="97987-132">A red squiggle appears under this line of code if the service URI is misspelled or if the service itself is down or isn’t performing.</span></span> <span data-ttu-id="97987-133">Se você apontar para o código, uma mensagem de erro descreve o problema.</span><span class="sxs-lookup"><span data-stu-id="97987-133">If you point to the code, an error message describes the problem.</span></span> <span data-ttu-id="97987-134">Você pode encontrar as mesmas informações no **lista de erros** janela ou a **a janela de saída** depois de criar.</span><span class="sxs-lookup"><span data-stu-id="97987-134">You can find the same information in the **Error List** window or in the **Output Window** after you build.</span></span>
<br />  <span data-ttu-id="97987-135">Há duas maneiras de especificar definições de configuração para uma conexão de WSDL, usando o arquivo App. config para o projeto, ou usando os parâmetros de tipo estático na declaração do provedor de tipo.</span><span class="sxs-lookup"><span data-stu-id="97987-135">There are two ways to specify configuration settings for a WSDL connection, by using the app.config file for the project, or by using the static type parameters in the type provider declaration.</span></span> <span data-ttu-id="97987-136">Você pode usar o svcutil.exe para gerar elementos do arquivo de configuração apropriado.</span><span class="sxs-lookup"><span data-stu-id="97987-136">You can use svcutil.exe to generate appropriate configuration file elements.</span></span> <span data-ttu-id="97987-137">Para obter mais informações sobre como usar o svcutil.exe para gerar informações de configuração para um serviço web, consulte [Ferramenta Utilitária de metadados ServiceModel &#40; Svcutil.exe &#41; ](https://msdn.microsoft.com/library/aa347733.aspx).</span><span class="sxs-lookup"><span data-stu-id="97987-137">For more information about using svcutil.exe to generate configuration information for a web service, see [ServiceModel Metadata Utility Tool &#40;Svcutil.exe&#41;](https://msdn.microsoft.com/library/aa347733.aspx).</span></span> <span data-ttu-id="97987-138">Para obter uma descrição completa dos parâmetros de tipo estático para o provedor de tipo WSDL, consulte [provedor de tipos WsdlService](https://msdn.microsoft.com/visualfsharpdocs/conceptual/wsdlservice-type-provider-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="97987-138">For a full description of the static type parameters for the WSDL type provider, see [WsdlService Type Provider](https://msdn.microsoft.com/visualfsharpdocs/conceptual/wsdlservice-type-provider-%5bfsharp%5d).</span></span>
<br />

## <a name="calling-the-web-service-and-processing-the-results"></a><span data-ttu-id="97987-139">Chamar o serviço web e processar os resultados</span><span class="sxs-lookup"><span data-stu-id="97987-139">Calling the web service, and processing the results</span></span>
<span data-ttu-id="97987-140">Cada serviço web tem seu próprio conjunto de tipos que são usados como parâmetros para suas chamadas de método.</span><span class="sxs-lookup"><span data-stu-id="97987-140">Each web service has its own set of types that are used as parameters for its method calls.</span></span> <span data-ttu-id="97987-141">Nesta etapa, esses parâmetros de preparação, chamar um método web e processar as informações que ele retorna.</span><span class="sxs-lookup"><span data-stu-id="97987-141">In this step, you prepare these parameters, call a web method, and process the information that it returns.</span></span>


#### <a name="to-call-the-web-service-and-process-the-results"></a><span data-ttu-id="97987-142">Para chamar o serviço web e processar os resultados</span><span class="sxs-lookup"><span data-stu-id="97987-142">To call the web service, and process the results</span></span>

1. <span data-ttu-id="97987-143">O serviço web pode atingir o tempo limite ou parar de funcionar, portanto você deve incluir a chamada de serviço da web em uma bloco de tratamento de exceções.</span><span class="sxs-lookup"><span data-stu-id="97987-143">The web service might time out or stop functioning, so you should include the web service call in an exception handling block.</span></span> <span data-ttu-id="97987-144">Escreva o código a seguir para tentar obter dados do serviço da web.</span><span class="sxs-lookup"><span data-stu-id="97987-144">Write the following code to try to get data from the web service.</span></span>
<br />

```fsharp
try
  let terraClient = TerraService.GetTerraServiceSoap ()
  let myPlace = new TerraService.ServiceTypes.msrmaps.com.Place(City = "Redmond", State = "Washington", Country = "United States")
  let myLocation = terraClient.ConvertPlaceToLonLatPt(myPlace)
  printfn "Redmond Latitude: %f Longitude: %f" (myLocation.Lat) (myLocation.Lon)
with
| :? ServerTooBusyException as exn ->
  let innerMessage =
    match (exn.InnerException) with
    | null -> ""
    | innerExn -> innerExn.Message
  printfn "An exception occurred:\n %s\n %s" exn.Message innerMessage
| exn -> printfn "An exception occurred: %s" exn.Message
```

<span data-ttu-id="97987-145">Observe que você criar os tipos de dados que são necessários para o serviço web, tais como **local** e **local**, como o tipo de tipos aninhados sob o WsdlService **TerraService**.</span><span class="sxs-lookup"><span data-stu-id="97987-145">Notice that you create the data types that are needed for the web service, such as **Place** and **Location**, as nested types under the WsdlService type **TerraService**.</span></span>
<br />


## <a name="see-also"></a><span data-ttu-id="97987-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="97987-146">See Also</span></span>
[<span data-ttu-id="97987-147">Provedor de tipos WsdlService</span><span class="sxs-lookup"><span data-stu-id="97987-147">WsdlService Type Provider</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/wsdlservice-type-provider-%5bfsharp%5d)

[<span data-ttu-id="97987-148">Provedores de Tipos</span><span class="sxs-lookup"><span data-stu-id="97987-148">Type Providers</span></span>](index.md)
