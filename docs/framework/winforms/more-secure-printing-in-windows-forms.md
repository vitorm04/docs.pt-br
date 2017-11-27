---
title: "Impressão mais segura no Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, printing
- PrintingPermission class [Windows Forms], Windows Forms security
- printing [Windows Forms], security
- security [Windows Forms], printing
ms.assetid: 48fd36ac-872f-4de0-902a-e52969cd4367
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b89a94fd0223d817b0dee37f7a3ed84dcbacbbec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="more-secure-printing-in-windows-forms"></a><span data-ttu-id="e5696-102">Impressão mais segura no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e5696-102">More Secure Printing in Windows Forms</span></span>
<span data-ttu-id="e5696-103">Aplicativos dos Windows Forms com frequência incluem recursos de impressão.</span><span class="sxs-lookup"><span data-stu-id="e5696-103">Windows Forms applications frequently include printing abilities.</span></span> <span data-ttu-id="e5696-104">O [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] usa o <xref:System.Drawing.Printing.PrintingPermission> classe para controlar o acesso aos recursos de impressão e os respectivos <xref:System.Drawing.Printing.PrintingPermissionLevel> valor de enumeração para indicar o nível de acesso.</span><span class="sxs-lookup"><span data-stu-id="e5696-104">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] uses the <xref:System.Drawing.Printing.PrintingPermission> class to control access to printing capabilities and the associated <xref:System.Drawing.Printing.PrintingPermissionLevel> enumeration value to indicate the level of access.</span></span> <span data-ttu-id="e5696-105">Por padrão, a impressão é habilitada por padrão nas zonas da Internet e da Intranet Local. No entanto, o nível de acesso é restrito em ambas as zonas.</span><span class="sxs-lookup"><span data-stu-id="e5696-105">By default, printing is enabled by default in the Local Intranet and Internet zones; however, the level of access is restricted in both zones.</span></span> <span data-ttu-id="e5696-106">Não importa se o seu aplicativo pode imprimir, requer interação do usuário ou não pode imprimir, isso dependerá do valor da permissão concedida ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e5696-106">Whether your application can print, requires user interaction, or cannot print depends upon the permission value granted to the application.</span></span> <span data-ttu-id="e5696-107">Por padrão, a zona de Intranet Local recebe <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> recebe acesso e a zona da Intranet <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> acesso.</span><span class="sxs-lookup"><span data-stu-id="e5696-107">By default, the Local Intranet zone receives <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> access and the Intranet zone receives <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> access.</span></span>  
  
 <span data-ttu-id="e5696-108">A tabela a seguir mostra a funcionalidade disponível em cada nível de permissão de impressão.</span><span class="sxs-lookup"><span data-stu-id="e5696-108">The following table shows the functionality available at each printing permission level.</span></span>  
  
|<span data-ttu-id="e5696-109">PrintingPermissionLevel</span><span class="sxs-lookup"><span data-stu-id="e5696-109">PrintingPermissionLevel</span></span>|<span data-ttu-id="e5696-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="e5696-110">Description</span></span>|  
|-----------------------------|-----------------|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>|<span data-ttu-id="e5696-111">Fornece acesso completo a todas as impressoras instaladas.</span><span class="sxs-lookup"><span data-stu-id="e5696-111">Provides full access to all installed printers.</span></span>|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>|<span data-ttu-id="e5696-112">Habilita a impressão programática para a impressora padrão e a impressão mais segura por meio de uma caixa de diálogo de impressão restritiva.</span><span class="sxs-lookup"><span data-stu-id="e5696-112">Enables programmatic printing to the default printer and safer printing through a restrictive printing dialog box.</span></span> <span data-ttu-id="e5696-113"><xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> é um subconjunto de <xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>.</span><span class="sxs-lookup"><span data-stu-id="e5696-113"><xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> is a subset of <xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>.</span></span>|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>|<span data-ttu-id="e5696-114">Fornece impressão apenas em uma caixa de diálogo mais restrita.</span><span class="sxs-lookup"><span data-stu-id="e5696-114">Provides printing only from a more-restricted dialog box.</span></span> <span data-ttu-id="e5696-115"><xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> é um subconjunto de <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>.</span><span class="sxs-lookup"><span data-stu-id="e5696-115"><xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> is a subset of <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>.</span></span>|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting>|<span data-ttu-id="e5696-116">Impede o acesso a impressoras.</span><span class="sxs-lookup"><span data-stu-id="e5696-116">Prevents access to printers.</span></span> <span data-ttu-id="e5696-117"><xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting> é um subconjunto de <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>.</span><span class="sxs-lookup"><span data-stu-id="e5696-117"><xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting> is a subset of <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e5696-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e5696-118">See Also</span></span>  
 [<span data-ttu-id="e5696-119">Acesso mais seguro a arquivos e a dados nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e5696-119">More Secure File and Data Access in Windows Forms</span></span>](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)  
 [<span data-ttu-id="e5696-120">Considerações adicionais sobre segurança nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e5696-120">Additional Security Considerations in Windows Forms</span></span>](../../../docs/framework/winforms/additional-security-considerations-in-windows-forms.md)  
 [<span data-ttu-id="e5696-121">Visão geral da segurança dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e5696-121">Security in Windows Forms Overview</span></span>](../../../docs/framework/winforms/security-in-windows-forms-overview.md)  
 [<span data-ttu-id="e5696-122">Segurança do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e5696-122">Windows Forms Security</span></span>](../../../docs/framework/winforms/windows-forms-security.md)
