---
title: Canal Caching com enviar
ms.date: 03/30/2017
ms.assetid: e69a2502-25cb-43bf-b8d2-95fbdecb41cb
ms.openlocfilehash: 619088def1f5e443a31244516655d75d1e25c9cb
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43503809"
---
# <a name="channel-caching-with-send"></a><span data-ttu-id="7225d-102">Canal Caching com enviar</span><span class="sxs-lookup"><span data-stu-id="7225d-102">Channel Caching with Send</span></span>
<span data-ttu-id="7225d-103"><xref:System.ServiceModel.Activities.SendMessageChannelCache> permite que os usuários para ter diferentes níveis de cachê do canal com <xref:System.ServiceModel.Activities.Send> e atividades de <xref:System.ServiceModel.Activities.SendParametersContent> .</span><span class="sxs-lookup"><span data-stu-id="7225d-103">The <xref:System.ServiceModel.Activities.SendMessageChannelCache> enables users to have different levels of channel caching with <xref:System.ServiceModel.Activities.Send> and <xref:System.ServiceModel.Activities.SendParametersContent> activities.</span></span> <span data-ttu-id="7225d-104">o cachê de instância é habilitado por padrão e este exemplo demonstra os seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="7225d-104">Instance-level caching is enabled by default and this sample demonstrates the following features:</span></span>  
  
1.  <span data-ttu-id="7225d-105">Compartilhar <xref:System.ServiceModel.Activities.SendMessageChannelCache> através de um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7225d-105">Share a <xref:System.ServiceModel.Activities.SendMessageChannelCache> across an application domain.</span></span>  
  
2.  <span data-ttu-id="7225d-106">Desativar o cachê do canal.</span><span class="sxs-lookup"><span data-stu-id="7225d-106">Disable channel caching.</span></span>  
  
3.  <span data-ttu-id="7225d-107">Compartilhar <xref:System.ServiceModel.Activities.SendMessageChannelCache> entre instâncias de fluxo de trabalho em <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="7225d-107">Share a <xref:System.ServiceModel.Activities.SendMessageChannelCache> among workflow instances in a <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="7225d-108">Demonstra</span><span class="sxs-lookup"><span data-stu-id="7225d-108">Demonstrates</span></span>  
 <span data-ttu-id="7225d-109">extensão de<xref:System.ServiceModel.Activities.SendMessageChannelCache> , <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.ReceiveContent> e atividades de <xref:System.ServiceModel.Activities.SendReply> .</span><span class="sxs-lookup"><span data-stu-id="7225d-109"><xref:System.ServiceModel.Activities.SendMessageChannelCache> extension, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.ReceiveContent> and <xref:System.ServiceModel.Activities.SendReply> activities.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7225d-110">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="7225d-110">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="7225d-111">Carregar a solução do projeto em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] e compile o projeto.</span><span class="sxs-lookup"><span data-stu-id="7225d-111">Load the project solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] and build the project.</span></span>  
  
2.  <span data-ttu-id="7225d-112">Executar em gerado aplicativo de EchoWorkflowService EchoWorkflowService \ \ bin \ debug.</span><span class="sxs-lookup"><span data-stu-id="7225d-112">Run the EchoWorkflowService application generated in \EchoWorkflowService\bin\debug.</span></span>  
  
3.  <span data-ttu-id="7225d-113">Executam EchoWorkflowClient aplicativo gerado no .\EchoWorkflowClient\bin\debug.</span><span class="sxs-lookup"><span data-stu-id="7225d-113">Run the EchoWorkflowClient application generated in .\EchoWorkflowClient\bin\debug.</span></span>  
  
4.  <span data-ttu-id="7225d-114">O cliente chama a operação de eco no serviço e imprime os resultados.</span><span class="sxs-lookup"><span data-stu-id="7225d-114">The client calls the Echo operation on the service and prints the results.</span></span> <span data-ttu-id="7225d-115">Quando os resultados foram impressos, pressione ENTER para sair do cliente e o serviço.</span><span class="sxs-lookup"><span data-stu-id="7225d-115">When the results have been printed, press ENTER to exit the client and the service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7225d-116">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="7225d-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7225d-117">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="7225d-117">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7225d-118">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="7225d-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7225d-119">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="7225d-119">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\ChannelCache`
