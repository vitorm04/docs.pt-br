---
title: "Instruções passo a passo: projetando controles dos Windows Forms com preenchimento, margens e a propriedade AutoSize"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2dce58776af84b1f4c733ddce2553e4b18b1b824
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-laying-out-windows-forms-controls-with-padding-margins-and-the-autosize-property"></a>Instruções passo a passo: projetando controles dos Windows Forms com preenchimento, margens e a propriedade AutoSize
O posicionamento exato dos controles no formulário é uma prioridade alta para muitos aplicativos. O **Designer de Formulários do Windows** fornece várias ferramentas de layout para fazer isso. Três das mais importantes são o <xref:System.Windows.Forms.Control.Margin%2A>, <xref:System.Windows.Forms.Control.Padding%2A>, e <xref:System.Windows.Forms.Control.AutoSize%2A> propriedades, que estão presentes em todos os controles de formulários do Windows.  
  
 O <xref:System.Windows.Forms.Control.Margin%2A> propriedade define o espaço ao redor do controle que mantém outros controla uma distância especificada de bordas do controle.  
  
 O <xref:System.Windows.Forms.Control.Padding%2A> propriedade define o espaço no interior de um controle que mantém o conteúdo do controle (por exemplo, o valor de seu <xref:System.Windows.Forms.Control.Text%2A> propriedade) uma distância especificada de bordas do controle.  
  
 A ilustração a seguir mostra o <xref:System.Windows.Forms.Control.Padding%2A> e <xref:System.Windows.Forms.Control.Margin%2A> propriedades em um controle.  
  
 ![Preenchimento e margem para controles dos Windows Forms](../../../../docs/framework/winforms/controls/media/vs-winformpadmargin.gif "VS_WinFormPadMargin")  
  
 O <xref:System.Windows.Forms.Control.AutoSize%2A> propriedade informa um controle redimensionada automaticamente para seu conteúdo. Ele não será redimensionado para ser menor do que o valor de seu original <xref:System.Windows.Forms.Control.Size%2A> propriedade e ele irá considerar o valor de seu <xref:System.Windows.Forms.Control.Padding%2A> propriedade.  
  
 As tarefas ilustradas neste passo a passo incluem:  
  
-   Criação de um projeto dos Windows Forms  
  
-   Configurando margens para seus controles  
  
-   Configurando preenchimento para seus controles  
  
-   Dimensionar automaticamente seus controles  
  
 Ao terminar, você terá um entendimento da função desempenhada por esses importantes recursos de layout.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Para concluir este passo a passo, você precisará de:  
  
-   Permissões suficientes para poder criar e executar projetos de aplicativos dos Windows Forms no computador no qual Visual Studio está instalado.  
  
## <a name="creating-the-project"></a>Criando o Projeto  
 A primeira etapa é criar o projeto e configurar o formulário.  
  
#### <a name="to-create-the-project"></a>Para criar o projeto  
  
