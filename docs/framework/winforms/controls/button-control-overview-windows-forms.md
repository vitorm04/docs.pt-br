---
title: Visão geral do controle Button (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- Button
helpviewer_keywords:
- Button control [Windows Forms], about Button control
- buttons [Windows Forms], about buttons
ms.assetid: 255b291b-51a9-4a92-a1a4-2400cd82443f
ms.openlocfilehash: 88255882d3255eff112b9048a906182b64d75084
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="button-control-overview-windows-forms"></a>Visão geral do controle Button (Windows Forms)
O controle <xref:System.Windows.Forms.Button> dos Windows Forms permite que o usuário clique nele para realizar uma ação. Quando o botão é clicado, ele se parece como se estivesse sendo empurrado e solto. Sempre que o usuário clica em um botão, o <xref:System.Windows.Forms.Control.Click> manipulador de eventos é chamado. Coloque o código de <xref:System.Windows.Forms.Control.Click> manipulador de eventos para realizar qualquer ação que você escolher.  
  
 O texto exibido no botão está contido no <xref:System.Windows.Forms.Control.Text%2A> propriedade. Se o texto exceder a largura do botão, ele será encapsulado para a próxima linha. No entanto, ele será recortado se o controle não puder acomodar sua altura geral. Para obter mais informações, consulte [Como definir o texto exibido por um controle dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md). O <xref:System.Windows.Forms.Control.Text%2A> propriedade pode conter uma chave de acesso, que permite que um usuário "clique" do controle pressionando a tecla ALT com a chave de acesso. Para obter mais detalhes, consulte [Como criar chaves de acesso para controles dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md). A aparência do texto é controlada pelo <xref:System.Windows.Forms.Control.Font%2A> propriedade e o <xref:System.Windows.Forms.ButtonBase.TextAlign%2A> propriedade.  
  
 O <xref:System.Windows.Forms.Button> controle também pode exibir imagens usando o <xref:System.Windows.Forms.ButtonBase.Image%2A> e <xref:System.Windows.Forms.ButtonBase.ImageList%2A> propriedades. Para obter mais informações, consulte [Como definir a imagem exibida por um controle dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-image-displayed-by-a-windows-forms-control.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.Button>  
 [Como responder a cliques no botão dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [Formas de selecionar um controle de botão dos Windows Forms](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [Como designar um botão dos Windows Forms como o botão Aceitar usando o Designer](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-accept-button-using-the-designer.md)  
 [Como projetar um botão do Windows Forms como o botão Cancelar usando o Designer](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-cancel-button-using-the-designer.md)  
 [Controle de botão](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
