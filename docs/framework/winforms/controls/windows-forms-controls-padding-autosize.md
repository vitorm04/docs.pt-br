---
title: 'Passo a passo: Definir o layout de controles do Windows Forms com preenchimento, margens e a propriedade AutoSize'
ms.date: 03/30/2017
f1_keywords:
- Margin.Bottom
- Margin.Left
- Margin.Top
- Margin.All
- Margin.Right
helpviewer_keywords:
- Margin property [Windows Forms], walkthroughs
- walkthroughs [Windows Forms], layout
- AutoSize property [Windows Forms], walkthroughs
- Padding property [Windows Forms], walkthroughs
- layout [Windows Forms], margins and padding
- Windows Forms, layout
ms.assetid: f8ae2a6b-db13-4630-8e25-d104091205c7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: daf0c6495b89033e75c27a1ff0cbceaff9d85f34
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987170"
---
# <a name="walkthrough-lay-out-controls-with-padding-margins-and-the-autosize-property"></a>Passo a passo: Dispor controles com preenchimento, margens e a propriedade AutoSize

O posicionamento exato dos controles no formulário é uma prioridade alta para muitos aplicativos. O **Designer de formulários do Windows** no Visual Studio oferece muitas ferramentas de layout para fazer isso. Três das mais importantes são as propriedades <xref:System.Windows.Forms.Control.Margin%2A>, <xref:System.Windows.Forms.Control.Padding%2A>e <xref:System.Windows.Forms.Control.AutoSize%2A> , que estão presentes em todos os controles de Windows Forms.

A <xref:System.Windows.Forms.Control.Margin%2A> propriedade define o espaço em torno do controle que mantém outros controles uma distância especificada das bordas do controle.

A <xref:System.Windows.Forms.Control.Padding%2A> propriedade define o espaço no interior de um controle que mantém o conteúdo do controle (por exemplo, o valor de sua <xref:System.Windows.Forms.Control.Text%2A> Propriedade) uma distância especificada das bordas do controle.

A ilustração a seguir mostra <xref:System.Windows.Forms.Control.Padding%2A> as <xref:System.Windows.Forms.Control.Margin%2A> Propriedades e em um controle.

![Preenchimento e margem para controles de Windows Forms](./media/vs-winformpadmargin.gif)

A <xref:System.Windows.Forms.Control.AutoSize%2A> propriedade informa um controle para se dimensionar automaticamente para seu conteúdo. Ele não será redimensionado para ser menor que o valor de sua <xref:System.Windows.Forms.Control.Size%2A> Propriedade original e considerará o valor de sua <xref:System.Windows.Forms.Control.Padding%2A> propriedade.

## <a name="prerequisites"></a>Pré-requisitos

Você precisará do Visual Studio para concluir este passo a passos.

## <a name="create-the-project"></a>Criar o projeto

1. No Visual Studio, crie um projeto de **aplicativo** do `LayoutExample`Windows chamado.

2. Selecione o formulário no **Designer de Formulários do Windows**.

## <a name="set-margins-for-controls"></a>Definir margens para controles

Você pode definir a distância padrão entre os controles usando a <xref:System.Windows.Forms.Control.Margin%2A> propriedade. Quando você move um controle feche suficiente para um outro controle, você verá uma guia de alinhamento que mostra as margens para os dois controles. O controle que você está movendo também se ajustará à distância definida pelas margens.

### <a name="arrange-controls-on-your-form-using-the-margin-property"></a>Organizar controles no formulário usando a propriedade Margin

1. Arraste dois <xref:System.Windows.Forms.Button> controles da **caixa de ferramentas** para o formulário.

2. Selecione um dos <xref:System.Windows.Forms.Button> controles e mova-o para o outro, até que esteja quase tocando.

   Observe a guia de alinhamento que aparece entre eles. Essa distância é a soma dos <xref:System.Windows.Forms.Control.Margin%2A> valores dos dois controles. O controle que você está movendo se ajusta a essa distância. Para obter detalhes, [consulte Passo a passos: Organizando controles em Windows Forms usando Snaplines](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).

