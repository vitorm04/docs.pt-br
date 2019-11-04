---
title: 'Instruções passo a passo: projetando controles dos Windows Forms com preenchimento, margens e a propriedade AutoSize'
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 76c880c208355b01d0fbaf46cf58091ad147846b
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460605"
---
# <a name="walkthrough-lay-out-controls-with-padding-margins-and-the-autosize-property"></a>Walkthrough: dispor controles com preenchimento, margens e a propriedade AutoSize

O posicionamento exato dos controles no formulário é uma prioridade alta para muitos aplicativos. O **Designer de formulários do Windows** no Visual Studio oferece muitas ferramentas de layout para fazer isso. Três das mais importantes são as propriedades <xref:System.Windows.Forms.Control.Margin%2A>, <xref:System.Windows.Forms.Control.Padding%2A>e <xref:System.Windows.Forms.Control.AutoSize%2A>, que estão presentes em todos os controles de Windows Forms.

A propriedade <xref:System.Windows.Forms.Control.Margin%2A> define o espaço em torno do controle que mantém outros controles uma distância especificada das bordas do controle.

A propriedade <xref:System.Windows.Forms.Control.Padding%2A> define o espaço no interior de um controle que mantém o conteúdo do controle (por exemplo, o valor de sua propriedade <xref:System.Windows.Forms.Control.Text%2A>) uma distância especificada das bordas do controle.

A ilustração a seguir mostra as propriedades <xref:System.Windows.Forms.Control.Padding%2A> e <xref:System.Windows.Forms.Control.Margin%2A> em um controle.

![Preenchimento e margem para controles de Windows Forms](./media/vs-winformpadmargin.gif)

A propriedade <xref:System.Windows.Forms.Control.AutoSize%2A> informa um controle para se dimensionar automaticamente para seu conteúdo. Ele não será redimensionado para ser menor que o valor de sua propriedade de <xref:System.Windows.Forms.Control.Size%2A> original e considerará o valor de sua propriedade <xref:System.Windows.Forms.Control.Padding%2A>.

## <a name="prerequisites"></a>Prerequisites

Você precisará do Visual Studio para concluir este passo a passos.

## <a name="create-the-project"></a>Criar o projeto

1. No Visual Studio, crie um projeto de **aplicativo do Windows** chamado `LayoutExample`.

2. Selecione o formulário no **Designer de Formulários do Windows**.

## <a name="set-margins-for-controls"></a>Definir margens para controles

Você pode definir a distância padrão entre os controles usando a propriedade <xref:System.Windows.Forms.Control.Margin%2A>. Quando você move um controle feche suficiente para um outro controle, você verá uma guia de alinhamento que mostra as margens para os dois controles. O controle que você está movendo também se ajustará à distância definida pelas margens.

### <a name="arrange-controls-on-your-form-using-the-margin-property"></a>Organizar controles no formulário usando a propriedade Margin

1. Arraste dois controles de <xref:System.Windows.Forms.Button> da **caixa de ferramentas** para seu formulário.

2. Selecione um dos controles de <xref:System.Windows.Forms.Button> e mova-o para o outro, até que esteja quase tocando.

   Observe a guia de alinhamento que aparece entre eles. Essa distância é a soma dos valores de <xref:System.Windows.Forms.Control.Margin%2A> de dois controles. O controle que você está movendo se ajusta a essa distância. Para mais detalhes, consulte [Instruções passo a passo: organizando controles nos Windows Forms usando linhas de alinhamento](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).

3. Altere a propriedade <xref:System.Windows.Forms.Control.Margin%2A> de um dos controles expandindo a entrada <xref:System.Windows.Forms.Control.Margin%2A> na janela **Propriedades** e definindo a propriedade <xref:System.Windows.Forms.Padding.All%2A> como **20**.

4. Selecione um dos controles de <xref:System.Windows.Forms.Button> e mova-o para o outro.

   A guia de alinhamento definindo a soma dos valores de margem é maior e o controle se ajusta a uma distância maior de outro controle.

