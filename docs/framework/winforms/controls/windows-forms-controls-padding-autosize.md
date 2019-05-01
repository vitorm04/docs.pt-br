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
ms.openlocfilehash: 230c7cb80ce6b8a29f7334ed0f8d297fd829faf9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62009078"
---
# <a name="walkthrough-laying-out-windows-forms-controls-with-padding-margins-and-the-autosize-property"></a>Passo a passo: Definir o layout de controles do Windows Forms com preenchimento, margens e a propriedade AutoSize
O posicionamento exato dos controles no formulário é uma prioridade alta para muitos aplicativos. O **Designer de Formulários do Windows** fornece várias ferramentas de layout para fazer isso. Três das mais importantes são as <xref:System.Windows.Forms.Control.Margin%2A>, <xref:System.Windows.Forms.Control.Padding%2A>, e <xref:System.Windows.Forms.Control.AutoSize%2A> propriedades, que estão presentes em todos os controles de formulários do Windows.  
  
 O <xref:System.Windows.Forms.Control.Margin%2A> propriedade define o espaço em torno do controle que mantém outros controla uma distância especificada da bordas do controle.  
  
 O <xref:System.Windows.Forms.Control.Padding%2A> propriedade define o espaço no interior de um controle que mantém o conteúdo do controle (por exemplo, o valor de seu <xref:System.Windows.Forms.Control.Text%2A> propriedade) uma distância especificada da bordas do controle.  
  
 A ilustração a seguir mostra a <xref:System.Windows.Forms.Control.Padding%2A> e <xref:System.Windows.Forms.Control.Margin%2A> propriedades em um controle.  
  
 ![Preenchimento e margem para controles dos Windows Forms](./media/vs-winformpadmargin.gif "VS_WinFormPadMargin")  
  
 O <xref:System.Windows.Forms.Control.AutoSize%2A> propriedade informa um controle a ser dimensionado automaticamente ao seu conteúdo. Ele não será redimensionado para ser menor do que o valor de seus originais <xref:System.Windows.Forms.Control.Size%2A> propriedade e ele considerará o valor do seu <xref:System.Windows.Forms.Control.Padding%2A> propriedade.  
  
 As tarefas ilustradas neste passo a passo incluem:  
  
- Criação de um projeto dos Windows Forms  
  
- Configurando margens para seus controles  
  
- Configurando preenchimento para seus controles  
  
- Dimensionar automaticamente seus controles  
  
 Ao terminar, você terá um entendimento da função desempenhada por esses importantes recursos de layout.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Para concluir este passo a passo, você precisará de:  
  
- Permissões suficientes para poder criar e executar projetos de aplicativos dos Windows Forms no computador no qual Visual Studio está instalado.  
  
## <a name="creating-the-project"></a>Criando o Projeto  
 A primeira etapa é criar o projeto e configurar o formulário.  
  
#### <a name="to-create-the-project"></a>Para criar o projeto  
  
1. Criar um projeto de **aplicativo do Windows** chamado de `LayoutExample`. Para obter mais informações, confira [Como: Criar um projeto de aplicativo do Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) .  
  
2. Selecione o formulário no **Designer de Formulários do Windows**.  
  
## <a name="setting-margins-for-your-controls"></a>Configurando margens para seus controles  
 Você pode definir a distância padrão entre os controles usando o <xref:System.Windows.Forms.Control.Margin%2A> propriedade. Quando você move um controle feche suficiente para um outro controle, você verá uma guia de alinhamento que mostra as margens para os dois controles. O controle que você está movendo também se ajustará à distância definida pelas margens.  
  
#### <a name="to-arrange-controls-on-your-form-using-the-margin-property"></a>Para organizar os controles no formulário usando a propriedade Margin  
  
1. Arraste duas <xref:System.Windows.Forms.Button> controla a partir de **caixa de ferramentas** para seu formulário.  
  
2. Selecione uma da <xref:System.Windows.Forms.Button> controla e mova-o perto do outro, até que eles quase encostem.  
  
     Observe a guia de alinhamento que aparece entre eles. Essa distância é a soma dos dois controles <xref:System.Windows.Forms.Control.Margin%2A> valores. O controle que você está movendo se ajusta a essa distância. Para obter detalhes, consulte [passo a passo: Organizando controles nos Windows Forms usando guias de alinhamento](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).  
  
