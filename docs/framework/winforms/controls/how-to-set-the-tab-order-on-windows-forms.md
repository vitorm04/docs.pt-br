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
ms.openlocfilehash: 50f5f91a946aeebc4d82630b25d18d8f8d2ea4be
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59339899"
---
# <a name="how-to-set-the-tab-order-on-windows-forms"></a>Como: Definir a ordem de tabulação nos Windows Forms
A ordem de tabulação é a ordem em que um usuário move o foco de um controle para outro pressionando a tecla TAB. Cada formulário tem sua própria ordem de tabulação. Por padrão, a ordem de tabulação é igual à ordem em que você criou os controles. A numeração da ordem de tabulação começa com zero.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-set-the-tab-order-of-a-control"></a>Para definir a ordem de tabulação de um controle  
  
1. No menu **Exibir**, clique em **Ordem de Tabulação**.  
  
     Isso ativa o modo de seleção de ordem de tabulação do formulário. Um número (representando o <xref:System.Windows.Forms.Control.TabIndex%2A> propriedade) aparece no canto superior esquerdo de cada controle.  
  
2. Clique nos controles sequencialmente para estabelecer a ordem de tabulação desejada.  
  
    > [!NOTE]
    >  Local do controle na ordem de tabulação pode ser definido como qualquer valor maior ou igual a 0. Quando ocorrem duplicatas, a ordem z dos dois controles é avaliada e o controle na parte superior é tabulado primeiro. (A ordem z consiste na disposição em camadas visuais de controles em um formulário ao longo do eixo z do formulário [profundidade]. A ordem z determina quais controles estão na frente de outros controles.) Para obter mais informações sobre a ordem z, consulte [Colocando objetos em camadas nos Windows Forms](how-to-layer-objects-on-windows-forms.md).  
  
3. Quando você tiver terminado, clique em **Ordem de Tabulação** no menu **Exibir** novamente para sair do modo de ordem de tabulação.  
  
    > [!NOTE]
    >  Controles que não é possível obter o foco, bem como controles desabilitados e invisíveis, não têm um <xref:System.Windows.Forms.Control.TabIndex%2A> propriedade e são não incluídos na ordem de tabulação. Conforme um usuário pressiona a tecla TAB, esses controles são ignorados.  
  
 Como alternativa, a ordem de tabulação pode ser definida na janela Propriedades usando o <xref:System.Windows.Forms.Control.TabIndex%2A> propriedade. O <xref:System.Windows.Forms.Control.TabIndex%2A> propriedade de um controle que determina onde é posicionado na ordem de tabulação. Por padrão, o primeiro controle desenhado tem um <xref:System.Windows.Forms.Control.TabIndex%2A> valor de 0, o segundo tem um <xref:System.Windows.Forms.Control.TabIndex%2A> 1 e assim por diante.  
  
 Além disso, por padrão, uma <xref:System.Windows.Forms.GroupBox> controle tem seu próprio <xref:System.Windows.Forms.Control.TabIndex%2A> valor, que é um número inteiro. Um <xref:System.Windows.Forms.GroupBox> controle em si não pode ter o foco em tempo de execução. Assim, cada controle dentro de um <xref:System.Windows.Forms.GroupBox> tem seu próprio decimal <xref:System.Windows.Forms.Control.TabIndex%2A> valor, começando com.0. Naturalmente, como o <xref:System.Windows.Forms.Control.TabIndex%2A> de um <xref:System.Windows.Forms.GroupBox> controle é incrementado, os controles dentro dele são incrementados de acordo. Se você tiver alterado uma <xref:System.Windows.Forms.Control.TabIndex%2A> valor de 5 a 6, o <xref:System.Windows.Forms.Control.TabIndex%2A> valor do primeiro controle em seu grupo muda automaticamente para 6,0 e assim por diante.  
  
 Por fim, qualquer controle dos muitos no seu formulário podem ser ignorados na ordem de tabulação. Geralmente, pressionar TAB sucessivamente no tempo de execução seleciona cada controle na ordem de tabulação. Desativando o <xref:System.Windows.Forms.Control.TabStop%2A> propriedade, você pode fazer um controle ser transmitida na ordem de tabulação do formulário.  
  
#### <a name="to-remove-a-control-from-the-tab-order"></a>Para remover um controle da ordem de tabulação  
  
1. Defina o controle <xref:System.Windows.Forms.Control.TabStop%2A> propriedade para `false` na janela Propriedades.  
  
     Um controle cuja <xref:System.Windows.Forms.Control.TabStop%2A> propriedade foi definida como `false` ainda mantém sua posição na ordem de tabulação, mesmo que o controle seja ignorado ao percorrer os controles com a tecla TAB.  
  
    > [!NOTE]
    >  Um grupo de botões de opção tem uma única parada de tabulação no tempo de execução. O botão selecionado (ou seja, o botão com sua <xref:System.Windows.Forms.RadioButton.Checked%2A> propriedade definida como `true`) tem seu <xref:System.Windows.Forms.Control.TabStop%2A> propriedade é definida automaticamente como `true`, enquanto os outros botões têm seus <xref:System.Windows.Forms.Control.TabStop%2A> propriedade definida como `false`. Para obter mais informações sobre o agrupamento <xref:System.Windows.Forms.RadioButton> controles, consulte [agrupando controles de RadioButton do Windows Forms para funcionarem como um conjunto](how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md).  
  
## <a name="see-also"></a>Consulte também

- [Controles dos Windows Forms](index.md)
- [Organizando Controles nos Windows Forms](arranging-controls-on-windows-forms.md)
- [Controles a serem usados nos Windows Forms](controls-to-use-on-windows-forms.md)
- [Controles dos Windows Forms por função](windows-forms-controls-by-function.md)