5. Altere a propriedade <xref:System.Windows.Forms.Control.Margin%2A> do controle selecionado expandindo a entrada <xref:System.Windows.Forms.Control.Margin%2A> na janela **Propriedades** e definindo a propriedade <xref:System.Windows.Forms.Padding.Top%2A> como **5**.

6. Mover o controle selecionado abaixo de outro controle e observar que a guia de alinhamento é menor. Mover o controle selecionado para a esquerda de outro controle e observe que a guia de alinhamento retém o valor observado na etapa 4.

7. Você pode definir cada um dos aspectos da propriedade <xref:System.Windows.Forms.Control.Margin%2A>, <xref:System.Windows.Forms.Padding.Left%2A>, <xref:System.Windows.Forms.Padding.Top%2A>, <xref:System.Windows.Forms.Padding.Right%2A>, <xref:System.Windows.Forms.Padding.Bottom%2A>, para valores diferentes ou pode defini-los com o mesmo valor com a propriedade <xref:System.Windows.Forms.Padding.All%2A>.

## <a name="set-padding-for-controls"></a>Definir preenchimento para controles

Para alcançar o layout preciso necessário para seu aplicativo, os controles geralmente contém controles filho. Quando você quiser especificar a proximidade da borda do controle filho para a borda do controle pai, use a propriedade <xref:System.Windows.Forms.Control.Padding%2A> do controle pai em conjunto com a propriedade <xref:System.Windows.Forms.Control.Margin%2A> do controle filho. A propriedade <xref:System.Windows.Forms.Control.Padding%2A> também é usada para controlar a proximidade do conteúdo de um controle (por exemplo, a propriedade <xref:System.Windows.Forms.Control.Text%2A> de um controle de <xref:System.Windows.Forms.Button>) com suas bordas.

### <a name="arrange-controls-on-your-form-using-padding"></a>Organizar controles no formulário usando o preenchimento

1. Arraste um controle de <xref:System.Windows.Forms.Button> da **caixa de ferramentas** para seu formulário.

2. Altere o valor da propriedade <xref:System.Windows.Forms.Control.AutoSize%2A> do controle de <xref:System.Windows.Forms.Button> para **true**.

3. Altere a propriedade <xref:System.Windows.Forms.Control.Padding%2A> expandindo a entrada <xref:System.Windows.Forms.Control.Padding%2A> na janela **Propriedades** e definindo a propriedade <xref:System.Windows.Forms.Padding.All%2A> como **5**.

   O controle se expande para fornecer espaço para o novo preenchimento.

4. Arraste um controle de <xref:System.Windows.Forms.GroupBox> da **caixa de ferramentas** para seu formulário. Arraste um controle de <xref:System.Windows.Forms.Button> da **caixa de ferramentas** para o controle de <xref:System.Windows.Forms.GroupBox>. Posicione o controle de <xref:System.Windows.Forms.Button> para que ele seja liberado com o canto inferior direito do controle de <xref:System.Windows.Forms.GroupBox>.

   Observe as snaplines que aparecem como o controle de <xref:System.Windows.Forms.Button> se aproxima das bordas inferior e direita do controle de <xref:System.Windows.Forms.GroupBox>. Essas snaplines correspondem à propriedade <xref:System.Windows.Forms.Control.Margin%2A> da <xref:System.Windows.Forms.Button>.

5. Altere a propriedade <xref:System.Windows.Forms.Control.Padding%2A> do controle de <xref:System.Windows.Forms.GroupBox> expandindo a entrada <xref:System.Windows.Forms.Control.Padding%2A> na janela **Propriedades** e definindo a propriedade <xref:System.Windows.Forms.Padding.All%2A> como **20**.

6. Selecione o controle de <xref:System.Windows.Forms.Button> dentro do controle de <xref:System.Windows.Forms.GroupBox> e mova-o para o centro do <xref:System.Windows.Forms.GroupBox>.

   As snaplines aparecem em uma distância maior das bordas do controle de <xref:System.Windows.Forms.GroupBox>. Essa distância é a soma da propriedade <xref:System.Windows.Forms.Control.Margin%2A> do controle de <xref:System.Windows.Forms.Button> e da propriedade <xref:System.Windows.Forms.Control.Padding%2A> do controle de <xref:System.Windows.Forms.GroupBox>.

