---
title: Controlando a auto inicialização do host de serviço do WCF
ms.date: 03/30/2017
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
ms.openlocfilehash: 806d85df2a7fff63704db755400b81cc2dc5c37b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64652083"
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a><span data-ttu-id="2e745-102">Controlando a auto inicialização do host de serviço do WCF</span><span class="sxs-lookup"><span data-stu-id="2e745-102">Controlling Auto-launching of WCF Service Host</span></span>
<span data-ttu-id="2e745-103">Você pode controlar o recurso a autoinicialização do Host de serviço do Windows Communication Foundation (WCF) (WcfSvcHost.exe) para um projeto de biblioteca de serviço WCF, quando você depurar outro projeto na mesma solução do Visual Studio que contém vários projetos.</span><span class="sxs-lookup"><span data-stu-id="2e745-103">You can control the auto-launching capability of Windows Communication Foundation (WCF) Service Host (WcfSvcHost.exe) for a WCF Service Library project, when you debug another project in the same Visual Studio solution containing multiple projects.</span></span>  
  
 <span data-ttu-id="2e745-104">Para fazer isso, clique com botão direito no projeto de serviço do WCF no **Gerenciador de soluções**, escolha **Properties**e clique em **opções do WCF** guia. O **iniciar durante a depuração de outro projeto na mesma solução o Host de serviço de WCF** caixa de seleção é habilitada por padrão.</span><span class="sxs-lookup"><span data-stu-id="2e745-104">To do so, right-click the WCF Service Project in **Solution Explorer**, choose **Properties**, and click **WCF Options** tab. The **Start WCF Service Host when debugging another project in the same solution** check box is enabled by default.</span></span> <span data-ttu-id="2e745-105">Você pode desmarcar a caixa para que o Host de serviço do WCF para esse projeto específico não é iniciada quando outro projeto é depurado na mesma solução.</span><span class="sxs-lookup"><span data-stu-id="2e745-105">You can clear the box so that WCF Service Host for this specific project is not launched when another project is debugged in the same solution.</span></span>  
  
 <span data-ttu-id="2e745-106">Esse comportamento não afeta a depuração F5, ou as funcionalidades de adicionar referência de serviço para este projeto.</span><span class="sxs-lookup"><span data-stu-id="2e745-106">This behavior does not affect the F5 debugging, or Add Service Reference functionalities for this project.</span></span>  
  
 <span data-ttu-id="2e745-107">Essa opção está disponível para os projetos a seguir:</span><span class="sxs-lookup"><span data-stu-id="2e745-107">This option is available to the following projects:</span></span>  
  
- <span data-ttu-id="2e745-108">Projeto de biblioteca de serviço do WCF.</span><span class="sxs-lookup"><span data-stu-id="2e745-108">WCF Service Library Project.</span></span>  
  
- <span data-ttu-id="2e745-109">Projeto de biblioteca de serviço de fluxo de trabalho sequencial.</span><span class="sxs-lookup"><span data-stu-id="2e745-109">Sequential Workflow Service Library Project.</span></span>  
  
- <span data-ttu-id="2e745-110">Projeto de biblioteca de serviço de fluxo de trabalho de máquina de estado.</span><span class="sxs-lookup"><span data-stu-id="2e745-110">State Machine Workflow Service Library Project.</span></span>  
  
- <span data-ttu-id="2e745-111">Projeto de biblioteca de serviço de sindicalização.</span><span class="sxs-lookup"><span data-stu-id="2e745-111">Syndication Service Library Project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e745-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2e745-112">See also</span></span>

- [<span data-ttu-id="2e745-113">Host de serviço do WCF (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="2e745-113">WCF Service Host (WcfSvcHost.exe)</span></span>](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
