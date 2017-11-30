---
title: "Associação de dados em um cliente do ASP.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68b49fa6-94e7-4d4c-a34e-902a2b3770b6
caps.latest.revision: "23"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7ceb63315d94c0deed161bb294e8f61bf523bb63
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="data-binding-in-an-aspnet-client"></a><span data-ttu-id="6d1d5-102">Associação de dados em um cliente do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="6d1d5-102">Data Binding in an ASP.NET Client</span></span>
<span data-ttu-id="6d1d5-103">Este exemplo demonstra como associar dados retornados por um típico [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] serviço em um aplicativo de Web Forms.</span><span class="sxs-lookup"><span data-stu-id="6d1d5-103">This sample demonstrates how to bind data returned by a typical [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service in a Web Forms application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6d1d5-104">As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="6d1d5-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="6d1d5-105">Este exemplo demonstra um serviço que implementa um contrato que define um padrão de comunicação de solicitação-resposta.</span><span class="sxs-lookup"><span data-stu-id="6d1d5-105">This sample demonstrates a service that implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="6d1d5-106">O exemplo consiste em um aplicativo de Web Forms acessível de um navegador do cliente e um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço hospedado pelo Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="6d1d5-106">The sample consists of a client Web Forms application accessible from a browser and a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service hosted by Internet Information Services (IIS).</span></span>  
  
 <span data-ttu-id="6d1d5-107">O serviço implementa um contrato que define um padrão de comunicação de solicitação-resposta.</span><span class="sxs-lookup"><span data-stu-id="6d1d5-107">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="6d1d5-108">O contrato é definido pelo `IWeatherService` interface, que expõe uma operação denominada `GetWeatherData`.</span><span class="sxs-lookup"><span data-stu-id="6d1d5-108">The contract is defined by the `IWeatherService` interface, which exposes an operation named `GetWeatherData`.</span></span> <span data-ttu-id="6d1d5-109">Esta operação aceita uma matriz de cidades e retorna uma matriz de `WeatherData` objetos que representam a temperatura alta e baixa prevista para uma cidade.</span><span class="sxs-lookup"><span data-stu-id="6d1d5-109">This operation accepts an array of cities and returns an array of `WeatherData` objects that represent the high and low forecasted temperature for a city.</span></span>  
  
 <span data-ttu-id="6d1d5-110">Sobre o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] página. aspx do cliente, uma Web de DataGrid controle é definido, que contém a representação gráfica dos dados retornados pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="6d1d5-110">On the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] client .aspx page, a DataGrid Web control is defined, which contains the graphical representation of the data returned by the service.</span></span> <span data-ttu-id="6d1d5-111">Código de chamadas de página. aspx a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço para os dados de clima e retorna os dados para uma matriz de `WeatherData` objetos.</span><span class="sxs-lookup"><span data-stu-id="6d1d5-111">Code on the .aspx page calls the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service for weather data and returns the data to an array of `WeatherData` objects.</span></span> <span data-ttu-id="6d1d5-112">A grade de dados especifica onde obter seus dados, definindo seu `DataSource` propriedade para essa matriz.</span><span class="sxs-lookup"><span data-stu-id="6d1d5-112">The DataGrid specifies where to get its data from by setting its `DataSource` property to that array.</span></span> <span data-ttu-id="6d1d5-113">A associação de dados ocorre com uma chamada para a grade de dados `DataBind` método.</span><span class="sxs-lookup"><span data-stu-id="6d1d5-113">The data binding occurs with a call to the DataGrid's `DataBind` method.</span></span> <span data-ttu-id="6d1d5-114">Todo esse código está contido dentro do.`aspx`</span><span class="sxs-lookup"><span data-stu-id="6d1d5-114">All of this code is contained inside the .`aspx`</span></span> <span data-ttu-id="6d1d5-115">página `Page_Load` método, portanto toda vez que o usuário atualiza a página do navegador, os dados é atualizado em DataGrid.</span><span class="sxs-lookup"><span data-stu-id="6d1d5-115">page's `Page_Load` method, so every time the user refreshes the browser page, the data is updated in the DataGrid.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6d1d5-116">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="6d1d5-116">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="6d1d5-117">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6d1d5-117">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="6d1d5-118">Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6d1d5-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="6d1d5-119">Cliente neste exemplo é um site da Web que é executado em um servidor Web de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="6d1d5-119">This sample's client is a Web site that runs under a development Web server.</span></span> <span data-ttu-id="6d1d5-120">Para iniciar o servidor de desenvolvimento da Web, digite o seguinte no prompt de comando: "`%SystemDrive%\Program Files\Common Files\Microsoft Shared\DevServer\9.0\WebDev.WebServer.EXE" /port:8000 /path:<WebFormsSamplePath>\CS\client /vpath:/client`.</span><span class="sxs-lookup"><span data-stu-id="6d1d5-120">To launch the development Web server, type the following at the command prompt: "`%SystemDrive%\Program Files\Common Files\Microsoft Shared\DevServer\9.0\WebDev.WebServer.EXE" /port:8000 /path:<WebFormsSamplePath>\CS\client /vpath:/client`.</span></span> <span data-ttu-id="6d1d5-121">Em seguida, navegue até http://localhost:8000 e cliente.</span><span class="sxs-lookup"><span data-stu-id="6d1d5-121">Then browse to http://localhost:8000/client.</span></span> <span data-ttu-id="6d1d5-122">Para executar esse exemplo em computadores, substitua todas as referências a `localhost` no arquivo Web. config do cliente, com o nome do computador do servidor.</span><span class="sxs-lookup"><span data-stu-id="6d1d5-122">To run this sample across computers, replace all references to `localhost` in the client's Web.config file with the computer name of the server.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6d1d5-123">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="6d1d5-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6d1d5-124">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="6d1d5-124">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6d1d5-125">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="6d1d5-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6d1d5-126">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="6d1d5-126">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WebForms`  
  
## <a name="see-also"></a><span data-ttu-id="6d1d5-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6d1d5-127">See Also</span></span>
