---
title: Calculadora correlacionada
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c365166e-6552-49a4-bf17-9f4e597d4d41
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 53d96e090edabc65b7356497c3726d29e46c4ea7
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2017
---
# <a name="correlated-calculator"></a><span data-ttu-id="d1cda-102">Calculadora correlacionada</span><span class="sxs-lookup"><span data-stu-id="d1cda-102">Correlated Calculator</span></span>
<span data-ttu-id="d1cda-103">Este exemplo demonstra como usar as atividades de mensagens (<xref:System.ServiceModel.Activities.Receive> e <xref:System.ServiceModel.Activities.SendReply>) no designer com correlação conteudo com base em um parâmetro na mensagem.</span><span class="sxs-lookup"><span data-stu-id="d1cda-103">This sample demonstrates how to use the messaging activities (<xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply>) in the designer with content-based correlation based on a parameter in the message.</span></span> <span data-ttu-id="d1cda-104">Nesse cenário, o funcionamento da calculadora estão em um trem paralelo.</span><span class="sxs-lookup"><span data-stu-id="d1cda-104">In this scenario, the operations of the calculator are in a parallel convoy.</span></span> <span data-ttu-id="d1cda-105">Uma instância e uma correlação (com base em `CalculatorId`) são criadas quando a primeira mensagem é enviada para o fluxo de trabalho, e mensagens subsequentes com a mesma `CalculatorId` são distribuídos a essa instância até que a operação de redefinição é chamada.</span><span class="sxs-lookup"><span data-stu-id="d1cda-105">Both an instance and a correlation (based on `CalculatorId`) are created when the first message is sent to the workflow, and subsequent messages with the same `CalculatorId` are dispatched to that instance until the Reset operation is called.</span></span> <span data-ttu-id="d1cda-106">O cliente é implementado como um aplicativo de WPF que usa um proxy código baseado de cliente para se comunicar com o serviço.</span><span class="sxs-lookup"><span data-stu-id="d1cda-106">The client is implemented as a WPF application that uses a code-based client proxy to communicate with the service.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="d1cda-107">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="d1cda-107">To use this sample</span></span>  
  
1.  <span data-ttu-id="d1cda-108">Inicie [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] em permissões elevadas, abra o arquivo de solução de For.sln.</span><span class="sxs-lookup"><span data-stu-id="d1cda-108">Start [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] in elevated permissions, open the For.sln solution file.</span></span>  
  
    1.  <span data-ttu-id="d1cda-109">Navegue até a pasta que contém [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d1cda-109">Navigate to the folder that contains [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
    2.  <span data-ttu-id="d1cda-110">Devenv.exe e selecione **executar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="d1cda-110">Right-click Devenv.exe and select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="d1cda-111">Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de CorrelatedCalculator.sln.</span><span class="sxs-lookup"><span data-stu-id="d1cda-111">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the CorrelatedCalculator.sln solution file.</span></span>  
  
3.  <span data-ttu-id="d1cda-112">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="d1cda-112">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
4.  <span data-ttu-id="d1cda-113">Para executar o projeto de serviço, pressione CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="d1cda-113">To run the service project, press CTRL+F5.</span></span>  
  
5.  <span data-ttu-id="d1cda-114">Uma vez que o serviço está pronto e escutar mensagens, em Solution Explorer, clique com o botão direito do mouse no projeto do cliente e executá-lo.</span><span class="sxs-lookup"><span data-stu-id="d1cda-114">Once the service is ready and listening for messages, in Solution Explorer, right-click the Client project and run it.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d1cda-115">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="d1cda-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d1cda-116">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="d1cda-116">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d1cda-117">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="d1cda-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d1cda-118">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="d1cda-118">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\CorellatedCalculator`