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
ms.workload: dotnet
ms.openlocfilehash: a2c34506ca33af80b83f365893e56a5a9d437b89
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
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
