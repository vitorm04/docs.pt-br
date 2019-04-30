---
title: 'Como: Dimensionar um controle de rótulo do Windows Forms para encaixar o conteúdo'
ms.date: 03/30/2017
helpviewer_keywords:
- captions [Windows Forms], sizing
- sizing controls
- size [Windows Forms], controls
- labels [Windows Forms], sizing to fit contents
- Label control [Windows Forms], sizing to fit contents
ms.assetid: 99648964-63b2-438c-980e-d24103ad602b
ms.openlocfilehash: 110aab0c0826bb4b06e22158afd6af37b5406be4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61971191"
---
# <a name="how-to-size-a-windows-forms-label-control-to-fit-its-contents"></a>Como: Dimensionar um controle de rótulo do Windows Forms para encaixar o conteúdo
Os formulários do Windows <xref:System.Windows.Forms.Label> controle pode ser uma linha ou várias linhas, e podem ser fixas de tamanho ou pode redimensionar automaticamente para acomodar sua legenda. O <xref:System.Windows.Forms.Label.AutoSize%2A> propriedade ajuda você a dimensionar os controles para ajustar as legendas de maiores ou menores, que é particularmente útil se a legenda será alterado em tempo de execução.  
  
### <a name="to-make-a-label-control-resize-dynamically-to-fit-its-contents"></a>Para fazer com que um controle de rótulo redimensionar dinamicamente para ajustar seu conteúdo  
  
1. Defina suas <xref:System.Windows.Forms.Label.AutoSize%2A> propriedade para `true`.  
  
 Se <xref:System.Windows.Forms.Label.AutoSize%2A> é definido como `false`, palavras especificadas no <xref:System.Windows.Forms.Label.Text%2A> propriedade será encapsulado para a próxima linha se possível, mas o controle não crescerá.  
  
## <a name="see-also"></a>Consulte também

- [Como: Criar chaves de acesso com controles de rótulo dos Windows Forms](how-to-create-access-keys-with-windows-forms-label-controls.md)
- [Visão geral do controle Label](label-control-overview-windows-forms.md)
- [Controle de rótulo](label-control-windows-forms.md)
