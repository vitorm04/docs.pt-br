---
title: Exemplo de compensação personalizado
ms.date: 03/30/2017
ms.assetid: 385920da-9284-44bf-9fe9-0d87c7478ec5
ms.openlocfilehash: ac141a48f87f5b14f6b528f7b3ceb7fdddeaf2d2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43503713"
---
# <a name="custom-compensation-sample"></a><span data-ttu-id="eca19-102">Exemplo de compensação personalizado</span><span class="sxs-lookup"><span data-stu-id="eca19-102">Custom Compensation Sample</span></span>
<span data-ttu-id="eca19-103">Este exemplo mostra como usar <xref:System.Activities.Statements.CompensableActivity> e seu manipulador de compensação para definir a lógica personalizada de compensação.</span><span class="sxs-lookup"><span data-stu-id="eca19-103">This sample shows how to use <xref:System.Activities.Statements.CompensableActivity> and its compensation handler to define custom compensation logic.</span></span> <span data-ttu-id="eca19-104">O cenário modelado nesse exemplo é uma agência de arrendamento do caminhão.</span><span class="sxs-lookup"><span data-stu-id="eca19-104">The scenario modeled in this sample is a Truck Rental Agency.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="eca19-105">Detalhes de exemplo</span><span class="sxs-lookup"><span data-stu-id="eca19-105">Sample Details</span></span>  
 <span data-ttu-id="eca19-106">As etapas simuladas são:</span><span class="sxs-lookup"><span data-stu-id="eca19-106">The steps simulated are:</span></span>  
  
1.  <span data-ttu-id="eca19-107">As aspas alugado do caminhão de um usuário por uma determinada data.</span><span class="sxs-lookup"><span data-stu-id="eca19-107">The user requests truck rental quotes for a given date.</span></span>  
  
2.  <span data-ttu-id="eca19-108">Três empresas do caminhão são entradas em contato e as três aspas são fornecidas.</span><span class="sxs-lookup"><span data-stu-id="eca19-108">Three truck companies are contacted and the three quotes are provided.</span></span>  
  
3.  <span data-ttu-id="eca19-109">O usuário seleciona uma citação do caminhão e continua a ordem pelo cartão de crédito.</span><span class="sxs-lookup"><span data-stu-id="eca19-109">The user selects one truck quote and proceeds to order by credit card.</span></span>  
  
4.  <span data-ttu-id="eca19-110">O aplicativo cancela as outras aspas de dois caminhões.</span><span class="sxs-lookup"><span data-stu-id="eca19-110">The application cancels the other two truck quotes.</span></span>  
  
5.  <span data-ttu-id="eca19-111">O aplicativo carrega uma taxa de serviço que é não reembolsável para contas não superiores se cancelamento acontece 10 dias ou menos antes da data de retorno.</span><span class="sxs-lookup"><span data-stu-id="eca19-111">The application charges a service fee that is non-refundable for non-premium accounts if cancelation happens 10 days or less prior to the reservation date.</span></span>  
  
6.  <span data-ttu-id="eca19-112">O aplicativo carrega a taxa de alugado caminhão.</span><span class="sxs-lookup"><span data-stu-id="eca19-112">The application charges the truck rental fee.</span></span>  
  
7.  <span data-ttu-id="eca19-113">O aplicativo esperado até a data de fallback ou até que o cliente decidir cancelar a reserva, qualquer vem primeiro.</span><span class="sxs-lookup"><span data-stu-id="eca19-113">The application waits until the reservation date or until the customer decided to cancel the reservation, whichever comes first.</span></span>  
  
8.  <span data-ttu-id="eca19-114">Se o cliente cancela a reserva, lógica personalizada de compensação de <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> é executado de acordo com a seguinte lógica:</span><span class="sxs-lookup"><span data-stu-id="eca19-114">If the customer cancels the reservation, the <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> custom compensation logic runs according to the following logic:</span></span>  
  
    1.  <span data-ttu-id="eca19-115">Se o cliente tem uma conta não superior e é menor que 10 dias de data de retorno, então a taxa de serviço é carregada ainda; caso contrário, o aplicativo reembolsa a taxa de serviço.</span><span class="sxs-lookup"><span data-stu-id="eca19-115">If the customer has a non-premium account and it is less than 10 days prior to the reservation date, then the service fee is still charged; otherwise, the application refunds the service fee.</span></span>  
  
    2.  <span data-ttu-id="eca19-116">O resto das atividades compensáveis (taxa de pedido de caminhão + ordem de caminhão) é executado de acordo com a lógica padrão de compensação, que é compensar em ordem inversa de execução.</span><span class="sxs-lookup"><span data-stu-id="eca19-116">The rest of the compensable activities (truck order + truck order fee) are run according to the default compensation logic, which is to compensate in reverse order of execution.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="eca19-117">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="eca19-117">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="eca19-118">Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra a solução de CustomCompensation.sln.</span><span class="sxs-lookup"><span data-stu-id="eca19-118">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the CustomCompensation.sln solution.</span></span> <span data-ttu-id="eca19-119">Ele está localizado no diretório \ WF básico compensação \ \ \ CustomCompensation.</span><span class="sxs-lookup"><span data-stu-id="eca19-119">It is located in the \WF\Basic\Compensation\CustomCompensation directory.</span></span>  
  
2.  <span data-ttu-id="eca19-120">Pressione CTRL+SHIFT+B para criar a solução.</span><span class="sxs-lookup"><span data-stu-id="eca19-120">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="eca19-121">O pressionar o CTRL + F5 para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="eca19-121">Press CTRL + F5 to run the application.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="eca19-122">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="eca19-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="eca19-123">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="eca19-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="eca19-124">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="eca19-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="eca19-125">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="eca19-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\CustomCompensation`