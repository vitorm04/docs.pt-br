---
title: Visão geral do controle Button (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- Button
helpviewer_keywords:
- Button control [Windows Forms], about Button control
- buttons [Windows Forms], about buttons
ms.assetid: 255b291b-51a9-4a92-a1a4-2400cd82443f
ms.openlocfilehash: 042ff7cb868b62778691348cb6c1ba464b794993
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54656434"
---
# <a name="button-control-overview-windows-forms"></a>Visão geral do controle Button (Windows Forms)
O controle <xref:System.Windows.Forms.Button> dos Windows Forms permite que o usuário clique nele para realizar uma ação. Quando o botão é clicado, ele se parece como se estivesse sendo empurrado e solto. Sempre que o usuário clica em um botão, o <xref:System.Windows.Forms.Control.Click> manipulador de eventos é invocado. Coloque o código no <xref:System.Windows.Forms.Control.Click> manipulador de eventos para executar qualquer ação que você escolher.  
  
 O texto exibido no botão está contido no <xref:System.Windows.Forms.Control.Text%2A> propriedade. Se o texto exceder a largura do botão, ele será encapsulado para a próxima linha. No entanto, ele será recortado se o controle não puder acomodar sua altura geral. Para obter mais informações, confira [Como: Definir o texto exibido pelo controle de um Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md). O <xref:System.Windows.Forms.Control.Text%2A> propriedade pode conter uma chave de acesso, que permite que um usuário "clique" no controle pressionando a tecla ALT com a chave de acesso. Para obter detalhes, consulte [como: Criar chaves de acesso para controles do Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md). A aparência do texto é controlada pela <xref:System.Windows.Forms.Control.Font%2A> propriedade e o <xref:System.Windows.Forms.ButtonBase.TextAlign%2A> propriedade.  
  
 O <xref:System.Windows.Forms.Button> controle também pode exibir imagens usando o <xref:System.Windows.Forms.ButtonBase.Image%2A> e <xref:System.Windows.Forms.ButtonBase.ImageList%2A> propriedades. Para obter mais informações, confira [Como: Definir a imagem exibida pelo controle de um Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-image-displayed-by-a-windows-forms-control.md).  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.Button>
- [Como: Responder a cliques de botão do Windows Forms](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)
- [Formas de selecionar um controle de botão dos Windows Forms](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)
- [Como: Designar um botão dos Windows Forms como botão aceitar usando o Designer](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-accept-button-using-the-designer.md)
- [Como: Designar um botão dos Windows Forms como o botão Cancelar usando o Designer](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-cancel-button-using-the-designer.md)
- [Controle de botão](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
