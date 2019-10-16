---
title: Controlando a auto inicialização do host de serviço do WCF
ms.date: 03/30/2017
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
ms.openlocfilehash: 7f21cd7ea600277461146387b962a89ea0a8472b
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320620"
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a><span data-ttu-id="a4517-102">Controlando a auto inicialização do host de serviço do WCF</span><span class="sxs-lookup"><span data-stu-id="a4517-102">Controlling Auto-launching of WCF Service Host</span></span>
<span data-ttu-id="a4517-103">Você pode controlar o recurso de inicialização automática do host de serviço do Windows Communication Foundation (WCF) (WcfSvcHost. exe) para um projeto de biblioteca de serviço WCF, quando você depura outro projeto na mesma solução do Visual Studio que contém vários projetos.</span><span class="sxs-lookup"><span data-stu-id="a4517-103">You can control the auto-launching capability of Windows Communication Foundation (WCF) Service Host (WcfSvcHost.exe) for a WCF Service Library project, when you debug another project in the same Visual Studio solution containing multiple projects.</span></span>  
  
 <span data-ttu-id="a4517-104">Para fazer isso, clique com o botão direito do mouse no projeto de serviço WCF no **Gerenciador de soluções**, escolha **Propriedades**e clique na guia **Opções do WCF** . A caixa de seleção **Iniciar host de serviço WCF ao depurar outro projeto na mesma solução** está habilitada por padrão.</span><span class="sxs-lookup"><span data-stu-id="a4517-104">To do so, right-click the WCF Service Project in **Solution Explorer**, choose **Properties**, and click **WCF Options** tab. The **Start WCF Service Host when debugging another project in the same solution** check box is enabled by default.</span></span> <span data-ttu-id="a4517-105">Você pode desmarcar a caixa para que o host de serviço do WCF para esse projeto específico não seja iniciado quando outro projeto for depurado na mesma solução.</span><span class="sxs-lookup"><span data-stu-id="a4517-105">You can clear the box so that WCF Service Host for this specific project is not launched when another project is debugged in the same solution.</span></span>  
  
 <span data-ttu-id="a4517-106">Esse comportamento não afeta a depuração F5 ou Adicionar Referência de Serviço funcionalidades para este projeto.</span><span class="sxs-lookup"><span data-stu-id="a4517-106">This behavior does not affect the F5 debugging, or Add Service Reference functionalities for this project.</span></span>  
  
 <span data-ttu-id="a4517-107">Essa opção está disponível para os seguintes projetos:</span><span class="sxs-lookup"><span data-stu-id="a4517-107">This option is available to the following projects:</span></span>  
  
- <span data-ttu-id="a4517-108">Projeto de biblioteca de serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="a4517-108">WCF Service Library Project.</span></span>  
  
- <span data-ttu-id="a4517-109">Projeto de biblioteca de serviço de fluxo de trabalho Sequencial.</span><span class="sxs-lookup"><span data-stu-id="a4517-109">Sequential Workflow Service Library Project.</span></span>  
  
- <span data-ttu-id="a4517-110">Projeto de biblioteca do serviço de fluxo de trabalho de máquina de estado.</span><span class="sxs-lookup"><span data-stu-id="a4517-110">State Machine Workflow Service Library Project.</span></span>  
  
- <span data-ttu-id="a4517-111">Projeto de biblioteca de serviço de distribuição.</span><span class="sxs-lookup"><span data-stu-id="a4517-111">Syndication Service Library Project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4517-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a4517-112">See also</span></span>

- [<span data-ttu-id="a4517-113">Host de serviço do WCF (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="a4517-113">WCF Service Host (WcfSvcHost.exe)</span></span>](wcf-service-host-wcfsvchost-exe.md)
