---
title: Controlando a auto inicialização do host de serviço do WCF
ms.date: 03/30/2017
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
ms.openlocfilehash: 63c3ca00c0cdc0b28de0fe245b616acd04ca50fe
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809882"
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a><span data-ttu-id="05d50-102">Controlando a auto inicialização do host de serviço do WCF</span><span class="sxs-lookup"><span data-stu-id="05d50-102">Controlling Auto-launching of WCF Service Host</span></span>
<span data-ttu-id="05d50-103">Você pode controlar o recurso auto inicialização do Host de serviço do Windows Communication Foundation (WCF) (WcfSvcHost.exe) para um projeto de biblioteca de serviços WCF, quando você depurar outro projeto na mesma solução do Visual Studio que contém vários projetos.</span><span class="sxs-lookup"><span data-stu-id="05d50-103">You can control the auto-launching capability of Windows Communication Foundation (WCF) Service Host (WcfSvcHost.exe) for a WCF Service Library project, when you debug another project in the same Visual Studio solution containing multiple projects.</span></span>  
  
 <span data-ttu-id="05d50-104">Para fazer isso, clique com botão direito no projeto de serviço do WCF no **Solution Explorer**, escolha **propriedades**e clique em **WCF opções** guia. O **iniciar ao depurar outro projeto na mesma solução o Host de serviço de WCF** caixa de seleção é habilitada por padrão.</span><span class="sxs-lookup"><span data-stu-id="05d50-104">To do so, right-click the WCF Service Project in **Solution Explorer**, choose **Properties**, and click **WCF Options** tab. The **Start WCF Service Host when debugging another project in the same solution** check box is enabled by default.</span></span> <span data-ttu-id="05d50-105">Você pode desmarcar a caixa para que o Host de serviço do WCF para este projeto específico não é iniciado quando o outro projeto é depurado na mesma solução.</span><span class="sxs-lookup"><span data-stu-id="05d50-105">You can clear the box so that WCF Service Host for this specific project is not launched when another project is debugged in the same solution.</span></span>  
  
 <span data-ttu-id="05d50-106">Esse comportamento não afeta a depuração F5 ou funcionalidades adicionar referência de serviço para este projeto.</span><span class="sxs-lookup"><span data-stu-id="05d50-106">This behavior does not affect the F5 debugging, or Add Service Reference functionalities for this project.</span></span>  
  
 <span data-ttu-id="05d50-107">Essa opção está disponível para os projetos a seguir:</span><span class="sxs-lookup"><span data-stu-id="05d50-107">This option is available to the following projects:</span></span>  
  
-   <span data-ttu-id="05d50-108">Projeto de biblioteca de serviço do WCF.</span><span class="sxs-lookup"><span data-stu-id="05d50-108">WCF Service Library Project.</span></span>  
  
-   <span data-ttu-id="05d50-109">Projeto de biblioteca de serviço de fluxo de trabalho sequencial.</span><span class="sxs-lookup"><span data-stu-id="05d50-109">Sequential Workflow Service Library Project.</span></span>  
  
-   <span data-ttu-id="05d50-110">Projeto de biblioteca de serviço de fluxo de trabalho de máquina de estado.</span><span class="sxs-lookup"><span data-stu-id="05d50-110">State Machine Workflow Service Library Project.</span></span>  
  
-   <span data-ttu-id="05d50-111">Projeto de biblioteca de serviço de distribuição.</span><span class="sxs-lookup"><span data-stu-id="05d50-111">Syndication Service Library Project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05d50-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="05d50-112">See Also</span></span>  
 [<span data-ttu-id="05d50-113">Host de serviço do WCF (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="05d50-113">WCF Service Host (WcfSvcHost.exe)</span></span>](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