## <a name="size-controls-automatically"></a>Dimensionar controles automaticamente

Em alguns aplicativos, o tamanho de um controle não será o mesmo no momento de execução como era no momento de design. O texto de um controle de <xref:System.Windows.Forms.Button>, por exemplo, pode ser obtido de um banco de dados e seu comprimento não é conhecido com antecedência.

Quando a propriedade <xref:System.Windows.Forms.Control.AutoSize%2A> for definida como `true`, o controle será redimensionado para seu conteúdo. Para obter mais informações, consulte [Visão Geral da Propriedade AutoSize](autosize-property-overview.md).

### <a name="arrange-controls-on-your-form-using-the-autosize-property"></a>Organizar controles no formulário usando a propriedade AutoSize

1. Arraste um controle de <xref:System.Windows.Forms.Button> da **caixa de ferramentas** para seu formulário.

2. Altere o valor da propriedade <xref:System.Windows.Forms.Control.AutoSize%2A> do controle de <xref:System.Windows.Forms.Button> para **true**.

3. Altere a propriedade <xref:System.Windows.Forms.Control.Text%2A> do controle de <xref:System.Windows.Forms.Button> para **esse botão tem uma cadeia de caracteres longa para sua propriedade Text**.

   Quando você confirma a alteração, o controle de <xref:System.Windows.Forms.Button> é redimensionado para se ajustar ao novo texto.

4. Arraste outro controle de <xref:System.Windows.Forms.Button> da **caixa de ferramentas** para seu formulário.

5. Altere a propriedade <xref:System.Windows.Forms.Control.Text%2A> do controle de <xref:System.Windows.Forms.Button> para "**este botão tem uma cadeia de caracteres longa para sua propriedade de texto".**

   Quando você confirma a alteração, o controle de <xref:System.Windows.Forms.Button> não se redimensiona, e o texto é recortado pela borda direita do controle.

6. Altere a propriedade <xref:System.Windows.Forms.Control.Padding%2A> expandindo a entrada <xref:System.Windows.Forms.Control.Padding%2A> na janela **Propriedades** e definindo a propriedade <xref:System.Windows.Forms.Padding.All%2A> como **5**.

   O texto no interior do controle é cortado nos quatro lados.

7. Altere a propriedade <xref:System.Windows.Forms.Control.AutoSize%2A> do controle de <xref:System.Windows.Forms.Button> para **true**.

   O controle de <xref:System.Windows.Forms.Button> se redimensiona para abranger toda a cadeia de caracteres. Além disso, o preenchimento foi adicionado ao texto, fazendo com que o controle de <xref:System.Windows.Forms.Button> se expanda em todas as quatro direções.

8. Arraste um controle de <xref:System.Windows.Forms.Button> da **caixa de ferramentas** para seu formulário. Posicione no canto inferior direito do formulário.

9. Altere o valor da propriedade <xref:System.Windows.Forms.Control.AutoSize%2A> do controle de <xref:System.Windows.Forms.Button> para **true**.

10. Defina a propriedade <xref:System.Windows.Forms.Control.Anchor%2A> do controle de <xref:System.Windows.Forms.Button> como <xref:System.Windows.Forms.AnchorStyles.Right><xref:System.Windows.Forms.AnchorStyles.Bottom>.

11. Altere a propriedade <xref:System.Windows.Forms.Control.Text%2A> do controle de <xref:System.Windows.Forms.Button> para "**este botão tem uma cadeia de caracteres longa para sua propriedade de texto".**

   Quando você confirma a alteração, o controle de <xref:System.Windows.Forms.Button> é redimensionado para a esquerda. Em geral, o dimensionamento automático aumentará o tamanho de um controle na direção oposta à configuração da propriedade <xref:System.Windows.Forms.Control.Anchor%2A>.

## <a name="autosize-and-autosizemode-properties"></a>Propriedades AutoSize e autosizingmode

 Alguns controles oferecem suporte a `AutoSizeMode` propriedade, que lhe dá controle mais refinado sobre o comportamento de dimensionamento automático de um controle.

