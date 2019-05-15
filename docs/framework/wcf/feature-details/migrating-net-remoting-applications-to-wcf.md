---
title: Migrando aplicativos remotos .NET para o WCF
ms.date: 03/30/2017
helpviewer_keywords:
- ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
ms.openlocfilehash: c0ce7c9badc8bad6eedc58827b6efe2595ab2cf8
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592873"
---
# <a name="migrating-net-remoting-applications-to-wcf"></a><span data-ttu-id="26ed3-102">Migrando aplicativos remotos .NET para o WCF</span><span class="sxs-lookup"><span data-stu-id="26ed3-102">Migrating .NET Remoting Applications to WCF</span></span>
<span data-ttu-id="26ed3-103">**Este tópico é específico para uma tecnologia herdada que é mantida para compatibilidade com versões anteriores com aplicativos existentes e não é recomendada para novo desenvolvimento. Aplicativos distribuídos agora devem ser desenvolvidos usando o WCF.**</span><span class="sxs-lookup"><span data-stu-id="26ed3-103">**This topic is specific to a legacy technology that is retained for backward compatibility with existing applications and is not recommended for new development. Distributed applications should now be developed using WCF.**</span></span>  
  
 <span data-ttu-id="26ed3-104">Há duas maneiras para tirar proveito do WCF com aplicativos existentes do .NET Remoting: migração e integração.</span><span class="sxs-lookup"><span data-stu-id="26ed3-104">There are two ways to take advantage of WCF with existing .NET Remoting applications: integration and migration.</span></span> <span data-ttu-id="26ed3-105">Integração permite que você tenha o .NET Remoting 2.0 e do WCF em execução lado a lado, permitindo que você exponha os mesmos objetos de negócios sobre ambas as tecnologias simultaneamente sem a necessidade de modificar seu código .NET Remoting 2.0 existente.</span><span class="sxs-lookup"><span data-stu-id="26ed3-105">Integration allows you to have .NET Remoting 2.0 and WCF running side by side, letting you expose the same business objects over both technologies simultaneously without having to modify your existing .NET Remoting 2.0 code.</span></span> <span data-ttu-id="26ed3-106">A integração requer que você está executando no .NET Framework 2.0 ou superior.</span><span class="sxs-lookup"><span data-stu-id="26ed3-106">Integration requires that you are running on .NET Framework 2.0 or greater.</span></span> <span data-ttu-id="26ed3-107">Se você quiser tirar proveito dos recursos do WCF e não é necessário para compatibilidade com sistemas de comunicação remota 2.0 de transferência, você pode migrar todo o seu serviço para o WCF.</span><span class="sxs-lookup"><span data-stu-id="26ed3-107">If you want to take advantage of WCF features and do not need wire compatibility with Remoting 2.0 systems, you can migrate your entire service to WCF.</span></span> <span data-ttu-id="26ed3-108">Migração do .NET Remoting 2.0 para o WCF requer alterações a interface do objeto remoto e seus parâmetros de configuração.</span><span class="sxs-lookup"><span data-stu-id="26ed3-108">Migration from .NET Remoting 2.0 to WCF requires changes to the remote object's interface and its configuration settings.</span></span> <span data-ttu-id="26ed3-109">Esses tópicos são abordados [de comunicação remota para o Windows Communication Foundation](https://go.microsoft.com/fwlink/?LinkId=74403).</span><span class="sxs-lookup"><span data-stu-id="26ed3-109">Both of these topics are covered in [From Remoting to the Windows Communication Foundation](https://go.microsoft.com/fwlink/?LinkId=74403).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26ed3-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="26ed3-110">See also</span></span>

- [<span data-ttu-id="26ed3-111">Visão geral conceitual</span><span class="sxs-lookup"><span data-stu-id="26ed3-111">Conceptual Overview</span></span>](../../../../docs/framework/wcf/conceptual-overview.md)
