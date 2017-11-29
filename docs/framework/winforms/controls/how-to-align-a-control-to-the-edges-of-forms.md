---
title: "Como alinhar um controle às bordas de formulários"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dock property [Windows Forms], aligning controls (using code)
- forms [Windows Forms], aligning controls
- controls [Windows Forms], aligning on forms
- custom controls [Windows Forms], docking using code
ms.assetid: 5994cb59-242b-4e75-bd0e-62879c34d702
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a55212ac4d770848355ace1b0ef3fff3cc50f871
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-align-a-control-to-the-edges-of-forms"></a>Como alinhar um controle às bordas de formulários
Você pode fazer com que o seu controle alinhe a borda de formulários, definindo o <xref:System.Windows.Forms.Control.Dock%2A> propriedade. Essa propriedade determina onde reside o controle no formulário. O <xref:System.Windows.Forms.Control.Dock%2A> propriedade pode ser definida com os seguintes valores:  
  
|Configuração|Efeito no seu controle|  
|-------------|----------------------------|  
|<xref:System.Windows.Forms.DockStyle.Bottom>|Encaixa na parte inferior do formulário.|  
|<xref:System.Windows.Forms.DockStyle.Fill>|Preenche todo o espaço restante no formulário.|  
|<xref:System.Windows.Forms.DockStyle.Left>|Encaixa do lado esquerdo do formulário.|  
|<xref:System.Windows.Forms.DockStyle.None>|Faz não encaixe em qualquer local e ele aparece no local especificado por seu <xref:System.Windows.Forms.Control.Location%2A> propriedade.|  
|<xref:System.Windows.Forms.DockStyle.Right>|Encaixa do lado direito do formulário.|  
|<xref:System.Windows.Forms.DockStyle.Top>|Encaixa na parte superior do formulário.|  
  
 Não há suporte de tempo de design para esse recurso no Visual Studio.  
  
### <a name="to-set-the-dock-property-for-your-control-at-run-time"></a>Para definir a propriedade Dock de controle de tempo de execução  
  
1.  Definir o <xref:System.Windows.Forms.Control.Dock%2A> propriedade para o valor apropriado no código.  
  
    ```vb  
    ' To set the Dock property internally.  
    Me.Dock = DockStyle.Top  
    ' To set the Dock property from another object.  
    UserControl1.Dock = DockStyle.Top  
    ```  
  
    ```csharp  
    // To set the Dock property internally.  
    this.Dock = DockStyle.Top;  
    // To set the Dock property from another object.  
    UserControl1.Dock = DockStyle.Top;  
    ```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType>  
 [Desenvolvendo controles dos Windows Forms personalizados com o .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [Como ancorar e encaixar controles filho em um controle FlowLayoutPanel](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)  
 [Como ancorar e encaixar controles filho em um controle TableLayoutPanel](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [Visão geral da propriedade AutoSize](../../../../docs/framework/winforms/controls/autosize-property-overview.md)
