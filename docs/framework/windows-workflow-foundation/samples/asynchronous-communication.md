---
title: Comunicação assíncrona
ms.date: 03/30/2017
ms.assetid: 128dc092-9eb2-4e33-9470-9a7f62b60df6
ms.openlocfilehash: e1bc63b5d3178b8e98350dedd8eb0791e0e35589
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142870"
---
# <a name="asynchronous-communication"></a><span data-ttu-id="49c8e-102">Comunicação assíncrona</span><span class="sxs-lookup"><span data-stu-id="49c8e-102">Asynchronous Communication</span></span>
<span data-ttu-id="49c8e-103">Esta amostra demonstra como a comunicação entre dois serviços diferentes da Windows Workflow Foundation (WF) é feita de forma assíncrona por padrão.</span><span class="sxs-lookup"><span data-stu-id="49c8e-103">This sample demonstrates how the communication between two different Windows Workflow Foundation (WF) services is done asynchronously by default.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="49c8e-104">Demonstra</span><span class="sxs-lookup"><span data-stu-id="49c8e-104">Demonstrates</span></span>  
 <span data-ttu-id="49c8e-105">Comunicação assíncrona entre os serviços de [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="49c8e-105">Asynchronous communication between [!INCLUDE[wf1](../../../../includes/wf1-md.md)] services.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="49c8e-106">Discussão</span><span class="sxs-lookup"><span data-stu-id="49c8e-106">Discussion</span></span>  
 <span data-ttu-id="49c8e-107">Este exemplo mostra como a comunicação entre aplicativos de [!INCLUDE[wf1](../../../../includes/wf1-md.md)] é feita de forma assíncrona usando as atividades de mensagem fornecidas pelo.NET Framework.</span><span class="sxs-lookup"><span data-stu-id="49c8e-107">This sample shows how the communication between [!INCLUDE[wf1](../../../../includes/wf1-md.md)] applications is done asynchronously by using the messaging activities provided by .NET Framework.</span></span>  
  
 <span data-ttu-id="49c8e-108">Esse exemplo consiste em três projetos.</span><span class="sxs-lookup"><span data-stu-id="49c8e-108">This sample consists of the following three projects.</span></span>  
  
 <span data-ttu-id="49c8e-109">CreditCheckService</span><span class="sxs-lookup"><span data-stu-id="49c8e-109">CreditCheckService</span></span>  
 <span data-ttu-id="49c8e-110">Esse serviço recebe a pontuação de crédito de uma pessoa específico ou o valor do item para adquirir, e então decidir se o crédito é dado a pessoa.</span><span class="sxs-lookup"><span data-stu-id="49c8e-110">This service receives the credit score of a particular person or the value of the item to acquire, and then decides whether the credit is given to the person.</span></span>  
  
 <span data-ttu-id="49c8e-111">RentalApprovalService</span><span class="sxs-lookup"><span data-stu-id="49c8e-111">RentalApprovalService</span></span>  
 <span data-ttu-id="49c8e-112">Esse serviço recebe um aplicativo de uma pessoa que é a necessidade de qualquer crédito.</span><span class="sxs-lookup"><span data-stu-id="49c8e-112">This service receives an application from a person who is in need of some credit.</span></span> <span data-ttu-id="49c8e-113">Esse serviço se comunica de forma assíncrona com `CreditCheckService` para decidir se o aplicativo de crédito é válido.</span><span class="sxs-lookup"><span data-stu-id="49c8e-113">This service communicates asynchronously with the `CreditCheckService` to decide whether the credit application is valid.</span></span>  
  
 <span data-ttu-id="49c8e-114">Cliente</span><span class="sxs-lookup"><span data-stu-id="49c8e-114">Client</span></span>  
 <span data-ttu-id="49c8e-115">O cliente se comunica com forma `RentalApprovalService` para saber se o crédito é certo.</span><span class="sxs-lookup"><span data-stu-id="49c8e-115">The client communicates synchronously with the `RentalApprovalService` to know whether the credit is approved.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="49c8e-116">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="49c8e-116">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="49c8e-117">Clique com o botão direito do mouse na solução **Comunicação Assíncrona** e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="49c8e-117">Right-click the **AsynchronousCommunication** solution and select **Properties**.</span></span>  
  
2. <span data-ttu-id="49c8e-118">Em **Propriedades Comuns,** selecione **Projeto de Inicialização**e selecione **Vários Projetos de Inicialização**.</span><span class="sxs-lookup"><span data-stu-id="49c8e-118">In **Common Properties**, select **Startup Project**, and select **Multiple Startup Projects**.</span></span>  
  
3. <span data-ttu-id="49c8e-119">Mova **RentalApprovalService** para a primeira posição da lista, seguido pelo **CreditCheckService**, seguido pelo **Cliente**.</span><span class="sxs-lookup"><span data-stu-id="49c8e-119">Move **RentalApprovalService** to the first position in the list, followed by **CreditCheckService**, followed by **Client**.</span></span> <span data-ttu-id="49c8e-120">Defina a ação **Iniciar** em todos os três projetos.</span><span class="sxs-lookup"><span data-stu-id="49c8e-120">Set the **Start** action on all three projects.</span></span>  
  
4. <span data-ttu-id="49c8e-121">Clique **em OK**e pressione F5 para executar a amostra.</span><span class="sxs-lookup"><span data-stu-id="49c8e-121">Click **OK**, and press F5 to run the sample.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="49c8e-122">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="49c8e-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="49c8e-123">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="49c8e-123">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="49c8e-124">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="49c8e-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="49c8e-125">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="49c8e-125">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\AsynchronousCommunication`
