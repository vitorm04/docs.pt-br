---
title: "Como dimensionar um controle de rótulo dos Windows Forms para encaixar o conteúdo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- captions [Windows Forms], sizing
- sizing controls
- size [Windows Forms], controls
- labels [Windows Forms], sizing to fit contents
- Label control [Windows Forms], sizing to fit contents
ms.assetid: 99648964-63b2-438c-980e-d24103ad602b
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bd89d72264e5837d2c41fcb0ab024a7b16f4205b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-size-a-windows-forms-label-control-to-fit-its-contents"></a>Como dimensionar um controle de rótulo dos Windows Forms para encaixar o conteúdo
Windows Forms <xref:System.Windows.Forms.Label> controle pode ser de linha única ou multilinha, e podem ser fixas no tamanho ou pode redimensionar automaticamente para acomodar a legenda. O <xref:System.Windows.Forms.Label.AutoSize%2A> propriedade ajuda a dimensionar os controles para caber legendas maiores ou menores, que é especialmente útil se a legenda será alterado em tempo de execução.  
  
### <a name="to-make-a-label-control-resize-dynamically-to-fit-its-contents"></a>Para fazer com que um controle de rótulo redimensionar dinamicamente para acomodar seu conteúdo  
  
1.  Definir seu <xref:System.Windows.Forms.Label.AutoSize%2A> propriedade `true`.  
  
 Se <xref:System.Windows.Forms.Label.AutoSize%2A> é definido como `false`, palavras especificadas no <xref:System.Windows.Forms.Label.Text%2A> propriedade ajustarão para a próxima linha se possível, mas o controle não aumentará.  
  
## <a name="see-also"></a>Consulte também  
 [Como criar teclas de acesso com controles de rótulo dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-access-keys-with-windows-forms-label-controls.md)  
 [Visão geral do controle Label](../../../../docs/framework/winforms/controls/label-control-overview-windows-forms.md)  
 [Controle de rótulo](../../../../docs/framework/winforms/controls/label-control-windows-forms.md)
