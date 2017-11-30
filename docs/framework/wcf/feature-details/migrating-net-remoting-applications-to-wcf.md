---
title: Migrando aplicativos remotos .NET para o WCF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: dff06fbc52c0f4371abf0bcc465fd6a6d8be5859
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="migrating-net-remoting-applications-to-wcf"></a><span data-ttu-id="9dbf5-102">Migrando aplicativos remotos .NET para o WCF</span><span class="sxs-lookup"><span data-stu-id="9dbf5-102">Migrating .NET Remoting Applications to WCF</span></span>
<span data-ttu-id="9dbf5-103">**Este tópico é específico para uma tecnologia herdada que é mantida para compatibilidade com aplicativos existentes e não é recomendada para novo desenvolvimento. Aplicativos distribuídos agora devem ser desenvolvidos usando [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].**</span><span class="sxs-lookup"><span data-stu-id="9dbf5-103">**This topic is specific to a legacy technology that is retained for backward compatibility with existing applications and is not recommended for new development. Distributed applications should now be developed using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].**</span></span>  
  
 <span data-ttu-id="9dbf5-104">Há duas maneiras para tirar proveito dos [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] com aplicativos existentes de .NET Remoting: migração e integração.</span><span class="sxs-lookup"><span data-stu-id="9dbf5-104">There are two ways to take advantage of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] with existing .NET Remoting applications: integration and migration.</span></span> <span data-ttu-id="9dbf5-105">A integração permite que o .net 2.0 de comunicação remota e [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] em execução lado a lado, que ajuda você expõe os mesmos objetos de negócios em ambas as tecnologias simultaneamente sem a necessidade de modificar seu .net existentes 2.0 de comunicação remota de código.</span><span class="sxs-lookup"><span data-stu-id="9dbf5-105">Integration allows you to have .Net Remoting 2.0 and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] running side by side, letting you expose the same business objects over both technologies simultaneously without having to modify your existing .Net Remoting 2.0 code.</span></span> <span data-ttu-id="9dbf5-106">Integração exige que você está executando [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 ou superior.</span><span class="sxs-lookup"><span data-stu-id="9dbf5-106">Integration requires that you are running on [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 or greater.</span></span> <span data-ttu-id="9dbf5-107">Se você quiser tirar proveito de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] recursos e não não precisam de transmissão compatibilidade com sistemas de comunicação remota 2.0, você pode migrar o serviço inteiro [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9dbf5-107">If you want to take advantage of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] features and do not need wire compatibility with Remoting 2.0 systems, you can migrate your entire service to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="9dbf5-108">Migração de comunicação remota do .NET 2.0 para [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] requer alterações para a interface do objeto remoto e suas configurações.</span><span class="sxs-lookup"><span data-stu-id="9dbf5-108">Migration from .NET Remoting 2.0 to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] requires changes to the remote object's interface and its configuration settings.</span></span> <span data-ttu-id="9dbf5-109">Ambos esses tópicos são abordados em [de comunicação remota para o Windows Communication Foundation](http://go.microsoft.com/fwlink/?LinkId=74403).</span><span class="sxs-lookup"><span data-stu-id="9dbf5-109">Both of these topics are covered in [From Remoting to the Windows Communication Foundation](http://go.microsoft.com/fwlink/?LinkId=74403).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dbf5-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9dbf5-110">See Also</span></span>  
 <span data-ttu-id="9dbf5-111">[Conceptual Overview](../../../../docs/framework/wcf/conceptual-overview.md) (Visão geral conceitual)</span><span class="sxs-lookup"><span data-stu-id="9dbf5-111">[Conceptual Overview](../../../../docs/framework/wcf/conceptual-overview.md)</span></span>
