---
title: "Como deixar o controle invisível em tempo de execução"
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
- controls [Windows Forms], making invisible at run time
- invisible controls
- user controls [Windows Forms], invisible
- custom controls [Windows Forms], invisible
- run time [Windows Forms], making controls invisible
ms.assetid: 69eb2e72-32f5-4f79-a157-c2c5f60c1628
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 310750df0786eb07158909eb5e322369d157d1cb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-make-your-control-invisible-at-run-time"></a>Como deixar o controle invisível em tempo de execução
Há vezes em que você quer criar um controle de usuário invisível em tempo de execução. Por exemplo, um controle que é um relógio despertador pode ser invisível, exceto quando o alarme foi acionado. Isso é feito facilmente configurando o <xref:System.Windows.Forms.Control.Visible%2A> propriedade. Se o <xref:System.Windows.Forms.Control.Visible%2A> é de propriedade `true`, o controle será exibido como normal. Se for `false`, o controle será ocultado. Embora o código em seu controle ainda possa ser executado enquanto invisível, você não poderá interagir com o controle por meio da interface do usuário. Se quiser criar um controle invisível que ainda responde à entrada do usuário (por exemplo, cliques de mouse), você deverá criar um controle transparente. Para obter mais informações, veja [Como dar ao controle de uma tela de fundo transparente](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md).  
  
### <a name="to-make-your-control-invisible-at-run-time"></a>Para deixar o controle invisível em tempo de execução  
  
1.  Defina a propriedade <xref:System.Windows.Forms.Control.Visible%2A> como `false`.  
  
    ```vb  
    ' To set the Visible property from within your object's own code.  
    Me.Visible = False  
    ' To set the Visible property from another object.  
    myControl1.Visible = False  
    ```  
  
    ```csharp  
    // To set the Visible property from within your object's own code.  
    this.Visible = false;  
    // To set the Visible property from another object.  
    myControl1.Visible = false;  
    ```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.Control.Visible%2A>  
 [Desenvolvendo controles dos Windows Forms personalizados com o .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [Como dar ao controle uma tela de fundo transparente](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)
