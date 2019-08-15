---
title: 'Como: Definir a ordem de tabulação nos Windows Forms'
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
ms.openlocfilehash: 5559a3a3e4e62ce9e620de23feef3cbfa0ab8f60
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039848"
---
# <a name="how-to-set-the-tab-order-on-windows-forms"></a>Como: Definir a ordem de tabulação nos Windows Forms
A ordem de tabulação é a ordem em que um usuário move o foco de um controle para outro pressionando a tecla TAB. Cada formulário tem sua própria ordem de tabulação. Por padrão, a ordem de tabulação é igual à ordem em que você criou os controles. A numeração da ordem de tabulação começa com zero.

## <a name="to-set-the-tab-order-of-a-control"></a>Para definir a ordem de tabulação de um controle

1. No menu **Exibir**, clique em **Ordem de Tabulação**.

     Isso ativa o modo de seleção de ordem de tabulação do formulário. Um número (representando a <xref:System.Windows.Forms.Control.TabIndex%2A> Propriedade) aparece no canto superior esquerdo de cada controle.

2. Clique nos controles sequencialmente para estabelecer a ordem de tabulação desejada.

    > [!NOTE]
    >  Local do controle na ordem de tabulação pode ser definido como qualquer valor maior ou igual a 0. Quando ocorrem duplicatas, a ordem z dos dois controles é avaliada e o controle na parte superior é tabulado primeiro. (A ordem z consiste na disposição em camadas visuais de controles em um formulário ao longo do eixo z do formulário [profundidade]. A ordem z determina quais controles estão na frente de outros controles.) Para obter mais informações sobre a ordem z, consulte [Colocando objetos em camadas nos Windows Forms](how-to-layer-objects-on-windows-forms.md).

3. Quando você tiver terminado, clique em **Ordem de Tabulação** no menu **Exibir** novamente para sair do modo de ordem de tabulação.

    > [!NOTE]
    >  Controles que não podem obter o foco, bem como controles desabilitados e invisíveis, não têm <xref:System.Windows.Forms.Control.TabIndex%2A> uma propriedade e não são incluídos na ordem de tabulação. Conforme um usuário pressiona a tecla TAB, esses controles são ignorados.

 Como alternativa, a ordem de Tabulação pode ser definida no janela Propriedades <xref:System.Windows.Forms.Control.TabIndex%2A> usando a propriedade. A <xref:System.Windows.Forms.Control.TabIndex%2A> propriedade de um controle determina onde ele é posicionado na ordem de tabulação. Por padrão, o primeiro controle desenhado tem um <xref:System.Windows.Forms.Control.TabIndex%2A> valor de 0, o segundo tem um <xref:System.Windows.Forms.Control.TabIndex%2A> de 1 e assim por diante.

 Além disso, por padrão, <xref:System.Windows.Forms.GroupBox> um controle tem seu <xref:System.Windows.Forms.Control.TabIndex%2A> próprio valor, que é um número inteiro. Um <xref:System.Windows.Forms.GroupBox> controle em si não pode ter o foco em tempo de execução. Assim, cada controle dentro de <xref:System.Windows.Forms.GroupBox> um tem seu próprio <xref:System.Windows.Forms.Control.TabIndex%2A> valor decimal, começando com. 0. Naturalmente, como o <xref:System.Windows.Forms.Control.TabIndex%2A> de um <xref:System.Windows.Forms.GroupBox> controle é incrementado, os controles dentro dele serão incrementados de acordo. Se você tiver alterado <xref:System.Windows.Forms.Control.TabIndex%2A> um valor de 5 para 6, <xref:System.Windows.Forms.Control.TabIndex%2A> o valor do primeiro controle em seu grupo será alterado automaticamente para 6,0 e assim por diante.

 Por fim, qualquer controle dos muitos no seu formulário podem ser ignorados na ordem de tabulação. Geralmente, pressionar TAB sucessivamente no tempo de execução seleciona cada controle na ordem de tabulação. Ao desativar a <xref:System.Windows.Forms.Control.TabStop%2A> Propriedade, você pode fazer com que um controle seja passado na ordem de tabulação do formulário.

## <a name="to-remove-a-control-from-the-tab-order"></a>Para remover um controle da ordem de tabulação

1. Defina a propriedade do <xref:System.Windows.Forms.Control.TabStop%2A> controle como `false` no janela Propriedades.

     Um controle cuja <xref:System.Windows.Forms.Control.TabStop%2A> Propriedade foi definida como `false` ainda mantém sua posição na ordem de tabulação, embora o controle seja ignorado quando você percorre os controles com a tecla Tab.

    > [!NOTE]
    >  Um grupo de botões de opção tem uma única parada de tabulação no tempo de execução. O botão selecionado (ou seja, o botão com sua <xref:System.Windows.Forms.RadioButton.Checked%2A> propriedade definida como `true`) tem sua <xref:System.Windows.Forms.Control.TabStop%2A> propriedade definida automaticamente como `true`, enquanto os outros botões têm sua <xref:System.Windows.Forms.Control.TabStop%2A> propriedade definida como `false`. Para obter mais informações sobre <xref:System.Windows.Forms.RadioButton> como agrupar controles, consulte [agrupando Windows Forms controles RadioButton para funcionar como um conjunto](how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md).

## <a name="see-also"></a>Consulte também

- [Controles dos Windows Forms](index.md)
- [Organizando Controles nos Windows Forms](arranging-controls-on-windows-forms.md)
- [Controles a serem usados nos Windows Forms](controls-to-use-on-windows-forms.md)
- [Controles dos Windows Forms por função](windows-forms-controls-by-function.md)