### <a name="use-the-autosizemode-property"></a>Usar a propriedade autosizingmode

1. Arraste um controle de <xref:System.Windows.Forms.Panel> da **caixa de ferramentas** para seu formulário.

2. Defina o valor da propriedade <xref:System.Windows.Forms.Control.AutoSize%2A> do controle de <xref:System.Windows.Forms.Panel> como **true**.

3. Arraste um controle de <xref:System.Windows.Forms.Button> da **caixa de ferramentas** para o controle de <xref:System.Windows.Forms.Panel>.

4. Coloque o controle de <xref:System.Windows.Forms.Button> próximo ao canto inferior direito do controle de <xref:System.Windows.Forms.Panel>.

5. Selecione o controle de <xref:System.Windows.Forms.Panel> e pegue a alça de dimensionamento na parte inferior direita. Redimensione o controle de <xref:System.Windows.Forms.Panel> para que seja maior e menor.

   > [!NOTE]
   > Você pode redimensionar livremente o controle <xref:System.Windows.Forms.Panel>, mas não pode dimensioná-lo como menor que a posição do canto inferior direito do controle de <xref:System.Windows.Forms.Button>. Esse comportamento é especificado pelo valor padrão da propriedade `AutoSizeMode`, que é <xref:System.Windows.Forms.AutoSizeMode.GrowOnly>.

6. Defina o valor da propriedade `AutoSizeMode` do controle de <xref:System.Windows.Forms.Panel> como <xref:System.Windows.Forms.AutoSizeMode.GrowAndShrink>.

   O <xref:System.Windows.Forms.Panel> controle se ajusta ao redor do controle de <xref:System.Windows.Forms.Button>. Não é possível redimensionar o controle <xref:System.Windows.Forms.Panel>.

7. Arraste o controle de <xref:System.Windows.Forms.Button> para o canto superior esquerdo do controle de <xref:System.Windows.Forms.Panel>.

   O controle de <xref:System.Windows.Forms.Panel> redimensiona para a nova posição do controle de <xref:System.Windows.Forms.Button>.

## <a name="next-steps"></a>Próximas etapas

Há muitos outros recursos de layout para organizar controles em seus aplicativos dos Windows Forms. Aqui estão algumas combinações que você pode tentar:

- Crie um formulário usando um controle de <xref:System.Windows.Forms.TableLayoutPanel>. Para mais detalhes, consulte [Explicação passo a passo: organizando controles nos Windows Forms utilizando um TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md). Tente alterar os valores da propriedade <xref:System.Windows.Forms.Control.Padding%2A> do controle de <xref:System.Windows.Forms.TableLayoutPanel>, bem como a propriedade <xref:System.Windows.Forms.Control.Margin%2A> em seus controles filho.

- Experimente o mesmo experimento usando um controle de <xref:System.Windows.Forms.FlowLayoutPanel>. Para mais detalhes, consulte [Explicação passo a passo: organizando controles nos Windows Forms utilizando um FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md).

- Experimente o encaixe de controles filho em um controle <xref:System.Windows.Forms.Panel>. A propriedade <xref:System.Windows.Forms.Control.Padding%2A> é uma realização mais geral da propriedade <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A>, e você pode se comportar de que esse é o caso colocando um controle filho em um controle de <xref:System.Windows.Forms.Panel> e definindo a propriedade <xref:System.Windows.Forms.Control.Dock%2A> do controle filho como <xref:System.Windows.Forms.DockStyle.Fill>. Defina a propriedade <xref:System.Windows.Forms.Control.Padding%2A> do controle de <xref:System.Windows.Forms.Panel> com vários valores e observe o efeito.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Control.AutoSize%2A>
- <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A>
- <xref:System.Windows.Forms.Control.Margin%2A>
- <xref:System.Windows.Forms.Control.Padding%2A>
- [Visão geral da propriedade AutoSize](autosize-property-overview.md)
- [Passo a passo: organizando controles nos Windows Forms usando um TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Passo a passo: organizando controles nos Windows Forms utilizando um FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Instruções passo a passo: organizando controles no Windows Forms usando guias de alinhamento](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