3. Alterar o <xref:System.Windows.Forms.Control.Margin%2A> propriedade de um dos controles expandindo o <xref:System.Windows.Forms.Control.Margin%2A> entrada no **propriedades** janela e configuração o <xref:System.Windows.Forms.Padding.All%2A> 20 à propriedade.  
  
4. Selecione uma da <xref:System.Windows.Forms.Button> controla e mova-o perto do outro.  
  
     A guia de alinhamento definindo a soma dos valores de margem é maior e o controle se ajusta a uma distância maior de outro controle.  
  
5. Alteração a <xref:System.Windows.Forms.Control.Margin%2A> propriedade do controle selecionado expandindo a <xref:System.Windows.Forms.Control.Margin%2A> entrada na **propriedades** janela e definindo o <xref:System.Windows.Forms.Padding.Top%2A> propriedade para 5.  
  
6. Mover o controle selecionado abaixo de outro controle e observar que a guia de alinhamento é menor. Mover o controle selecionado para a esquerda de outro controle e observe que a guia de alinhamento retém o valor observado na etapa 4.  
  
7. Você pode definir cada um dos aspectos do <xref:System.Windows.Forms.Control.Margin%2A> propriedade, <xref:System.Windows.Forms.Padding.Left%2A>, <xref:System.Windows.Forms.Padding.Top%2A>, <xref:System.Windows.Forms.Padding.Right%2A>, <xref:System.Windows.Forms.Padding.Bottom%2A>, para valores diferentes, ou você pode defini-los todos para o mesmo valor com o <xref:System.Windows.Forms.Padding.All%2A> propriedade.  
  
## <a name="setting-padding-for-your-controls"></a>Configurando preenchimento para seus controles  
 Para alcançar o layout preciso necessário para seu aplicativo, os controles geralmente contém controles filho. Quando você deseja especificar a proximidade da borda do controle filho à borda do controle pai, use o controle de pai <xref:System.Windows.Forms.Control.Padding%2A> propriedade em conjunto com o controle de filho <xref:System.Windows.Forms.Control.Margin%2A> propriedade. O <xref:System.Windows.Forms.Control.Padding%2A> propriedade também é usada para controlar a proximidade de conteúdo do controle (por exemplo, um <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Text%2A> propriedade) para suas bordas.  
  
#### <a name="to-arrange-controls-on-your-form-using-padding"></a>Para organizar os controles no formulário usando preenchimento  
  
1. Arraste uma <xref:System.Windows.Forms.Button> controlar do **caixa de ferramentas** para seu formulário.  
  
2. Altere o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.AutoSize%2A> propriedade `true`.  
  
3. Alteração a <xref:System.Windows.Forms.Control.Padding%2A> propriedade expandindo o <xref:System.Windows.Forms.Control.Padding%2A> entrada na **propriedades** janela e definindo o <xref:System.Windows.Forms.Padding.All%2A> propriedade para 5.  
  
     O controle se expande para fornecer espaço para o novo preenchimento.  
  
4. Arraste uma <xref:System.Windows.Forms.GroupBox> controlar do **caixa de ferramentas** para seu formulário. Arraste um <xref:System.Windows.Forms.Button> controlar do **caixa de ferramentas** para o <xref:System.Windows.Forms.GroupBox> controle. Posição de <xref:System.Windows.Forms.Button> controlar alinhando com o canto inferior direito do <xref:System.Windows.Forms.GroupBox> controle.  
  
     Observe os guias de alinhamento que aparecem como o <xref:System.Windows.Forms.Button> controle se aproximar as bordas inferior e direita do <xref:System.Windows.Forms.GroupBox> controle. Essas guias de alinhamento correspondem do <xref:System.Windows.Forms.Control.Margin%2A> propriedade do <xref:System.Windows.Forms.Button>.  
  
5. Alterar o <xref:System.Windows.Forms.GroupBox> do controle <xref:System.Windows.Forms.Control.Padding%2A> propriedade expandindo o <xref:System.Windows.Forms.Control.Padding%2A> entrada no **propriedades** janela e configuração o <xref:System.Windows.Forms.Padding.All%2A> 20 à propriedade.  
  
