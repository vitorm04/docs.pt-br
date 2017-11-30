---
title: Como agrupar controles com o controle GroupBox dos Windows Forms
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], grouping
- GroupBox control [Windows Forms], grouping controls
- Windows Forms controls, grouping
ms.assetid: 0bda316d-bd2a-43aa-ac73-342453303169
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 50d29de04b4e221105bb02e58de01344f13af69f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-group-controls-with-the-windows-forms-groupbox-control"></a>Como agrupar controles com o controle GroupBox dos Windows Forms
Windows Forms <xref:System.Windows.Forms.GroupBox> controles são usados para agrupar outros controles. Há três razões para agrupar controles:  
  
-   Para criar um agrupamento visual dos elementos de formulário relacionados para uma interface do usuário clara.  
  
-   Para criar um agrupamento programático (de botões de opção, por exemplo).  
  
-   Para mover os controles como uma unidade em tempo de design.  
  
### <a name="to-create-a-group-of-controls"></a>Para criar um grupo de controles  
  
1.  Desenhar um <xref:System.Windows.Forms.GroupBox> controle em um formulário.  
  
2.  Adicione outros controles à caixa de grupo desenhando cada um deles dentro da caixa de grupo.  
  
     Se você tiver controles existentes que você deseja incluir em uma caixa de grupo, você pode selecionar todos os controles, recortá-los para a área de transferência, selecione o <xref:System.Windows.Forms.GroupBox> de controle e, em seguida, cole-os na caixa de grupo. Você também pode arrastá-los para a caixa de grupo.  
  
3.  Definir o <xref:System.Windows.Forms.GroupBox.Text%2A> propriedade da caixa de grupo para uma legenda apropriada.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.GroupBox>  
 [Controle GroupBox](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md)
