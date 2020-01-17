---
title: Migrando aplicativos remotos .NET para o WCF
ms.date: 03/30/2017
helpviewer_keywords:
- ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
ms.openlocfilehash: 1d7edab8ad89660f3384d0ccf556384175c4d5db
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76212159"
---
# <a name="migrating-net-remoting-applications-to-wcf"></a><span data-ttu-id="bca15-102">Migrando aplicativos remotos .NET para o WCF</span><span class="sxs-lookup"><span data-stu-id="bca15-102">Migrating .NET Remoting Applications to WCF</span></span>
<span data-ttu-id="bca15-103">**Este tópico é específico para uma tecnologia herdada que é mantida para compatibilidade com versões anteriores com aplicativos existentes e não é recomendada para desenvolvimento novo. Agora, os aplicativos distribuídos devem ser desenvolvidos usando o WCF.**</span><span class="sxs-lookup"><span data-stu-id="bca15-103">**This topic is specific to a legacy technology that is retained for backward compatibility with existing applications and is not recommended for new development. Distributed applications should now be developed using WCF.**</span></span>  
  
 <span data-ttu-id="bca15-104">Há duas maneiras de aproveitar o WCF com os aplicativos existentes de comunicação remota do .NET: integração e migração.</span><span class="sxs-lookup"><span data-stu-id="bca15-104">There are two ways to take advantage of WCF with existing .NET Remoting applications: integration and migration.</span></span> <span data-ttu-id="bca15-105">A integração permite que você tenha o .NET Remoting 2,0 e o WCF em execução lado a lado, permitindo que você exponha os mesmos objetos de negócios em ambas as tecnologias simultaneamente, sem a necessidade de modificar seu código .NET Remoting 2,0 existente.</span><span class="sxs-lookup"><span data-stu-id="bca15-105">Integration allows you to have .NET Remoting 2.0 and WCF running side by side, letting you expose the same business objects over both technologies simultaneously without having to modify your existing .NET Remoting 2.0 code.</span></span> <span data-ttu-id="bca15-106">A integração requer que você esteja executando o .NET Framework 2,0 ou superior.</span><span class="sxs-lookup"><span data-stu-id="bca15-106">Integration requires that you are running on .NET Framework 2.0 or greater.</span></span> <span data-ttu-id="bca15-107">Se você quiser aproveitar os recursos do WCF e não precisar de compatibilidade de conexão com os sistemas de comunicação remota 2,0, poderá migrar todo o serviço para o WCF.</span><span class="sxs-lookup"><span data-stu-id="bca15-107">If you want to take advantage of WCF features and do not need wire compatibility with Remoting 2.0 systems, you can migrate your entire service to WCF.</span></span> <span data-ttu-id="bca15-108">A migração do .NET Remoting 2,0 para o WCF requer alterações na interface do objeto remoto e em suas definições de configuração.</span><span class="sxs-lookup"><span data-stu-id="bca15-108">Migration from .NET Remoting 2.0 to WCF requires changes to the remote object's interface and its configuration settings.</span></span> <span data-ttu-id="bca15-109">Esses dois tópicos são abordados na [comunicação remota com o Windows Communication Foundation](https://docs.microsoft.com/previous-versions/aa730857(v=vs.80)).</span><span class="sxs-lookup"><span data-stu-id="bca15-109">Both of these topics are covered in [From Remoting to the Windows Communication Foundation](https://docs.microsoft.com/previous-versions/aa730857(v=vs.80)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bca15-110">Veja também</span><span class="sxs-lookup"><span data-stu-id="bca15-110">See also</span></span>

- [<span data-ttu-id="bca15-111">Visão geral conceitual</span><span class="sxs-lookup"><span data-stu-id="bca15-111">Conceptual Overview</span></span>](../../../../docs/framework/wcf/conceptual-overview.md)