3. Altere a <xref:System.Windows.Forms.Control.Margin%2A> propriedade de um dos controles expandindo a <xref:System.Windows.Forms.Control.Margin%2A> entrada na janela **Propriedades** e definindo a <xref:System.Windows.Forms.Padding.All%2A> Propriedade como **20**.

4. Selecione um dos <xref:System.Windows.Forms.Button> controles e mova-o para o outro.

   A guia de alinhamento definindo a soma dos valores de margem é maior e o controle se ajusta a uma distância maior de outro controle.

5. <xref:System.Windows.Forms.Padding.Top%2A> <xref:System.Windows.Forms.Control.Margin%2A>Altere a PropriedadedocontroleselecionadoexpandindoaentradanajanelaPropriedadesedefinindoapropriedadecomo5.<xref:System.Windows.Forms.Control.Margin%2A>

6. Mover o controle selecionado abaixo de outro controle e observar que a guia de alinhamento é menor. Mover o controle selecionado para a esquerda de outro controle e observe que a guia de alinhamento retém o valor observado na etapa 4.

7. Você pode definir cada <xref:System.Windows.Forms.Control.Margin%2A> um dos aspectos da propriedade <xref:System.Windows.Forms.Padding.Top%2A>, <xref:System.Windows.Forms.Padding.Bottom%2A> <xref:System.Windows.Forms.Padding.Left%2A> <xref:System.Windows.Forms.Padding.Right%2A>,,, para valores diferentes ou pode defini-los com o mesmo valor com a <xref:System.Windows.Forms.Padding.All%2A> propriedade.

## <a name="set-padding-for-controls"></a>Definir preenchimento para controles

Para alcançar o layout preciso necessário para seu aplicativo, os controles geralmente contém controles filho. Quando você quiser especificar a proximidade da borda do controle filho para a borda do controle pai, use a propriedade do <xref:System.Windows.Forms.Control.Padding%2A> controle pai em conjunto com a propriedade do <xref:System.Windows.Forms.Control.Margin%2A> controle filho. A <xref:System.Windows.Forms.Control.Padding%2A> Propriedade também é usada para controlar a proximidade do conteúdo de um controle (por exemplo, a <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Text%2A> propriedade de um controle) para suas bordas.

### <a name="arrange-controls-on-your-form-using-padding"></a>Organizar controles no formulário usando o preenchimento

1. Arraste um <xref:System.Windows.Forms.Button> controle da **caixa de ferramentas** para seu formulário.

2. Altere o valor da <xref:System.Windows.Forms.Button> Propriedade do <xref:System.Windows.Forms.Control.AutoSize%2A> controle para **true**.

3. <xref:System.Windows.Forms.Padding.All%2A> <xref:System.Windows.Forms.Control.Padding%2A>Altere a PropriedadeexpandindoaentradanajanelaPropriedadesedefinindoapropriedadecomo5.<xref:System.Windows.Forms.Control.Padding%2A>

   O controle se expande para fornecer espaço para o novo preenchimento.

4. Arraste um <xref:System.Windows.Forms.GroupBox> controle da **caixa de ferramentas** para seu formulário. Arraste um <xref:System.Windows.Forms.Button> controle da **caixa de ferramentas** para <xref:System.Windows.Forms.GroupBox> o controle. Posicione o <xref:System.Windows.Forms.Button> controle para que ele seja liberado com o canto inferior direito <xref:System.Windows.Forms.GroupBox> do controle.

   Observe as snaplines que aparecem à medida <xref:System.Windows.Forms.Button> que o controle se aproxima das bordas inferior e <xref:System.Windows.Forms.GroupBox> direita do controle. Essas snaplines correspondem à <xref:System.Windows.Forms.Control.Margin%2A> propriedade <xref:System.Windows.Forms.Button>do.

5. <xref:System.Windows.Forms.Control.Padding%2A> <xref:System.Windows.Forms.Padding.All%2A> <xref:System.Windows.Forms.Control.Padding%2A> Altere a propriedade docontrole expandindo a entrada na janela Propriedades e definindo a propriedade como 20. <xref:System.Windows.Forms.GroupBox>

