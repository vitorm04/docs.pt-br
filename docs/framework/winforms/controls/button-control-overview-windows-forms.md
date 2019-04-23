---
title: Visão geral do controle Button (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- Button
helpviewer_keywords:
- Button control [Windows Forms], about Button control
- buttons [Windows Forms], about buttons
ms.assetid: 255b291b-51a9-4a92-a1a4-2400cd82443f
ms.openlocfilehash: 1ded871fdfab83407d8022ca0c4ce6b2c8a6c67c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59076543"
---
# <a name="button-control-overview-windows-forms"></a>Visão geral do controle Button (Windows Forms)
O controle <xref:System.Windows.Forms.Button> dos Windows Forms permite que o usuário clique nele para realizar uma ação. Quando o botão é clicado, ele se parece como se estivesse sendo empurrado e solto. Sempre que o usuário clica em um botão, o <xref:System.Windows.Forms.Control.Click> manipulador de eventos é invocado. Coloque o código no <xref:System.Windows.Forms.Control.Click> manipulador de eventos para executar qualquer ação que você escolher.  
  
 O texto exibido no botão está contido no <xref:System.Windows.Forms.Control.Text%2A> propriedade. Se o texto exceder a largura do botão, ele será encapsulado para a próxima linha. No entanto, ele será recortado se o controle não puder acomodar sua altura geral. Para obter mais informações, confira [Como: Definir o texto exibido pelo controle de um Windows Forms](how-to-set-the-text-displayed-by-a-windows-forms-control.md). O <xref:System.Windows.Forms.Control.Text%2A> propriedade pode conter uma chave de acesso, que permite que um usuário "clique" no controle pressionando a tecla ALT com a chave de acesso. Para obter detalhes, confira [Como: Criar chaves de acesso para controles do Windows Forms](how-to-create-access-keys-for-windows-forms-controls.md). A aparência do texto é controlada pela <xref:System.Windows.Forms.Control.Font%2A> propriedade e o <xref:System.Windows.Forms.ButtonBase.TextAlign%2A> propriedade.  
  
 O <xref:System.Windows.Forms.Button> controle também pode exibir imagens usando o <xref:System.Windows.Forms.ButtonBase.Image%2A> e <xref:System.Windows.Forms.ButtonBase.ImageList%2A> propriedades. Para obter mais informações, confira [Como: Definir a imagem exibida pelo controle de um Windows Forms](how-to-set-the-image-displayed-by-a-windows-forms-control.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Button>
- [Como: Responder a cliques de botão do Windows Forms](how-to-respond-to-windows-forms-button-clicks.md)
- [Formas de selecionar um controle de botão dos Windows Forms](ways-to-select-a-windows-forms-button-control.md)
- [Como: Designar um botão dos Windows Forms como botão aceitar usando o Designer](designate-a-wf-button-as-the-accept-button-using-the-designer.md)
- [Como: Designar um botão dos Windows Forms como o botão Cancelar usando o Designer](designate-a-wf-button-as-the-cancel-button-using-the-designer.md)
- [Controle de botão](button-control-windows-forms.md)