6. Selecione o <xref:System.Windows.Forms.Button> controlar dentro a <xref:System.Windows.Forms.GroupBox> controlar e movê-la em direção ao centro do <xref:System.Windows.Forms.GroupBox>.  
  
     Os guias de alinhamento aparecem em uma distância maior das bordas do <xref:System.Windows.Forms.GroupBox> controle. Essa distância é a soma do <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Margin%2A> propriedade e o <xref:System.Windows.Forms.GroupBox> do controle <xref:System.Windows.Forms.Control.Padding%2A> propriedade.  
  
## <a name="automatically-sizing-your-controls"></a>Dimensionar automaticamente seus controles  
 Em alguns aplicativos, o tamanho de um controle não será o mesmo no momento de execução como era no momento de design. O texto de um <xref:System.Windows.Forms.Button> controle, por exemplo, pode ser retirado de um banco de dados e seu comprimento não será conhecido de antemão.  
  
 Quando o <xref:System.Windows.Forms.Control.AutoSize%2A> estiver definida como `true`, o controle será dimensionado para seu conteúdo. Para obter mais informações, consulte [Visão Geral da Propriedade AutoSize](autosize-property-overview.md).  
  
#### <a name="to-arrange-controls-on-your-form-using-the-autosize-property"></a>Para organizar os controles no formulário usando a propriedade AutoSize  
  
1. Arraste uma <xref:System.Windows.Forms.Button> controlar do **caixa de ferramentas** para seu formulário.  
  
2. Altere o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.AutoSize%2A> propriedade `true`.  
  
3. Alterar o <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Text%2A> propriedade como "**este botão tem uma cadeia de caracteres longa para sua propriedade Text**."  
  
     Quando você confirma a alteração, o <xref:System.Windows.Forms.Button> controle redimensionado para ajustar o novo texto.  
  
4. Arraste outro <xref:System.Windows.Forms.Button> controlar do **caixa de ferramentas** para seu formulário.  
  
5. Alterar o <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Text%2A> propriedade como "**este botão tem uma cadeia de caracteres longa para sua propriedade Text.**"  
  
     Quando você confirma a alteração, o <xref:System.Windows.Forms.Button> controle não se redimensiona e o texto é recortado na borda direita do controle.  
  
6. Alteração a <xref:System.Windows.Forms.Control.Padding%2A> propriedade expandindo o <xref:System.Windows.Forms.Control.Padding%2A> entrada na **propriedades** janela e definindo o <xref:System.Windows.Forms.Padding.All%2A> propriedade para 5.  
  
     O texto no interior do controle é cortado nos quatro lados.  
  
7. Alterar o <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.AutoSize%2A> propriedade `true`.  
  
     O <xref:System.Windows.Forms.Button> controle se redimensiona para abranger toda a cadeia de caracteres. Além disso, o preenchimento foi adicionado ao redor do texto, fazendo com que o <xref:System.Windows.Forms.Button> controle para expandir em todas as quatro direções.  
  
8. Arraste uma <xref:System.Windows.Forms.Button> controlar do **caixa de ferramentas** para seu formulário. Posicione no canto inferior direito do formulário.  
  
9. Altere o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.AutoSize%2A> propriedade `true`.  
  
10. Defina as <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Anchor%2A> propriedade <xref:System.Windows.Forms.AnchorStyles.Right>, <xref:System.Windows.Forms.AnchorStyles.Bottom>.  
  
11. Alterar o <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Text%2A> propriedade como "**este botão tem uma cadeia de caracteres longa para sua propriedade Text.**"  
  
     Quando você confirma a alteração, o <xref:System.Windows.Forms.Button> controle é redimensionado em direção à esquerda. Em geral, o dimensionamento automático aumentará o tamanho de um controle na direção oposta seu <xref:System.Windows.Forms.Control.Anchor%2A> configuração da propriedade.  
  
## <a name="autosize-and-autosizemode-properties"></a>Propriedades AutoSize e AutoSizeMode  
 Alguns controles oferecem suporte a `AutoSizeMode` propriedade, que lhe dá controle mais refinado sobre o comportamento de dimensionamento automático de um controle.  
  