6. Selecione o <xref:System.Windows.Forms.Button> controle dentro do <xref:System.Windows.Forms.GroupBox> controle e mova-o <xref:System.Windows.Forms.GroupBox>para o centro do.

   As snaplines aparecem em uma distância maior das bordas do <xref:System.Windows.Forms.GroupBox> controle. Essa distância <xref:System.Windows.Forms.Button> é a soma da <xref:System.Windows.Forms.Control.Margin%2A> Propriedade do controle e da <xref:System.Windows.Forms.GroupBox> Propriedade do <xref:System.Windows.Forms.Control.Padding%2A> controle.

## <a name="size-controls-automatically"></a>Dimensionar controles automaticamente

Em alguns aplicativos, o tamanho de um controle não será o mesmo no momento de execução como era no momento de design. O texto de um <xref:System.Windows.Forms.Button> controle, por exemplo, pode ser obtido de um banco de dados e seu comprimento não é conhecido com antecedência.

Quando a <xref:System.Windows.Forms.Control.AutoSize%2A> propriedade é definida como `true`, o controle se dimensionará para seu conteúdo. Para obter mais informações, consulte [Visão Geral da Propriedade AutoSize](autosize-property-overview.md).

### <a name="arrange-controls-on-your-form-using-the-autosize-property"></a>Organizar controles no formulário usando a propriedade AutoSize

1. Arraste um <xref:System.Windows.Forms.Button> controle da **caixa de ferramentas** para seu formulário.

2. Altere o valor da <xref:System.Windows.Forms.Button> Propriedade do <xref:System.Windows.Forms.Control.AutoSize%2A> controle para **true**.

3. Altere a <xref:System.Windows.Forms.Button> Propriedade do <xref:System.Windows.Forms.Control.Text%2A> controle para **esse botão tem uma cadeia de caracteres longa para sua propriedade Text**.

   Quando você confirma a alteração, o <xref:System.Windows.Forms.Button> controle é redimensionado para se ajustar ao novo texto.

4. Arraste outro <xref:System.Windows.Forms.Button> controle da **caixa de ferramentas** para o formulário.

5. Altere a <xref:System.Windows.Forms.Button> Propriedade do <xref:System.Windows.Forms.Control.Text%2A> controle para "**este botão tem uma cadeia de caracteres longa para sua propriedade de texto".**

   Quando você confirma a alteração, o <xref:System.Windows.Forms.Button> controle não se redimensiona, e o texto é recortado pela borda direita do controle.

6. <xref:System.Windows.Forms.Padding.All%2A> <xref:System.Windows.Forms.Control.Padding%2A>Altere a PropriedadeexpandindoaentradanajanelaPropriedadesedefinindoapropriedadecomo5.<xref:System.Windows.Forms.Control.Padding%2A>

   O texto no interior do controle é cortado nos quatro lados.

7. Altere a <xref:System.Windows.Forms.Button> Propriedade do <xref:System.Windows.Forms.Control.AutoSize%2A> controle para **true**.

   O <xref:System.Windows.Forms.Button> controle é redimensionado para abranger toda a cadeia de caracteres. Além disso, o preenchimento foi adicionado ao texto, fazendo com <xref:System.Windows.Forms.Button> que o controle se expanda em todas as quatro direções.

8. Arraste um <xref:System.Windows.Forms.Button> controle da **caixa de ferramentas** para seu formulário. Posicione no canto inferior direito do formulário.

9. Altere o valor da <xref:System.Windows.Forms.Button> Propriedade do <xref:System.Windows.Forms.Control.AutoSize%2A> controle para **true**.

10. Defina a <xref:System.Windows.Forms.Button> Propriedade do <xref:System.Windows.Forms.Control.Anchor%2A> controle como <xref:System.Windows.Forms.AnchorStyles.Right>, <xref:System.Windows.Forms.AnchorStyles.Bottom>.

11. Altere a <xref:System.Windows.Forms.Button> Propriedade do <xref:System.Windows.Forms.Control.Text%2A> controle para "**este botão tem uma cadeia de caracteres longa para sua propriedade de texto".**

   Quando você confirma a alteração, o <xref:System.Windows.Forms.Button> controle é redimensionado para a esquerda. Em geral, o dimensionamento automático aumentará o tamanho de um controle na direção oposta <xref:System.Windows.Forms.Control.Anchor%2A> à sua configuração de propriedade.

