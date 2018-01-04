---
title: "Como criar botões de alternância em controles ToolStrip"
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
- toggle buttons [Windows Forms], creating
- examples [Windows Forms], toolbars
- ToolStrip control [Windows Forms], creating toggle buttons
ms.assetid: d9c197df-4c65-43f2-beee-b68b52b2befc
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5547b35bda8054b3ca41435e04855408d8a77c8f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-toggle-buttons-in-toolstrip-controls"></a>Como criar botões de alternância em controles ToolStrip
Quando um usuário clica em um botão de alternância, ele aparece em baixo relevo e mantém a aparência de baixo relevo até que o usuário clica no botão novamente.  
  
### <a name="to-create-a-toggling-toolstripbutton"></a>Para criar uma alternância ToolStripButton  
  
-   Use o código como o exemplo de código a seguir. Esse código supõe que o formulário contém um <xref:System.Windows.Forms.ToolStrip> controle e que seu <xref:System.Windows.Forms.ToolStrip.Items%2A> coleção contém um <xref:System.Windows.Forms.ToolStripButton> chamado `toolStripButton1`. Ele também pressupõe que você tenha um manipulador de eventos chamado `toolStripButton1_CheckedChanged`.  
  
    ```vb  
    toolStripButton1.CheckOnClick = True  
    toolStripButton1.CheckedChanged AddressOf _  
    EventHandler(toolStripButton1_CheckedChanged);  
    ```  
  
    ```csharp  
    toolStripButton1.CheckOnClick = true;  
    toolStripButton1.CheckedChanged += new _  
    EventHandler(toolStripButton1_CheckedChanged);  
    ```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.ToolStripButton>  
 [Visão geral do controle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
