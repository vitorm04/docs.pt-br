---
title: Migrando aplicativos remotos .NET para o WCF
ms.date: 03/30/2017
helpviewer_keywords:
- ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
ms.openlocfilehash: 4040fb0ac223f91705a49b733f6a1f42d144068e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62046600"
---
# <a name="migrating-net-remoting-applications-to-wcf"></a><span data-ttu-id="0416e-102">Migrando aplicativos remotos .NET para o WCF</span><span class="sxs-lookup"><span data-stu-id="0416e-102">Migrating .NET Remoting Applications to WCF</span></span>
<span data-ttu-id="0416e-103">**Este tópico é específico para uma tecnologia herdada que é mantida para compatibilidade com versões anteriores com aplicativos existentes e não é recomendada para novo desenvolvimento. Aplicativos distribuídos agora devem ser desenvolvidos usando o WCF.**</span><span class="sxs-lookup"><span data-stu-id="0416e-103">**This topic is specific to a legacy technology that is retained for backward compatibility with existing applications and is not recommended for new development. Distributed applications should now be developed using WCF.**</span></span>  
  
 <span data-ttu-id="0416e-104">Há duas maneiras para tirar proveito do WCF com aplicativos existentes do .NET Remoting: migração e integração.</span><span class="sxs-lookup"><span data-stu-id="0416e-104">There are two ways to take advantage of WCF with existing .NET Remoting applications: integration and migration.</span></span> <span data-ttu-id="0416e-105">Integração permite que você tenha o .NET Remoting 2.0 e do WCF em execução lado a lado, permitindo que você exponha os mesmos objetos de negócios sobre ambas as tecnologias simultaneamente sem a necessidade de modificar seu código .NET Remoting 2.0 existente.</span><span class="sxs-lookup"><span data-stu-id="0416e-105">Integration allows you to have .NET Remoting 2.0 and WCF running side by side, letting you expose the same business objects over both technologies simultaneously without having to modify your existing .NET Remoting 2.0 code.</span></span> <span data-ttu-id="0416e-106">A integração requer que você esteja executando no [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 ou superior.</span><span class="sxs-lookup"><span data-stu-id="0416e-106">Integration requires that you are running on [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 or greater.</span></span> <span data-ttu-id="0416e-107">Se você quiser tirar proveito dos recursos do WCF e não é necessário para compatibilidade com sistemas de comunicação remota 2.0 de transferência, você pode migrar todo o seu serviço para o WCF.</span><span class="sxs-lookup"><span data-stu-id="0416e-107">If you want to take advantage of WCF features and do not need wire compatibility with Remoting 2.0 systems, you can migrate your entire service to WCF.</span></span> <span data-ttu-id="0416e-108">Migração do .NET Remoting 2.0 para o WCF requer alterações a interface do objeto remoto e seus parâmetros de configuração.</span><span class="sxs-lookup"><span data-stu-id="0416e-108">Migration from .NET Remoting 2.0 to WCF requires changes to the remote object's interface and its configuration settings.</span></span> <span data-ttu-id="0416e-109">Esses tópicos são abordados [de comunicação remota para o Windows Communication Foundation](https://go.microsoft.com/fwlink/?LinkId=74403).</span><span class="sxs-lookup"><span data-stu-id="0416e-109">Both of these topics are covered in [From Remoting to the Windows Communication Foundation](https://go.microsoft.com/fwlink/?LinkId=74403).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0416e-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0416e-110">See also</span></span>

- [<span data-ttu-id="0416e-111">Visão geral conceitual</span><span class="sxs-lookup"><span data-stu-id="0416e-111">Conceptual Overview</span></span>](../../../../docs/framework/wcf/conceptual-overview.md)
