---
title: Como definir a ordem de tabulação nos Windows Forms
ms.date: 03/30/2017
f1_keywords:
- TabStop
- TabIndex
helpviewer_keywords:
- tab order [Windows Forms], controls on Windows forms
- Windows Forms controls, setting tab order
- controls [Windows Forms], setting tab order
- Windows Forms, setting tab order
ms.assetid: 71fa8e76-0472-414b-ad3c-0f90166e0ad7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 026cff06a8d662cb40107fa76cf6d7989fe30cf1
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458530"
---
# <a name="how-to-set-the-tab-order-on-windows-forms"></a>Como definir a ordem de tabulação em Windows Forms

A ordem de tabulação é a ordem na qual um usuário move o foco de um controle para outro pressionando a tecla Tab. Cada formulário tem sua própria ordem de tabulação. Por padrão, a ordem de tabulação é igual à ordem em que você criou os controles. A numeração da ordem de tabulação começa com zero.

## <a name="to-set-the-tab-order-of-a-control"></a>Para definir a ordem de tabulação de um controle

1. No Visual Studio, no menu **Exibir** , selecione **ordem de tabulação**.

   Isso ativa o modo de seleção de ordem de tabulação do formulário. Um número (representando a propriedade <xref:System.Windows.Forms.Control.TabIndex%2A>) aparece no canto superior esquerdo de cada controle.

2. Clique nos controles sequencialmente para estabelecer a ordem de tabulação desejada.

   > [!NOTE]
   > Local do controle na ordem de tabulação pode ser definido como qualquer valor maior ou igual a 0. Quando ocorrem duplicatas, a ordem z dos dois controles é avaliada e o controle na parte superior é tabulado primeiro. (A ordem z consiste na disposição em camadas visuais de controles em um formulário ao longo do eixo z do formulário [profundidade]. A ordem z determina quais controles estão na frente de outros controles.) Para obter mais informações sobre a ordem z, consulte [camadas de objetos em Windows Forms](how-to-layer-objects-on-windows-forms.md).

3. Quando terminar, selecione a **ordem de tabulação** no menu **Exibir** novamente para sair do modo de ordem de tabulação.

   > [!NOTE]
   > Controles que não podem obter o foco, bem como controles desabilitados e invisíveis, não têm uma propriedade <xref:System.Windows.Forms.Control.TabIndex%2A> e não são incluídos na ordem de tabulação. Como um usuário pressiona a tecla Tab, esses controles são ignorados.

Como alternativa, a ordem de Tabulação pode ser definida no janela Propriedades usando a propriedade <xref:System.Windows.Forms.Control.TabIndex%2A>. A propriedade <xref:System.Windows.Forms.Control.TabIndex%2A> de um controle determina onde ele é posicionado na ordem de tabulação. Por padrão, o primeiro controle desenhado tem um valor de <xref:System.Windows.Forms.Control.TabIndex%2A> de 0, o segundo tem um <xref:System.Windows.Forms.Control.TabIndex%2A> de 1 e assim por diante.

Além disso, por padrão, um controle de <xref:System.Windows.Forms.GroupBox> tem seu próprio valor de <xref:System.Windows.Forms.Control.TabIndex%2A>, que é um número inteiro. Um controle de <xref:System.Windows.Forms.GroupBox> em si não pode ter o foco em tempo de execução. Assim, cada controle dentro de um <xref:System.Windows.Forms.GroupBox> tem seu próprio valor decimal <xref:System.Windows.Forms.Control.TabIndex%2A>, começando com. 0. Naturalmente, como o <xref:System.Windows.Forms.Control.TabIndex%2A> de um controle de <xref:System.Windows.Forms.GroupBox> é incrementado, os controles dentro dele serão incrementados de acordo. Se você alterou um valor de <xref:System.Windows.Forms.Control.TabIndex%2A> de 5 para 6, o valor de <xref:System.Windows.Forms.Control.TabIndex%2A> do primeiro controle em seu grupo será alterado automaticamente para 6,0 e assim por diante.

Por fim, qualquer controle dos muitos no seu formulário podem ser ignorados na ordem de tabulação. Normalmente, pressionar Tab sucessivamente em tempo de execução seleciona cada controle na ordem de tabulação. Desativando a propriedade <xref:System.Windows.Forms.Control.TabStop%2A>, você pode fazer com que um controle seja passado na ordem de tabulação do formulário.

## <a name="to-remove-a-control-from-the-tab-order"></a>Para remover um controle da ordem de tabulação

Defina a propriedade <xref:System.Windows.Forms.Control.TabStop%2A> do controle como **false** na janela **Propriedades** .

Um controle cuja propriedade <xref:System.Windows.Forms.Control.TabStop%2A> foi definida como `false` ainda mantém sua posição na ordem de tabulação, embora o controle seja ignorado quando você percorre os controles com a tecla Tab.

> [!NOTE]
> Um grupo de botões de opção tem uma única parada de tabulação no tempo de execução. O botão selecionado (ou seja, o botão com sua propriedade <xref:System.Windows.Forms.RadioButton.Checked%2A> definida como `true`) tem sua propriedade <xref:System.Windows.Forms.Control.TabStop%2A> definida automaticamente como `true`, enquanto os outros botões têm sua propriedade <xref:System.Windows.Forms.Control.TabStop%2A> definida como `false`. Para obter mais informações sobre como agrupar controles de <xref:System.Windows.Forms.RadioButton>, consulte [grouping Windows Forms controles RadioButton para funcionar como um conjunto](how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md).

## <a name="see-also"></a>Consulte também

- [Controles dos Windows Forms](index.md)
- [Controles a serem usados nos Windows Forms](controls-to-use-on-windows-forms.md)
- [Controles dos Windows Forms por função](windows-forms-controls-by-function.md)
