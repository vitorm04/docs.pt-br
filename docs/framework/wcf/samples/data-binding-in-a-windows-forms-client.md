---
title: "Associação de dados em um cliente de formulários do Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2a30b37-d6e2-4552-820e-e60b2bbe8829
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 163bd72d9c42680d72c435e8266c75876490a2dd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="data-binding-in-a-windows-forms-client"></a><span data-ttu-id="f68b3-102">Associação de dados em um cliente de formulários do Windows</span><span class="sxs-lookup"><span data-stu-id="f68b3-102">Data Binding in a Windows Forms Client</span></span>
<span data-ttu-id="f68b3-103">Este exemplo demonstra como associar a dados retornados por uma [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] serviço em um aplicativo do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="f68b3-103">This sample demonstrates how to bind to data returned by a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service in a Windows Forms application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f68b3-104">As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste artigo.</span><span class="sxs-lookup"><span data-stu-id="f68b3-104">The setup procedure and build instructions for this sample are located at the end of this article.</span></span>  
  
 <span data-ttu-id="f68b3-105">Este exemplo demonstra um serviço que implementa um contrato que define um padrão de comunicação de solicitação-resposta.</span><span class="sxs-lookup"><span data-stu-id="f68b3-105">This sample demonstrates a service that implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="f68b3-106">O exemplo consiste em um cliente de aplicativo do Windows Forms (.exe) e um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço hospedado pelo Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="f68b3-106">The sample consists of a client Windows Forms application (.exe) and a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service hosted by Internet Information Services (IIS).</span></span>  
  
 <span data-ttu-id="f68b3-107">O contrato é definido pelo `IWeatherService` interface, que expõe uma operação denominada `GetWeatherData`.</span><span class="sxs-lookup"><span data-stu-id="f68b3-107">The contract is defined by the `IWeatherService` interface, which exposes an operation named `GetWeatherData`.</span></span> <span data-ttu-id="f68b3-108">Esta operação aceita uma matriz de cidades e retorna uma matriz de `WeatherData` objetos que representam a temperatura alta e baixa prevista para uma cidade.</span><span class="sxs-lookup"><span data-stu-id="f68b3-108">This operation accepts an array of cities and returns an array of `WeatherData` objects that represent the high and low forecasted temperature for a city.</span></span>  
  
 <span data-ttu-id="f68b3-109">A associação de dados ocorre no cliente no aplicativo Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="f68b3-109">The data binding occurs on the client in the Windows Forms application.</span></span> <span data-ttu-id="f68b3-110">Um `DataGridView` é definido no designer de formulários do Windows, que é uma representação gráfica dos dados.</span><span class="sxs-lookup"><span data-stu-id="f68b3-110">A `DataGridView` is defined in the Windows Forms designer, which is a graphical representation of the data.</span></span> <span data-ttu-id="f68b3-111">Intermediário chamado `BindingSource` também é criado.</span><span class="sxs-lookup"><span data-stu-id="f68b3-111">An intermediary named `BindingSource` is also created.</span></span> <span data-ttu-id="f68b3-112">A fonte de dados de `BindingSource` é definida para a matriz de dados retornada pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="f68b3-112">The data source of `BindingSource` is set to the data array returned by the service.</span></span> <span data-ttu-id="f68b3-113">A finalidade de `BindingSource` é fornecer uma camada de indireção entre os dados e o modo de exibição de dados.</span><span class="sxs-lookup"><span data-stu-id="f68b3-113">The purpose of the `BindingSource` is to provide a layer of indirection between the data and the data view.</span></span> <span data-ttu-id="f68b3-114">Toda a interação com os dados, como navegar, classificação, filtragem e atualizar, é feita com chamadas para o `BindingSource` componente.</span><span class="sxs-lookup"><span data-stu-id="f68b3-114">All interaction with the data, such as navigating, sorting, filtering, and updating, is accomplished with calls to the `BindingSource` component.</span></span> <span data-ttu-id="f68b3-115">Para realizar a associação de dados para o `DataGridView`, o `datasource` do `DataGridView` é definido como o `BindingSource` objeto.</span><span class="sxs-lookup"><span data-stu-id="f68b3-115">To accomplish data binding to the `DataGridView`, the `datasource` of the `DataGridView` is then set to the `BindingSource` object.</span></span> <span data-ttu-id="f68b3-116">Todos os dados retornados do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço é exibido graficamente para o usuário.</span><span class="sxs-lookup"><span data-stu-id="f68b3-116">All of the data returned from the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is then displayed graphically to the user.</span></span>  <span data-ttu-id="f68b3-117">Toda vez que o usuário clica no botão, os dados retornados são atualizados automaticamente em associada a dados `DataGridView`.</span><span class="sxs-lookup"><span data-stu-id="f68b3-117">Every time the user clicks the button, the returned data is automatically updated in the data-bound `DataGridView`.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f68b3-118">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="f68b3-118">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="f68b3-119">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f68b3-119">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="f68b3-120">Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f68b3-120">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="f68b3-121">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f68b3-121">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f68b3-122">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="f68b3-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f68b3-123">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="f68b3-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f68b3-124">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="f68b3-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f68b3-125">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="f68b3-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WindowsForms`  
  
## <a name="see-also"></a><span data-ttu-id="f68b3-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f68b3-126">See Also</span></span>
