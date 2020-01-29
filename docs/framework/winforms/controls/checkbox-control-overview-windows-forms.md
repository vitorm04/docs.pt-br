---
title: Visão geral do controle CheckBox
ms.date: 03/30/2017
f1_keywords:
- CheckBox
helpviewer_keywords:
- CheckBox control [Windows Forms], about CheckBox control
- data binding [Windows Forms], checkbox controls
- check boxes [Windows Forms], about check boxes
ms.assetid: 085a4e0b-9046-473f-b141-d0edddfb2ebb
ms.openlocfilehash: b42816cf1bc0ce1ab6db0a2a436b17b0d4370d59
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737101"
---
# <a name="checkbox-control-overview-windows-forms"></a>Visão geral do controle CheckBox (Windows Forms)
O controle de <xref:System.Windows.Forms.CheckBox> de Windows Forms indica se uma determinada condição está ativada ou desativada. É usado normalmente para apresentar uma seleção Sim/Não ou Verdadeiro/Falso ao usuário. Use os controles de caixa de seleção em grupos para exibir múltiplas opções entre as quais o usuário pode escolher uma ou mais.  
  
 O controle de caixa de seleção é similar ao controle de botão de opção, ambos são usados para indicar uma seleção feita pelo usuário. A diferença é que apenas um botão de opção em um grupo pode ser selecionado de cada vez. Entretanto, com o controle de caixa de seleção é possível selecionar várias caixas de seleção.  
  
 Uma caixa de seleção pode se conectar aos elementos de um banco de dados usando associação de dados simples. Várias caixas de seleção podem ser agrupadas usando o controle de <xref:System.Windows.Forms.GroupBox>. Isso é útil para a aparência visual e também para o design de interface do usuário, uma vez que os controles agrupados podem ser movidos juntos no designer de formulários. Para mais informações, consulte [Associação de dados do Windows Forms](../windows-forms-data-binding.md) e [Controle do GroupBox](groupbox-control-windows-forms.md).  
  
 O controle <xref:System.Windows.Forms.CheckBox> tem duas propriedades importantes, <xref:System.Windows.Forms.CheckBox.Checked%2A> e <xref:System.Windows.Forms.CheckBox.CheckState%2A>. A propriedade <xref:System.Windows.Forms.CheckBox.Checked%2A> retorna `true` ou `false`. A propriedade <xref:System.Windows.Forms.CheckBox.CheckState%2A> retorna <xref:System.Windows.Forms.CheckState.Checked> ou <xref:System.Windows.Forms.CheckState.Unchecked>; ou, se a propriedade <xref:System.Windows.Forms.CheckBox.ThreeState%2A> for definida como `true`, <xref:System.Windows.Forms.CheckBox.CheckState%2A> também poderá retornar <xref:System.Windows.Forms.CheckState.Indeterminate>. No estado indeterminado, a caixa é mostrada com uma aparência esmaecida para indicar que a opção não está disponível.  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.CheckBox>
- [Como definir opções com os controles CheckBox dos Windows Forms](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [Como responder a cliques em CheckBox dos Windows Forms](how-to-respond-to-windows-forms-checkbox-clicks.md)
- [Controle CheckBox](checkbox-control-windows-forms.md)
