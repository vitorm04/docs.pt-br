---
title: Dimensionar um controle rótulo para ajustar seu conteúdo
ms.date: 03/30/2017
helpviewer_keywords:
- captions [Windows Forms], sizing
- sizing controls
- size [Windows Forms], controls
- labels [Windows Forms], sizing to fit contents
- Label control [Windows Forms], sizing to fit contents
ms.assetid: 99648964-63b2-438c-980e-d24103ad602b
ms.openlocfilehash: 6a563693feaa5074f5d13f0b82cc4d0305a79c23
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743780"
---
# <a name="how-to-size-a-windows-forms-label-control-to-fit-its-contents"></a>Como dimensionar um controle de rótulo dos Windows Forms para encaixar o conteúdo
O controle de <xref:System.Windows.Forms.Label> de Windows Forms pode ser de linha única ou de várias linhas e pode ser corrigido em tamanho ou pode ser redimensionado automaticamente para acomodar sua legenda. A propriedade <xref:System.Windows.Forms.Label.AutoSize%2A> ajuda a dimensionar os controles para se ajustar a legendas maiores ou menores, o que é particularmente útil se a legenda for alterada em tempo de execução.  
  
### <a name="to-make-a-label-control-resize-dynamically-to-fit-its-contents"></a>Para fazer com que um controle de rótulo redimensione dinamicamente para se ajustar ao seu conteúdo  
  
1. Defina sua propriedade <xref:System.Windows.Forms.Label.AutoSize%2A> como `true`.  
  
 Se <xref:System.Windows.Forms.Label.AutoSize%2A> for definido como `false`, as palavras especificadas na propriedade <xref:System.Windows.Forms.Label.Text%2A> serão encapsuladas na próxima linha, se possível, mas o controle não será aumentado.  
  
## <a name="see-also"></a>Veja também

- [Como criar teclas de acesso com controles de rótulo dos Windows Forms](how-to-create-access-keys-with-windows-forms-label-controls.md)
- [Visão geral do controle Label](label-control-overview-windows-forms.md)
- [Controle de rótulo](label-control-windows-forms.md)
