---
title: Uso básico de atividades de SendParameters e de ReceiveParameters
ms.date: 03/30/2017
ms.assetid: 1b6b1681-3d41-403f-bfe2-3f600f24aa8c
ms.openlocfilehash: c13999ad1571a6413e30e801b6c642000f8e4654
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43467689"
---
# <a name="basic-usage-of-sendparameters-and-receiveparameters-activities"></a><span data-ttu-id="44c70-102">Uso básico de atividades de SendParameters e de ReceiveParameters</span><span class="sxs-lookup"><span data-stu-id="44c70-102">Basic Usage of SendParameters and ReceiveParameters Activities</span></span>
<span data-ttu-id="44c70-103">Este exemplo mostra o uso de <xref:System.ServiceModel.Activities.SendParametersContent> e de atividades de <xref:System.ServiceModel.Activities.ReceiveParametersContent> .</span><span class="sxs-lookup"><span data-stu-id="44c70-103">This sample shows the use of <xref:System.ServiceModel.Activities.SendParametersContent> and <xref:System.ServiceModel.Activities.ReceiveParametersContent> activities.</span></span> <span data-ttu-id="44c70-104">O serviço expõe uma operação que recebe um argumento de cadeia de caracteres e ecoa a entrada de volta para o cliente.</span><span class="sxs-lookup"><span data-stu-id="44c70-104">The service exposes one operation that takes a string argument and echoes the input back to the client.</span></span> <span data-ttu-id="44c70-105">O exemplo a seguir mostra como configurar parâmetros para essas atividades de mensagem.</span><span class="sxs-lookup"><span data-stu-id="44c70-105">The sample shows how to set up the parameters for these messaging activities.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="44c70-106">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="44c70-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="44c70-107">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="44c70-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="44c70-108">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="44c70-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="44c70-109">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="44c70-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\SendReceiveParameters`  
  
#### <a name="using-this-sample"></a><span data-ttu-id="44c70-110">Usando este exemplo</span><span class="sxs-lookup"><span data-stu-id="44c70-110">Using this sample</span></span>  
  
1.  <span data-ttu-id="44c70-111">Carregar a solução do projeto em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] e compile o projeto.</span><span class="sxs-lookup"><span data-stu-id="44c70-111">Load the project solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] and build the project.</span></span>  
  
2.  <span data-ttu-id="44c70-112">Executa EchoWorkflowService aplicativo gerado em [] do diretório da solução EchoWorkflowService \ \ bin \ debug.</span><span class="sxs-lookup"><span data-stu-id="44c70-112">First run the EchoWorkflowService application generated in [solution base directory]\EchoWorkflowService\bin\debug.</span></span>  
  
3.  <span data-ttu-id="44c70-113">Segundo, executam EchoWorkflowClient aplicativo gerado em [] do diretório da solução EchoWorkflowClient \ \ bin \ debug.</span><span class="sxs-lookup"><span data-stu-id="44c70-113">Second, run the EchoWorkflowClient application generated in [solution base directory]\EchoWorkflowClient\bin\debug.</span></span>  
  
4.  <span data-ttu-id="44c70-114">O cliente chama a operação de eco no serviço e imprime os resultados.</span><span class="sxs-lookup"><span data-stu-id="44c70-114">The client calls Echo operation on the service and prints the results.</span></span> <span data-ttu-id="44c70-115">Quando completo, pressione ENTER para sair do cliente e o serviço.</span><span class="sxs-lookup"><span data-stu-id="44c70-115">When complete, press ENTER to exit the client and then the service.</span></span>