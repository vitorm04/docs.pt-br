---
title: Calculadora correlacionada
ms.date: 03/30/2017
ms.assetid: c365166e-6552-49a4-bf17-9f4e597d4d41
ms.openlocfilehash: 71cfdd0906ef20ec36b76ef5e508a4551b9fe3fe
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43517307"
---
# <a name="correlated-calculator"></a><span data-ttu-id="d0160-102">Calculadora correlacionada</span><span class="sxs-lookup"><span data-stu-id="d0160-102">Correlated Calculator</span></span>
<span data-ttu-id="d0160-103">Este exemplo demonstra como usar as atividades de mensagens (<xref:System.ServiceModel.Activities.Receive> e <xref:System.ServiceModel.Activities.SendReply>) no designer com correlação conteudo com base em um parâmetro na mensagem.</span><span class="sxs-lookup"><span data-stu-id="d0160-103">This sample demonstrates how to use the messaging activities (<xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply>) in the designer with content-based correlation based on a parameter in the message.</span></span> <span data-ttu-id="d0160-104">Nesse cenário, o funcionamento da calculadora estão em um trem paralelo.</span><span class="sxs-lookup"><span data-stu-id="d0160-104">In this scenario, the operations of the calculator are in a parallel convoy.</span></span> <span data-ttu-id="d0160-105">Uma instância e uma correlação (com base em `CalculatorId`) são criadas quando a primeira mensagem é enviada para o fluxo de trabalho, e mensagens subsequentes com a mesma `CalculatorId` são distribuídos a essa instância até que a operação de redefinição é chamada.</span><span class="sxs-lookup"><span data-stu-id="d0160-105">Both an instance and a correlation (based on `CalculatorId`) are created when the first message is sent to the workflow, and subsequent messages with the same `CalculatorId` are dispatched to that instance until the Reset operation is called.</span></span> <span data-ttu-id="d0160-106">O cliente é implementado como um aplicativo de WPF que usa um proxy código baseado de cliente para se comunicar com o serviço.</span><span class="sxs-lookup"><span data-stu-id="d0160-106">The client is implemented as a WPF application that uses a code-based client proxy to communicate with the service.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="d0160-107">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="d0160-107">To use this sample</span></span>  
  
1.  <span data-ttu-id="d0160-108">Inicie [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] em permissões elevadas, abra o arquivo de solução de For.sln.</span><span class="sxs-lookup"><span data-stu-id="d0160-108">Start [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] in elevated permissions, open the For.sln solution file.</span></span>  
  
    1.  <span data-ttu-id="d0160-109">Navegue até a pasta que contém [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d0160-109">Navigate to the folder that contains [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
    2.  <span data-ttu-id="d0160-110">Devenv.exe com o botão direito e selecione **executar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="d0160-110">Right-click Devenv.exe and select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="d0160-111">Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de CorrelatedCalculator.sln.</span><span class="sxs-lookup"><span data-stu-id="d0160-111">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the CorrelatedCalculator.sln solution file.</span></span>  
  
3.  <span data-ttu-id="d0160-112">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="d0160-112">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
4.  <span data-ttu-id="d0160-113">Para executar o projeto de serviço, pressione CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="d0160-113">To run the service project, press CTRL+F5.</span></span>  
  
5.  <span data-ttu-id="d0160-114">Uma vez que o serviço está pronto e escutar mensagens, em Solution Explorer, clique com o botão direito do mouse no projeto do cliente e executá-lo.</span><span class="sxs-lookup"><span data-stu-id="d0160-114">Once the service is ready and listening for messages, in Solution Explorer, right-click the Client project and run it.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d0160-115">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="d0160-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d0160-116">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="d0160-116">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d0160-117">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="d0160-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d0160-118">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="d0160-118">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\CorellatedCalculator`