---
title: Visão geral do controle Button
ms.date: 03/30/2017
f1_keywords:
- Button
helpviewer_keywords:
- Button control [Windows Forms], about Button control
- buttons [Windows Forms], about buttons
ms.assetid: 255b291b-51a9-4a92-a1a4-2400cd82443f
ms.openlocfilehash: 4ba7b333e5414efb4814d64ce50c55e08b27f859
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747080"
---
# <a name="button-control-overview-windows-forms"></a>Visão geral do controle Button (Windows Forms)
O controle <xref:System.Windows.Forms.Button> dos Windows Forms permite que o usuário clique nele para realizar uma ação. Quando o botão é clicado, ele se parece como se estivesse sendo empurrado e solto. Sempre que o usuário clica em um botão, o manipulador de eventos <xref:System.Windows.Forms.Control.Click> é invocado. Coloque o código no manipulador de eventos <xref:System.Windows.Forms.Control.Click> para executar qualquer ação que você escolher.  
  
 O texto exibido no botão está contido na propriedade <xref:System.Windows.Forms.Control.Text%2A>. Se o texto exceder a largura do botão, ele será encapsulado para a próxima linha. No entanto, ele será recortado se o controle não puder acomodar sua altura geral. Para obter mais informações, consulte [Como definir o texto exibido por um controle dos Windows Forms](how-to-set-the-text-displayed-by-a-windows-forms-control.md). A propriedade <xref:System.Windows.Forms.Control.Text%2A> pode conter uma chave de acesso, que permite que um usuário "clique" no controle pressionando a tecla ALT com a tecla de acesso. Para obter mais detalhes, consulte [Como criar chaves de acesso para controles dos Windows Forms](how-to-create-access-keys-for-windows-forms-controls.md). A aparência do texto é controlada pela propriedade <xref:System.Windows.Forms.Control.Font%2A> e a propriedade <xref:System.Windows.Forms.ButtonBase.TextAlign%2A>.  
  
 O controle de <xref:System.Windows.Forms.Button> também pode exibir imagens usando as propriedades <xref:System.Windows.Forms.ButtonBase.Image%2A> e <xref:System.Windows.Forms.ButtonBase.ImageList%2A>. Para obter mais informações, consulte [Como definir a imagem exibida por um controle dos Windows Forms](how-to-set-the-image-displayed-by-a-windows-forms-control.md).  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.Button>
- [Como responder a cliques no botão dos Windows Forms](how-to-respond-to-windows-forms-button-clicks.md)
- [Formas de selecionar um controle de botão dos Windows Forms](ways-to-select-a-windows-forms-button-control.md)
- [Como designar um botão do Windows Forms como o botão Aceitar usando o Designer](designate-a-wf-button-as-the-accept-button-using-the-designer.md)
- [Como projetar um botão do Windows Forms como o botão Cancelar usando o Designer](designate-a-wf-button-as-the-cancel-button-using-the-designer.md)
- [Controle de botão](button-control-windows-forms.md)
