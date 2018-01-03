---
title: MEF para .NET para aplicativos da Windows Store
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7667770e-d163-4ad6-a303-085cf73db2f2
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8436bff3b6ca1061621a67eb45bdc8aedea33f2c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="mef-for-net-for-windows-store-apps"></a><span data-ttu-id="fee7b-102">MEF para .NET para aplicativos da Windows Store</span><span class="sxs-lookup"><span data-stu-id="fee7b-102">MEF for .NET for Windows Store Apps</span></span>
<span data-ttu-id="fee7b-103"><xref:System.Composition?displayProperty=nameWithType>e seus namespaces filho contêm tipos para desenvolvimento extensíveis [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplicativos com o Managed Extensibility Framework (MEF).</span><span class="sxs-lookup"><span data-stu-id="fee7b-103"><xref:System.Composition?displayProperty=nameWithType> and its child namespaces contain types for developing extensible [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps with Managed Extensibility Framework (MEF).</span></span> <span data-ttu-id="fee7b-104">Esses namespaces são parte do [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] subconjunto para o [!INCLUDE[win8](../../../includes/win8-md.md)] sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="fee7b-104">These namespaces are part of the [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] subset for the [!INCLUDE[win8](../../../includes/win8-md.md)] operating system.</span></span>  
  
 <span data-ttu-id="fee7b-105">Esses namespaces não fazem parte da biblioteca de classes principal distribuída com o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fee7b-105">These namespaces are not part of the core class library distributed with the .NET Framework.</span></span> <span data-ttu-id="fee7b-106">Para instalar esses namespaces, abra seu projeto no [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], escolha **gerenciar pacotes NuGet** do **projeto** menu e pesquise online o pacote Composition.</span><span class="sxs-lookup"><span data-stu-id="fee7b-106">To install these namespaces, open your project in [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choose **Manage NuGet Packages** from the **Project** menu, and search online for the Microsoft.Composition package.</span></span>  
  
-   <span data-ttu-id="fee7b-107"><xref:System.Composition?displayProperty=nameWithType>fornece classes que constituem o principal MEF para [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplicativos.</span><span class="sxs-lookup"><span data-stu-id="fee7b-107"><xref:System.Composition?displayProperty=nameWithType> provides classes that constitute the core MEF for [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps.</span></span>  
  
-   <span data-ttu-id="fee7b-108"><xref:System.Composition.Convention?displayProperty=nameWithType>fornece tipos que oferece suporte ao uso de MEF com um modelo de configuração baseado em convenção.</span><span class="sxs-lookup"><span data-stu-id="fee7b-108"><xref:System.Composition.Convention?displayProperty=nameWithType> provides types that support using MEF with a convention-based configuration model.</span></span>  
  
-   <span data-ttu-id="fee7b-109"><xref:System.Composition.Hosting?displayProperty=nameWithType>fornece tipos MEF que são úteis para desenvolvedores de aplicativos de host.</span><span class="sxs-lookup"><span data-stu-id="fee7b-109"><xref:System.Composition.Hosting?displayProperty=nameWithType> provides MEF types that are useful to developers of host applications.</span></span>  
  
-   <span data-ttu-id="fee7b-110"><xref:System.Composition.Hosting.Core?displayProperty=nameWithType>fornece tipos MEF usados internamente pelo mecanismo de composição.</span><span class="sxs-lookup"><span data-stu-id="fee7b-110"><xref:System.Composition.Hosting.Core?displayProperty=nameWithType> provides MEF types used internally by the composition engine.</span></span>  
  
 <span data-ttu-id="fee7b-111">Para obter mais informações sobre [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] e uma lista de namespaces e tipos que ele contém, consulte [visão geral de aplicativos .NET da Windows Store](http://go.microsoft.com/fwlink/p/?LinkID=238312) no Centro de desenvolvimento do Windows.</span><span class="sxs-lookup"><span data-stu-id="fee7b-111">For more information about [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] and a list of namespaces and types that it contains, see [.NET for Windows Store apps overview](http://go.microsoft.com/fwlink/p/?LinkID=238312) in the Windows Dev Center.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fee7b-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fee7b-112">See Also</span></span>  
 [<span data-ttu-id="fee7b-113">Visão geral de aplicativos .NET da Windows Store</span><span class="sxs-lookup"><span data-stu-id="fee7b-113">.NET for Windows Store apps overview</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=238312)  
 [<span data-ttu-id="fee7b-114">.NET para aplicativos da Windows Store – APIs com suporte</span><span class="sxs-lookup"><span data-stu-id="fee7b-114">.NET for Windows Store apps – supported APIs</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=247912)  
 [<span data-ttu-id="fee7b-115">MEF (Managed Extensibility Framework)</span><span class="sxs-lookup"><span data-stu-id="fee7b-115">Managed Extensibility Framework (MEF)</span></span>](../../../docs/framework/mef/index.md)
