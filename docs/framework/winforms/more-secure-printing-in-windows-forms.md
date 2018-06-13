---
title: Impressão mais segura no Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, printing
- PrintingPermission class [Windows Forms], Windows Forms security
- printing [Windows Forms], security
- security [Windows Forms], printing
ms.assetid: 48fd36ac-872f-4de0-902a-e52969cd4367
ms.openlocfilehash: 976079f39e13186014b77e85c092c37be11238b7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538933"
---
# <a name="more-secure-printing-in-windows-forms"></a>Impressão mais segura no Windows Forms
Aplicativos dos Windows Forms com frequência incluem recursos de impressão. O [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] usa o <xref:System.Drawing.Printing.PrintingPermission> classe para controlar o acesso aos recursos de impressão e os respectivos <xref:System.Drawing.Printing.PrintingPermissionLevel> valor de enumeração para indicar o nível de acesso. Por padrão, a impressão é habilitada por padrão nas zonas da Internet e da Intranet Local. No entanto, o nível de acesso é restrito em ambas as zonas. Não importa se o seu aplicativo pode imprimir, requer interação do usuário ou não pode imprimir, isso dependerá do valor da permissão concedida ao aplicativo. Por padrão, a zona de Intranet Local recebe <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> recebe acesso e a zona da Intranet <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> acesso.  
  
 A tabela a seguir mostra a funcionalidade disponível em cada nível de permissão de impressão.  
  
|PrintingPermissionLevel|Descrição|  
|-----------------------------|-----------------|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>|Fornece acesso completo a todas as impressoras instaladas.|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>|Habilita a impressão programática para a impressora padrão e a impressão mais segura por meio de uma caixa de diálogo de impressão restritiva. <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> é um subconjunto de <xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>.|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>|Fornece impressão apenas em uma caixa de diálogo mais restrita. <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> é um subconjunto de <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>.|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting>|Impede o acesso a impressoras. <xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting> é um subconjunto de <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>.|  
  
## <a name="see-also"></a>Consulte também  
 [Acesso mais seguro a arquivos e a dados nos Windows Forms](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)  
 [Considerações adicionais sobre segurança nos Windows Forms](../../../docs/framework/winforms/additional-security-considerations-in-windows-forms.md)  
 [Visão geral da segurança dos Windows Forms](../../../docs/framework/winforms/security-in-windows-forms-overview.md)  
 [Segurança do Windows Forms](../../../docs/framework/winforms/windows-forms-security.md)
