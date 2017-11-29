---
title: "Uso básico de atividades de SendParameters e de ReceiveParameters"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b6b1681-3d41-403f-bfe2-3f600f24aa8c
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9c3b6f189f1a2564662af89961c9363f025ae8c3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="basic-usage-of-sendparameters-and-receiveparameters-activities"></a><span data-ttu-id="875ab-102">Uso básico de atividades de SendParameters e de ReceiveParameters</span><span class="sxs-lookup"><span data-stu-id="875ab-102">Basic Usage of SendParameters and ReceiveParameters Activities</span></span>
<span data-ttu-id="875ab-103">Este exemplo mostra o uso de <xref:System.ServiceModel.Activities.SendParametersContent> e de atividades de <xref:System.ServiceModel.Activities.ReceiveParametersContent> .</span><span class="sxs-lookup"><span data-stu-id="875ab-103">This sample shows the use of <xref:System.ServiceModel.Activities.SendParametersContent> and <xref:System.ServiceModel.Activities.ReceiveParametersContent> activities.</span></span> <span data-ttu-id="875ab-104">O serviço expõe uma operação que recebe um argumento de cadeia de caracteres e ecoa a entrada de volta para o cliente.</span><span class="sxs-lookup"><span data-stu-id="875ab-104">The service exposes one operation that takes a string argument and echoes the input back to the client.</span></span> <span data-ttu-id="875ab-105">O exemplo a seguir mostra como configurar parâmetros para essas atividades de mensagem.</span><span class="sxs-lookup"><span data-stu-id="875ab-105">The sample shows how to set up the parameters for these messaging activities.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="875ab-106">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="875ab-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="875ab-107">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="875ab-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="875ab-108">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="875ab-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="875ab-109">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="875ab-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\SendReceiveParameters`  
  
#### <a name="using-this-sample"></a><span data-ttu-id="875ab-110">Usando este exemplo</span><span class="sxs-lookup"><span data-stu-id="875ab-110">Using this sample</span></span>  
  
1.  <span data-ttu-id="875ab-111">Carregar a solução do projeto em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] e compile o projeto.</span><span class="sxs-lookup"><span data-stu-id="875ab-111">Load the project solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] and build the project.</span></span>  
  
2.  <span data-ttu-id="875ab-112">Executa EchoWorkflowService aplicativo gerado em [] do diretório da solução EchoWorkflowService \ \ bin \ debug.</span><span class="sxs-lookup"><span data-stu-id="875ab-112">First run the EchoWorkflowService application generated in [solution base directory]\EchoWorkflowService\bin\debug.</span></span>  
  
3.  <span data-ttu-id="875ab-113">Segundo, executam EchoWorkflowClient aplicativo gerado em [] do diretório da solução EchoWorkflowClient \ \ bin \ debug.</span><span class="sxs-lookup"><span data-stu-id="875ab-113">Second, run the EchoWorkflowClient application generated in [solution base directory]\EchoWorkflowClient\bin\debug.</span></span>  
  
4.  <span data-ttu-id="875ab-114">O cliente chama a operação de eco no serviço e imprime os resultados.</span><span class="sxs-lookup"><span data-stu-id="875ab-114">The client calls Echo operation on the service and prints the results.</span></span> <span data-ttu-id="875ab-115">Quando completo, pressione ENTER para sair do cliente e o serviço.</span><span class="sxs-lookup"><span data-stu-id="875ab-115">When complete, press ENTER to exit the client and then the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="875ab-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="875ab-116">See Also</span></span>
