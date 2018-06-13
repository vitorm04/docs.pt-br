---
title: Como agrupar controles RadioButton dos Windows Forms para funcionarem como um conjunto
ms.date: 03/30/2017
helpviewer_keywords:
- radio buttons [Windows Forms], grouping
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
- RadioButton control [Windows Forms], grouping
ms.assetid: 58f8fe34-50b7-49d8-a2be-c271be3c6b32
ms.openlocfilehash: cbc6ab410fa2ab9d89255f82863e51aad36f8c18
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33534486"
---
# <a name="how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set"></a>Como agrupar controles RadioButton dos Windows Forms para funcionarem como um conjunto
Windows Forms <xref:System.Windows.Forms.RadioButton> controles são projetados para dar aos usuários uma opção entre dois ou mais configurações, dos quais apenas um pode ser atribuído a um objeto ou um procedimento. Por exemplo, um grupo de <xref:System.Windows.Forms.RadioButton> controles podem exibir uma escolha de operadoras de pacote para um pedido, mas apenas um dos carros será usado. Portanto, apenas um <xref:System.Windows.Forms.RadioButton> por vez pode ser selecionado, mesmo que ele faz parte de um grupo funcional.  
  
 Grupo de botões de opção ao desenhar dentro de um contêiner, como um <xref:System.Windows.Forms.Panel> controle, um <xref:System.Windows.Forms.GroupBox> controle ou um formulário. Todos os botões de opção que forem adicionados diretamente a um formulário se tornam um grupo. Para adicionar grupos separados, você deve inseri-los em painéis ou caixas de grupo. Para obter mais informações sobre painéis ou caixas de grupo, consulte [Visão geral do controle Panel](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md) ou [Visão geral do controle GroupBox](../../../../docs/framework/winforms/controls/groupbox-control-overview-windows-forms.md).  
  
### <a name="to-group-radiobutton-controls-as-a-set-to-function-independently-of-other-sets"></a>Para agrupar controles RadioButton como um conjunto para funcionar independentemente dos outros conjuntos  
  
1.  Arraste um <xref:System.Windows.Forms.GroupBox> ou <xref:System.Windows.Forms.Panel> controlar do **Windows Forms** guia o **caixa de ferramentas** para o formulário.  
  
2.  Desenhar <xref:System.Windows.Forms.RadioButton> controles de <xref:System.Windows.Forms.GroupBox> ou <xref:System.Windows.Forms.Panel> controle.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.RadioButton>  
 [Visão geral do controle RadioButton](../../../../docs/framework/winforms/controls/radiobutton-control-overview-windows-forms.md)  
 [Visão geral do controle Panel](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)  
 [Visão geral do controle GroupBox](../../../../docs/framework/winforms/controls/groupbox-control-overview-windows-forms.md)  
 [Visão geral do controle CheckBox](../../../../docs/framework/winforms/controls/checkbox-control-overview-windows-forms.md)  
 [Controle RadioButton](../../../../docs/framework/winforms/controls/radiobutton-control-windows-forms.md)