## <a name="autosize-and-autosizemode-properties"></a>Propriedades AutoSize e autosizingmode

 Alguns controles oferecem suporte a `AutoSizeMode` propriedade, que lhe dá controle mais refinado sobre o comportamento de dimensionamento automático de um controle.

### <a name="use-the-autosizemode-property"></a>Usar a propriedade autosizingmode

1. Arraste um <xref:System.Windows.Forms.Panel> controle da **caixa de ferramentas** para seu formulário.

2. Defina o valor da <xref:System.Windows.Forms.Panel> Propriedade do <xref:System.Windows.Forms.Control.AutoSize%2A> controle como **true**.

3. Arraste um <xref:System.Windows.Forms.Button> controle da **caixa de ferramentas** para <xref:System.Windows.Forms.Panel> o controle.

4. Coloque o <xref:System.Windows.Forms.Button> controle próximo ao canto inferior direito <xref:System.Windows.Forms.Panel> do controle.

5. Selecione o <xref:System.Windows.Forms.Panel> controle e pegue a alça de dimensionamento na parte inferior direita. Redimensione o <xref:System.Windows.Forms.Panel> controle para que seja maior e menor.

   > [!NOTE]
   > Você pode redimensionar livremente <xref:System.Windows.Forms.Panel> o controle, mas não pode dimensioná-lo como menor que <xref:System.Windows.Forms.Button> a posição do canto inferior direito do controle. Esse comportamento é especificado pelo valor padrão da `AutoSizeMode` Propriedade, que é. <xref:System.Windows.Forms.AutoSizeMode.GrowOnly>

6. Defina o valor da <xref:System.Windows.Forms.Panel> Propriedade do `AutoSizeMode` controle como <xref:System.Windows.Forms.AutoSizeMode.GrowAndShrink>.

   O <xref:System.Windows.Forms.Panel> controle se ajusta ao redor do <xref:System.Windows.Forms.Button> controle. Não é possível redimensionar o <xref:System.Windows.Forms.Panel> controle.

7. Arraste o <xref:System.Windows.Forms.Button> controle para o canto superior esquerdo <xref:System.Windows.Forms.Panel> do controle.

   O <xref:System.Windows.Forms.Panel> controle é redimensionado para <xref:System.Windows.Forms.Button> a nova posição do controle.

## <a name="next-steps"></a>Próximas etapas

Há muitos outros recursos de layout para organizar controles em seus aplicativos dos Windows Forms. Aqui estão algumas combinações que você pode tentar:

- Crie um formulário usando um <xref:System.Windows.Forms.TableLayoutPanel> controle. Para obter detalhes, [consulte Passo a passos: Organizando controles em Windows Forms usando um TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md). Tente alterar os valores da <xref:System.Windows.Forms.TableLayoutPanel> <xref:System.Windows.Forms.Control.Padding%2A> Propriedade do controle, bem como a <xref:System.Windows.Forms.Control.Margin%2A> Propriedade em seus controles filho.

- Experimente o mesmo experimento usando um <xref:System.Windows.Forms.FlowLayoutPanel> controle. Para obter detalhes, [consulte Passo a passos: Organizando controles em Windows Forms usando um FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md).

- Experimente o encaixe de controles filho em um <xref:System.Windows.Forms.Panel> controle. A <xref:System.Windows.Forms.Control.Padding%2A> propriedade é uma realização mais geral <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A> da propriedade, e você pode se comportar de que esse é o caso colocando um controle filho em <xref:System.Windows.Forms.Panel> um controle e definindo a propriedade do <xref:System.Windows.Forms.Control.Dock%2A> controle filho como <xref:System.Windows.Forms.DockStyle.Fill>. Defina a <xref:System.Windows.Forms.Panel> Propriedade do <xref:System.Windows.Forms.Control.Padding%2A> controle com vários valores e observe o efeito.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Control.AutoSize%2A>
- <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A>
- <xref:System.Windows.Forms.Control.Margin%2A>
- <xref:System.Windows.Forms.Control.Padding%2A>
- [Visão geral da propriedade AutoSize](autosize-property-overview.md)
- [Passo a passo: Organizando controles em Windows Forms usando um TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Passo a passo: Organizando controles em Windows Forms usando um FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Passo a passo: Organizando controles em Windows Forms usando Snaplines](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
