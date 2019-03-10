---
title: Visão geral do controle CheckBox (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- CheckBox
helpviewer_keywords:
- CheckBox control [Windows Forms], about CheckBox control
- data binding [Windows Forms], checkbox controls
- check boxes [Windows Forms], about check boxes
ms.assetid: 085a4e0b-9046-473f-b141-d0edddfb2ebb
ms.openlocfilehash: 003e57db16c35b519d3948fc24e82a94a5c3744d
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57713437"
---
# <a name="checkbox-control-overview-windows-forms"></a>Visão geral do controle CheckBox (Windows Forms)
Os formulários do Windows <xref:System.Windows.Forms.CheckBox> controle indica se uma determinada condição é ativada ou desativada. É usado normalmente para apresentar uma seleção Sim/Não ou Verdadeiro/Falso ao usuário. Use os controles de caixa de seleção em grupos para exibir múltiplas opções entre as quais o usuário pode escolher uma ou mais.  
  
 O controle de caixa de seleção é similar ao controle de botão de opção, ambos são usados para indicar uma seleção feita pelo usuário. A diferença é que apenas um botão de opção em um grupo pode ser selecionado de cada vez. Entretanto, com o controle de caixa de seleção é possível selecionar várias caixas de seleção.  
  
 Uma caixa de seleção pode se conectar aos elementos de um banco de dados usando associação de dados simples. Várias caixas de seleção podem ser agrupadas usando o <xref:System.Windows.Forms.GroupBox> controle. Isso é útil para a aparência visual e também para o design de interface do usuário, uma vez que os controles agrupados podem ser movidos juntos no designer de formulários. Para mais informações, consulte [Associação de dados do Windows Forms](../windows-forms-data-binding.md) e [Controle do GroupBox](groupbox-control-windows-forms.md).  
  
 O <xref:System.Windows.Forms.CheckBox> controle tem duas propriedades importantes, <xref:System.Windows.Forms.CheckBox.Checked%2A> e <xref:System.Windows.Forms.CheckBox.CheckState%2A>. O <xref:System.Windows.Forms.CheckBox.Checked%2A> propriedade retorna um `true` ou `false`. O <xref:System.Windows.Forms.CheckBox.CheckState%2A> propriedade retorna um <xref:System.Windows.Forms.CheckState.Checked> ou <xref:System.Windows.Forms.CheckState.Unchecked>; ou, se o <xref:System.Windows.Forms.CheckBox.ThreeState%2A> estiver definida como `true`, <xref:System.Windows.Forms.CheckBox.CheckState%2A> também podem retornar <xref:System.Windows.Forms.CheckState.Indeterminate>. No estado indeterminado, a caixa é mostrada com uma aparência esmaecida para indicar que a opção não está disponível.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.CheckBox>
- [Como: Definir opções com controles CheckBox dos Windows Forms](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [Como: Responder ao Windows Forms cliques no CheckBox](how-to-respond-to-windows-forms-checkbox-clicks.md)
- [Controle CheckBox](checkbox-control-windows-forms.md)