#### <a name="to-use-the-autosizemode-property"></a>Para usar a propriedade AutoSizeMode  
  
1. Arraste uma <xref:System.Windows.Forms.Panel> controlar do **caixa de ferramentas** para seu formulário.  
  
2. Defina o valor da <xref:System.Windows.Forms.Panel> do controle <xref:System.Windows.Forms.Control.AutoSize%2A> propriedade `true`.  
  
3. Arraste um <xref:System.Windows.Forms.Button> controlar do **caixa de ferramentas** para o <xref:System.Windows.Forms.Panel> controle.  
  
4. Coloque o <xref:System.Windows.Forms.Button> controle canto inferior direito do <xref:System.Windows.Forms.Panel> controle.  
  
5. Selecione o <xref:System.Windows.Forms.Panel> controlar e arraste a alça de dimensionamento inferior direita. Redimensionar o <xref:System.Windows.Forms.Panel> controle a ser maiores e menores.  
  
    > [!NOTE]
    >  Você pode redimensionar livremente o <xref:System.Windows.Forms.Panel> controle, mas você não pode dimensioná-lo menor do que a posição do <xref:System.Windows.Forms.Button> canto inferior direito do controle. Esse comportamento é especificado pelo valor do padrão de `AutoSizeMode` propriedade, que é <xref:System.Windows.Forms.AutoSizeMode.GrowOnly>.  
  
6. Defina o valor da <xref:System.Windows.Forms.Panel> do controle `AutoSizeMode` propriedade <xref:System.Windows.Forms.AutoSizeMode.GrowAndShrink>.  
  
     O <xref:System.Windows.Forms.Panel> tamanhos de controle em si para envolver o <xref:System.Windows.Forms.Button> controle. Você não pode redimensionar o <xref:System.Windows.Forms.Panel> controle.  
  
7. Arraste o <xref:System.Windows.Forms.Button> controle em direção ao canto superior esquerdo do <xref:System.Windows.Forms.Panel> controle.  
  
     O <xref:System.Windows.Forms.Panel> controle é redimensionado para o <xref:System.Windows.Forms.Button> nova posição do controle.  
  
## <a name="next-steps"></a>Próximas etapas  
 Há muitos outros recursos de layout para organizar controles em seus aplicativos dos Windows Forms. Aqui estão algumas combinações que você pode tentar:  
  
- Criar um formulário usando um <xref:System.Windows.Forms.TableLayoutPanel> controle. Para obter detalhes, consulte [passo a passo: Organizando controles nos Windows Forms utilizando um TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md). Tente alterar os valores da <xref:System.Windows.Forms.TableLayoutPanel> do controle <xref:System.Windows.Forms.Control.Padding%2A> propriedade, bem como o <xref:System.Windows.Forms.Control.Margin%2A> propriedade em seus controles filho.  
  
- Experimente o mesmo teste usando um <xref:System.Windows.Forms.FlowLayoutPanel> controle. Para obter detalhes, consulte [passo a passo: Organizando controles nos Windows Forms utilizando um FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md).  
  
- Experimente encaixar controles filho em um <xref:System.Windows.Forms.Panel> controle. O <xref:System.Windows.Forms.Control.Padding%2A> propriedade é uma realização mais geral do <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A> propriedade e você pode atender à você mesmo que esse é o caso, colocando um controle filho um <xref:System.Windows.Forms.Panel> controle e configuração do controle filho <xref:System.Windows.Forms.Control.Dock%2A> propriedade a ser <xref:System.Windows.Forms.DockStyle.Fill>. Defina as <xref:System.Windows.Forms.Panel> do controle <xref:System.Windows.Forms.Control.Padding%2A> propriedade para vários valores e observe o efeito.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Control.AutoSize%2A>
- <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A>
- <xref:System.Windows.Forms.Control.Margin%2A>
- <xref:System.Windows.Forms.Control.Padding%2A>
- [Visão geral da propriedade AutoSize](autosize-property-overview.md)
- [Passo a passo: Organizando controles nos Windows Forms utilizando um TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Passo a passo: Organizando controles nos Windows Forms utilizando um FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Passo a passo: Organizando controles nos formulários do Windows usando guias de alinhamento](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