1.  Criar um projeto de **aplicativo do Windows** chamado de `LayoutExample`. Para obter mais informações, consulte [Como criar um projeto de aplicativos do Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  Selecione o formulário no **Designer de Formulários do Windows**.  
  
## <a name="setting-margins-for-your-controls"></a>Configurando margens para seus controles  
 Você pode definir a distância padrão entre os controles usando a <xref:System.Windows.Forms.Control.Margin%2A> propriedade. Quando você move um controle feche suficiente para um outro controle, você verá uma guia de alinhamento que mostra as margens para os dois controles. O controle que você está movendo também se ajustará à distância definida pelas margens.  
  
#### <a name="to-arrange-controls-on-your-form-using-the-margin-property"></a>Para organizar os controles no formulário usando a propriedade Margin  
  
1.  Arraste dois <xref:System.Windows.Forms.Button> controla a partir de **caixa de ferramentas** para seu formulário.  
  
2.  Selecione uma da <xref:System.Windows.Forms.Button> controla e movê-la perto de outra, até que eles são quase tocar.  
  
     Observe a guia de alinhamento que aparece entre eles. Essa distância é a soma de dois dos controles <xref:System.Windows.Forms.Control.Margin%2A> valores. O controle que você está movendo se ajusta a essa distância. Para mais detalhes, consulte [Instruções passo a passo: organizando controles nos Windows Forms usando linhas de alinhamento](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).  
  
3.  Alterar o <xref:System.Windows.Forms.Control.Margin%2A> propriedade de um dos controles expandindo o <xref:System.Windows.Forms.Control.Margin%2A> entrada no **propriedades** janela e configuração o <xref:System.Windows.Forms.Padding.All%2A> propriedade para 20.  
  
4.  Selecione uma da <xref:System.Windows.Forms.Button> controla e movê-la perto de outra.  
  
     A guia de alinhamento definindo a soma dos valores de margem é maior e o controle se ajusta a uma distância maior de outro controle.  
  
5.  Alterar o <xref:System.Windows.Forms.Control.Margin%2A> propriedade do controle selecionado expandindo o <xref:System.Windows.Forms.Control.Margin%2A> entrada no **propriedades** janela e configuração o <xref:System.Windows.Forms.Padding.Top%2A> propriedade para 5.  
  
6.  Mover o controle selecionado abaixo de outro controle e observar que a guia de alinhamento é menor. Mover o controle selecionado para a esquerda de outro controle e observe que a guia de alinhamento retém o valor observado na etapa 4.  
  
7.  Você pode definir cada um dos aspectos do <xref:System.Windows.Forms.Control.Margin%2A> propriedade <xref:System.Windows.Forms.Padding.Left%2A>, <xref:System.Windows.Forms.Padding.Top%2A>, <xref:System.Windows.Forms.Padding.Right%2A>, <xref:System.Windows.Forms.Padding.Bottom%2A>, valores diferentes, ou você pode defini-los todos para o mesmo valor com o <xref:System.Windows.Forms.Padding.All%2A> propriedade.  
  
## <a name="setting-padding-for-your-controls"></a>Configurando preenchimento para seus controles  
 Para alcançar o layout preciso necessário para seu aplicativo, os controles geralmente contém controles filho. Quando você deseja especificar a proximidade da borda do controle filho à borda do controle pai, use o controle de pai <xref:System.Windows.Forms.Control.Padding%2A> propriedade em conjunto com o controle de filho <xref:System.Windows.Forms.Control.Margin%2A> propriedade. O <xref:System.Windows.Forms.Control.Padding%2A> propriedade também é usada para controlar a proximidade de conteúdo de um controle (por exemplo, um <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Text%2A> propriedade) para suas bordas.  
  
#### <a name="to-arrange-controls-on-your-form-using-padding"></a>Para organizar os controles no formulário usando preenchimento  
  
1.  Arraste um <xref:System.Windows.Forms.Button> controlar do **caixa de ferramentas** para seu formulário.  
  
2.  Alterar o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.AutoSize%2A> propriedade `true`.  
  
3.  Alterar o <xref:System.Windows.Forms.Control.Padding%2A> propriedade expandindo o <xref:System.Windows.Forms.Control.Padding%2A> entrada no **propriedades** janela e configuração o <xref:System.Windows.Forms.Padding.All%2A> propriedade para 5.  
  
     O controle se expande para fornecer espaço para o novo preenchimento.  
  
4.  Arraste um <xref:System.Windows.Forms.GroupBox> controlar do **caixa de ferramentas** para seu formulário. Arraste um <xref:System.Windows.Forms.Button> de controle do **caixa de ferramentas** para o <xref:System.Windows.Forms.GroupBox> controle. Posição de <xref:System.Windows.Forms.Button> controlar alinhando com o canto inferior direito do <xref:System.Windows.Forms.GroupBox> controle.  
  
     Observe as linhas de ajuste que aparecem como a <xref:System.Windows.Forms.Button> controle se aproximar da parte inferior e direita das bordas do <xref:System.Windows.Forms.GroupBox> controle. Esses guias de alinhamento correspondem ao <xref:System.Windows.Forms.Control.Margin%2A> propriedade o <xref:System.Windows.Forms.Button>.  
  
5.  Alterar o <xref:System.Windows.Forms.GroupBox> do controle <xref:System.Windows.Forms.Control.Padding%2A> propriedade expandindo o <xref:System.Windows.Forms.Control.Padding%2A> entrada no **propriedades** janela e configuração o <xref:System.Windows.Forms.Padding.All%2A> propriedade para 20.  
  
6.  Selecione o <xref:System.Windows.Forms.Button> controle dentro de <xref:System.Windows.Forms.GroupBox> controlar e movê-la para o centro da <xref:System.Windows.Forms.GroupBox>.  
  
     Os guias de alinhamento aparecem em uma distância maior das bordas do <xref:System.Windows.Forms.GroupBox> controle. Essa distância é a soma da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Margin%2A> propriedade e o <xref:System.Windows.Forms.GroupBox> do controle <xref:System.Windows.Forms.Control.Padding%2A> propriedade.  
  
## <a name="automatically-sizing-your-controls"></a>Dimensionar automaticamente seus controles  
 Em alguns aplicativos, o tamanho de um controle não será o mesmo no momento de execução como era no momento de design. O texto de um <xref:System.Windows.Forms.Button> controle, por exemplo, pode ser retirado de um banco de dados e seu comprimento não será conhecido antecipadamente.  
  
 Quando o <xref:System.Windows.Forms.Control.AutoSize%2A> está definida como `true`, o controle será redimensionado automaticamente para o seu conteúdo. Para obter mais informações, consulte [Visão Geral da Propriedade AutoSize](../../../../docs/framework/winforms/controls/autosize-property-overview.md).  
  
#### <a name="to-arrange-controls-on-your-form-using-the-autosize-property"></a>Para organizar os controles no formulário usando a propriedade AutoSize  
  
1.  Arraste um <xref:System.Windows.Forms.Button> controlar do **caixa de ferramentas** para seu formulário.  
  
2.  Alterar o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.AutoSize%2A> propriedade `true`.  
  
3.  Alterar o <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Text%2A> propriedade como "**este botão tem uma cadeia de caracteres longa para a propriedade Text**."  
  
     Ao confirmar a alteração, o <xref:System.Windows.Forms.Button> controle é redimensionado para ajustar o novo texto.  
  
4.  Arraste outro <xref:System.Windows.Forms.Button> controlar do **caixa de ferramentas** para seu formulário.  
  
5.  Alterar o <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Text%2A> propriedade como "**este botão tem uma cadeia de caracteres longa para a propriedade Text.**"  
  
     Ao confirmar a alteração, o <xref:System.Windows.Forms.Button> controle redimensiona e o texto é recortado, a borda direita do controle.  
  
6.  Alterar o <xref:System.Windows.Forms.Control.Padding%2A> propriedade expandindo o <xref:System.Windows.Forms.Control.Padding%2A> entrada no **propriedades** janela e configuração o <xref:System.Windows.Forms.Padding.All%2A> propriedade para 5.  
  
     O texto no interior do controle é cortado nos quatro lados.  
  
7.  Alterar o <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.AutoSize%2A> propriedade `true`.  
  
     O <xref:System.Windows.Forms.Button> controle é redimensionado para abranger toda a cadeia de caracteres. Além disso, o preenchimento foi adicionado ao redor do texto, fazendo com que o <xref:System.Windows.Forms.Button> controle expandir em todas as quatro direções.  
  
8.  Arraste um <xref:System.Windows.Forms.Button> controlar do **caixa de ferramentas** para seu formulário. Posicione no canto inferior direito do formulário.  
  
9. Alterar o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.AutoSize%2A> propriedade `true`.  
  
10. Definir o <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Anchor%2A> propriedade <xref:System.Windows.Forms.AnchorStyles.Right>, <xref:System.Windows.Forms.AnchorStyles.Bottom>.  
  
11. Alterar o <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Text%2A> propriedade como "**este botão tem uma cadeia de caracteres longa para a propriedade Text.**"  
  
     Ao confirmar a alteração, o <xref:System.Windows.Forms.Button> controle é redimensionado para a esquerda. Em geral, o dimensionamento automático aumenta o tamanho de um controle na direção oposta seu <xref:System.Windows.Forms.Control.Anchor%2A> configuração de propriedade.  
  
## <a name="autosize-and-autosizemode-properties"></a>Propriedades AutoSize e AutoSizeMode  
 Alguns controles oferecem suporte a `AutoSizeMode` propriedade, que lhe dá controle mais refinado sobre o comportamento de dimensionamento automático de um controle.  
  
#### <a name="to-use-the-autosizemode-property"></a>Para usar a propriedade AutoSizeMode  
  
1.  Arraste um <xref:System.Windows.Forms.Panel> controlar do **caixa de ferramentas** para seu formulário.  
  
2.  Defina o valor da <xref:System.Windows.Forms.Panel> do controle <xref:System.Windows.Forms.Control.AutoSize%2A> propriedade `true`.  
  
3.  Arraste um <xref:System.Windows.Forms.Button> de controle do **caixa de ferramentas** para o <xref:System.Windows.Forms.Panel> controle.  
  
4.  Coloque o <xref:System.Windows.Forms.Button> controle no canto inferior direito do <xref:System.Windows.Forms.Panel> controle.  
  
5.  Selecione o <xref:System.Windows.Forms.Panel> controlar e arraste a alça de dimensionamento inferior direito. Redimensionar o <xref:System.Windows.Forms.Panel> controle maior e menor.  
  
    > [!NOTE]
    >  Você pode redimensionar livremente a <xref:System.Windows.Forms.Panel> controle, mas não dimensioná-lo menor do que a posição do <xref:System.Windows.Forms.Button> canto inferior direito de controle. Esse comportamento é especificado pelo valor padrão de `AutoSizeMode` propriedade, que é <xref:System.Windows.Forms.AutoSizeMode.GrowOnly>.  
  
6.  Defina o valor da <xref:System.Windows.Forms.Panel> do controle `AutoSizeMode` propriedade <xref:System.Windows.Forms.AutoSizeMode.GrowAndShrink>.  
  
     O <xref:System.Windows.Forms.Panel> tamanhos de controle em si, coloque o <xref:System.Windows.Forms.Button> controle. Você não pode redimensionar o <xref:System.Windows.Forms.Panel> controle.  
  
7.  Arraste o <xref:System.Windows.Forms.Button> controle na direção do canto superior esquerdo do <xref:System.Windows.Forms.Panel> controle.  
  
     O <xref:System.Windows.Forms.Panel> controle é redimensionado para o <xref:System.Windows.Forms.Button> nova posição do controle.  
  
## <a name="next-steps"></a>Próximas etapas  
 Há muitos outros recursos de layout para organizar controles em seus aplicativos dos Windows Forms. Aqui estão algumas combinações que você pode tentar:  
  
-   Criar um formulário usando um <xref:System.Windows.Forms.TableLayoutPanel> controle. Para mais detalhes, consulte [Explicação passo a passo: organizando controles nos Windows Forms utilizando um TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md). Tente alterar os valores da <xref:System.Windows.Forms.TableLayoutPanel> do controle <xref:System.Windows.Forms.Control.Padding%2A> propriedade, bem como a <xref:System.Windows.Forms.Control.Margin%2A> propriedade em seus controles filhos.  
  
-   Tente a mesma experiência usando um <xref:System.Windows.Forms.FlowLayoutPanel> controle. Para mais detalhes, consulte [Explicação passo a passo: organizando controles nos Windows Forms utilizando um FlowLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md).  
  
-   Experiência com encaixar controles filho em um <xref:System.Windows.Forms.Panel> controle. O <xref:System.Windows.Forms.Control.Padding%2A> propriedade é uma realização mais geral do <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A> propriedade e você pode atender-por conta própria a que esse é o caso, colocando um controle filho um <xref:System.Windows.Forms.Panel> controle e a configuração do controle filho <xref:System.Windows.Forms.Control.Dock%2A> propriedade <xref:System.Windows.Forms.DockStyle.Fill>. Definir o <xref:System.Windows.Forms.Panel> do controle <xref:System.Windows.Forms.Control.Padding%2A> propriedade para vários valores e observe o efeito.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.Control.AutoSize%2A>  
 <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A>  
 <xref:System.Windows.Forms.Control.Margin%2A>  
 <xref:System.Windows.Forms.Control.Padding%2A>  
 [Visão geral da propriedade AutoSize](../../../../docs/framework/winforms/controls/autosize-property-overview.md)  
 [Passo a passo: organizando controles nos Windows Forms usando um TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [Passo a passo: organizando controles nos Windows Forms utilizando um FlowLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [Passo a passo: organizando controles nos Windows Forms usando linhas de alinhamento](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
