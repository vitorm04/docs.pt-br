---
title: 'Instruções passo a passo: organizando controles nos Windows Forms usando linhas de alinhamento'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], arranging with snaplines
- snaplines [Windows Forms], arranging Windows Forms controls
- SnapLine class [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d5c9edc7-cf30-4a97-8ebe-201d569340f8
ms.openlocfilehash: 170b79f03515ab371f7013c267b28ba85dafd0f5
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44271410"
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-snaplines"></a>Instruções passo a passo: organizando controles nos Windows Forms usando linhas de alinhamento
O posicionamento exato dos controles no formulário é uma prioridade alta para muitos aplicativos. O Designer de Formulários do Windows fornece várias ferramentas de layout para fazer isso. Um dos mais importantes é a <xref:System.Windows.Forms.Design.Behavior.SnapLine> recurso.  
  
 As guias de alinhamento mostram exatamente onde alinhar os controles com outros controles. Elas também mostram as distâncias recomendadas para as margens entre os controles, conforme é especificado pelas diretrizes da Interface do Usuário do Windows. Para obter detalhes, consulte [User Interface Design and Development](https://go.microsoft.com/FWLink/?LinkId=83878) (Design e desenvolvimento da interface do usuário).  
  
 As guias de alinhamento facilitam o alinhamento dos controles para garantir uma aparência e um comportamento claros e profissionais.  
  
 As tarefas ilustradas neste passo a passo incluem:  
  
-   Criação de um projeto dos Windows Forms  
  
-   Espaçando e alinhando controles usando guias de alinhamento  
  
-   Alinhando às margens do formulário e do contêiner  
  
-   Alinhando a controles agrupados  
  
-   Usando guias de alinhamento para posicionar um controle descrevendo seu tamanho  
  
-   Usando guias de alinhamento ao arrastar um controle da caixa de ferramentas  
  
-   Redimensionando controles usando guias de alinhamento  
  
-   Alinhando um rótulo a um texto do controle  
  
-   Usando guias de alinhamento com navegação do teclado  
  
-   Guias de alinhamento e painéis de layout  
  
-   Desabilitando guias de alinhamento  
  
 Ao terminar, você terá um entendimento da função de layout desempenhada pelo recurso de guias de alinhamento.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="creating-the-project"></a>Criando o Projeto  
 A primeira etapa é criar o projeto e configurar o formulário.  
  
#### <a name="to-create-the-project"></a>Para criar o projeto  
  
1.  Criar um projeto de aplicativo baseado no Windows chamado "SnaplineExample" (**arquivo** > **New** > **projeto**  >  **Visual c#** ou **Visual Basic** > **área de trabalho clássica** > **aplicativo de formulários do Windows**).  
  
2.  Selecione o formulário no Designer de Formulários.  
  
## <a name="spacing-and-aligning-controls-using-snaplines"></a>Espaçando e alinhando controles usando guias de alinhamento  
 As guias de alinhamento oferecem uma maneira intuitiva e precisa de alinhar os controles no formulário. Elas aparecem quando você está movendo um controle ou controles selecionados para perto de uma posição que se alinha a outro controle ou conjunto de controles. Sua seleção será "ajustada" para a posição sugerida ao ser movida passando pelos outros controles.  
  
#### <a name="to-arrange-controls-using-snaplines"></a>Para organizar os controles usando guias de alinhamento  
  
1.  Arraste uma <xref:System.Windows.Forms.Button> controlar do **caixa de ferramentas** para seu formulário.  
  
2.  Mover o <xref:System.Windows.Forms.Button> controle para o canto inferior direito do formulário. Observe os guias de alinhamento que aparecem como o <xref:System.Windows.Forms.Button> controle se aproximar as bordas inferior e direita do formulário. Essas guias de alinhamento exibem a distância recomendada entre as bordas do controle e o formulário.  
  
3.  Mover o <xref:System.Windows.Forms.Button> controle ao redor as bordas do formulário e observe onde os guias de alinhamento aparecem. Quando tiver terminado, mova o <xref:System.Windows.Forms.Button> controle perto do centro do formulário.  
  
4.  Arraste outro <xref:System.Windows.Forms.Button> controlar do **caixa de ferramentas** para seu formulário.  
  
5.  Mova a segunda <xref:System.Windows.Forms.Button> controle até que ele esteja quase nível com o primeiro. Observe a guia de alinhamento que aparece na linha de base de texto de ambos os botões e observe que o controle que você está movendo se ajusta para uma posição nivelada exatamente com o outro controle.  
  
6.  Mova a segunda <xref:System.Windows.Forms.Button> controle até que ele está posicionado diretamente acima do primeiro. Observe as guias de alinhamento que aparecem ao longo das bordas esquerda e direita de ambos os botões e observe que o controle que você está movendo se ajusta para uma posição alinhada exatamente com o outro controle.  
  
7.  Selecione uma da <xref:System.Windows.Forms.Button> controla e mova-o perto do outro, até que eles quase encostem. Observe a guia de alinhamento que aparece entre eles. Essa é a distância recomendada entre as bordas dos controles. Observe também que o controle que você está movendo se encaixa nessa posição.  
  
8.  Arraste duas <xref:System.Windows.Forms.Panel> controla a partir de **caixa de ferramentas** para seu formulário.  
  
9. Mova um do <xref:System.Windows.Forms.Panel> controla até que ele esteja quase nível com o primeiro. Observe as guias de alinhamento que aparecem ao longo das bordas superior e inferior de ambos os controles e observe que o controle que você está movendo se ajusta para uma posição alinhada exatamente com o outro controle.  
  
## <a name="aligning-to-form-and-container-margins"></a>Alinhando às margens do formulário e do contêiner  
 As guias de alinhamento ajudam a alinhar os controles às margens do formulário e do contêiner de uma maneira consistente.  
  
#### <a name="to-align-controls-to-form-and-container-margins"></a>Para alinhar controles às margens do formulário e do contêiner  
  
1.  Selecione uma da <xref:System.Windows.Forms.Button> controla e mova-o perto da borda direita do formulário até que apareça um guia de alinhamento. A distância da guia de alinhamento da borda direita é a soma do controle <xref:System.Windows.Forms.Control.Margin%2A> propriedade e o formulário <xref:System.Windows.Forms.Control.Padding%2A> valores de propriedade.  
  
> [!NOTE]
>  Se o formulário <xref:System.Windows.Forms.Control.Padding%2A> estiver definida como 0,0,0,0, o Designer de formulários do Windows fornecerá ao formulário como um sombreado <xref:System.Windows.Forms.Control.Padding%2A> valor 9,9,9,9. Para substituir esse comportamento, atribua um valor diferente de 0,0,0,0.  
  
1.  Alterar o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Margin%2A> propriedade expandindo o <xref:System.Windows.Forms.Control.Margin%2A> entrada no **propriedades** janela e definindo o <xref:System.Windows.Forms.Padding.All%2A> propriedade como 0. Para obter detalhes, consulte [Instruções passo a passo: projetando controles dos Windows Forms com preenchimento, margens e a propriedade AutoSize](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md).  
  
2.  Mover o <xref:System.Windows.Forms.Button> controle perto da borda direita do formulário até que apareça um guia de alinhamento. Essa distância agora é fornecida pelo valor no formato <xref:System.Windows.Forms.Control.Padding%2A> propriedade.  
  
3.  Arraste uma <xref:System.Windows.Forms.GroupBox> controlar do **caixa de ferramentas** para seu formulário.  
  
4.  Altere o valor da <xref:System.Windows.Forms.GroupBox> do controle <xref:System.Windows.Forms.Control.Padding%2A> propriedade expandindo o <xref:System.Windows.Forms.Control.Padding%2A> entrada no **propriedades** janela e configuração o <xref:System.Windows.Forms.Padding.All%2A> propriedade para 10.  
  
5.  Arraste um <xref:System.Windows.Forms.Button> controlar do **caixa de ferramentas** para o <xref:System.Windows.Forms.GroupBox> controle.  
  
6.  Mover o <xref:System.Windows.Forms.Button> controle perto da borda direita do <xref:System.Windows.Forms.GroupBox> controlar até que apareça um guia de alinhamento. Mover o <xref:System.Windows.Forms.Button> controlar dentro a <xref:System.Windows.Forms.GroupBox> controle e observe onde os guias de alinhamento aparecem.  
  
## <a name="aligning-to-grouped-controls"></a>Alinhando a controles agrupados  
 Você pode usar guias de alinhamento para alinhar controles agrupados, bem como controles dentro de um <xref:System.Windows.Forms.GroupBox> controle.  
  
#### <a name="to-align-to-grouped-controls"></a>Para alinhar controles agrupados  
  
1.  Selecione dois dos controles no formulário. Mova um pouco a seleção e observe as guias de alinhamento que aparecem entre a seleção e os outros controles.  
  
2.  Arraste uma <xref:System.Windows.Forms.GroupBox> controlar do **caixa de ferramentas** para seu formulário.  
  
3.  Arraste um <xref:System.Windows.Forms.Button> controlar do **caixa de ferramentas** para o <xref:System.Windows.Forms.GroupBox> controle.  
  
4.  Selecione uma da <xref:System.Windows.Forms.Button> controles e movê-lo a <xref:System.Windows.Forms.GroupBox> controle. Observe os guias de alinhamento que aparecem nas bordas do <xref:System.Windows.Forms.GroupBox> controle. Além disso, observe os guias de alinhamento que aparecem nas bordas do <xref:System.Windows.Forms.Button> controle que está contido pelo <xref:System.Windows.Forms.GroupBox> controle. Os controles que são filhos de uma caixa de controles também dão suporte a guias de alinhamento.  
  
## <a name="using-snaplines-to-place-a-control-by-outlining-its-size"></a>Usando guias de alinhamento para posicionar um controle descrevendo seu tamanho  
 As guias de alinhamento ajudam a alinhar os controles quando você os coloca em um formulário pela primeira vez.  
  
#### <a name="to-use-snaplines-to-place-a-control-by-outlining-its-size"></a>Para usar guias de alinhamento para posicionar um controle descrevendo seu tamanho  
  
1.  No **caixa de ferramentas**, clique no <xref:System.Windows.Forms.Button> ícone do controle. Não o arraste para o formulário.  
  
2.  Mova o ponteiro do mouse sobre a superfície de design do formulário. Observe que o ponteiro muda para uma mira com o <xref:System.Windows.Forms.Button> ícone do controle anexado. Além disso, observe os guias de alinhamento que aparecem para sugerir posições alinhadas para o <xref:System.Windows.Forms.Button> controle.  
  
3.  Clique e mantenha o botão do mouse pressionado.  
  
4.  Arraste o ponteiro do mouse sobre o formulário. Observe que uma estrutura de tópicos é desenhada, indicando a posição e o tamanho do controle.  
  
5.  Arraste o ponteiro até que ele se alinhe com o outro controle no formulário. Observe que aparece uma guia de alinhamento para indicar o alinhamento.  
  
6.  Solte o botão do mouse. O controle é criado com a posição e com o tamanho indicados pela estrutura de tópicos.  
  
## <a name="using-snaplines-when-dragging-a-control-from-the-toolbox"></a>Usando guias de alinhamento ao arrastar um controle da caixa de ferramentas  
 As guias de alinhamento ajudam a alinhar os controles quando você os arrasta da **Caixa de ferramentas** para seu formulário.  
  
#### <a name="to-use-snaplines-when-dragging-a-control-from-the-toolbox"></a>Para usar guias de alinhamento ao arrastar um controle da caixa de ferramentas  
  
1.  Arraste uma <xref:System.Windows.Forms.Button> controlar do **caixa de ferramentas** para seu formulário, mas não solte o botão do mouse.  
  
2.  Mova o ponteiro do mouse sobre a superfície de design do formulário. Observe que o ponteiro muda para indicar a posição na qual o novo <xref:System.Windows.Forms.Button> controle será criado.  
  
3.  Arraste o ponteiro do mouse sobre o formulário. Observe os guias de alinhamento que aparecem para sugerir posições alinhadas para o <xref:System.Windows.Forms.Button> controle. Localize uma posição que esteja alinhada com outros controles.  
  
4.  Solte o botão do mouse. O controle é criado na posição indicada pela guia de alinhamento.  
  
## <a name="resizing-controls-using-snaplines"></a>Redimensionando controles usando guias de alinhamento  
 As guias de alinhamento ajudam a alinhar os controles à medida que você os redimensiona.  
  
#### <a name="to-resize-a-control-using-snaplines"></a>Para redimensionar um controle usando guias de alinhamento  
  
1.  Arraste uma <xref:System.Windows.Forms.Button> controlar do **caixa de ferramentas** para seu formulário.  
  
2.  Redimensionar o <xref:System.Windows.Forms.Button> controle capturando uma das alças de dimensionamento e arrastando o canto. Para obter detalhes, consulte [Instruções: redimensionar controles nos Windows Forms](../../../../docs/framework/winforms/controls/how-to-resize-controls-on-windows-forms.md).  
  
3.  Arraste a alça de dimensionamento até que um do <xref:System.Windows.Forms.Button> bordas do controle é alinhado com outro controle. Observe que uma guia de alinhamento aparece. Observe também que a alça de dimensionamento se encaixa na posição indicada pela guia de alinhamento.  
  
4.  Redimensionar o <xref:System.Windows.Forms.Button> controlar em direções diferentes e alinhe a alça de dimensionamento a diferentes controles. Observe como as guias de alinhamento aparecem em várias orientações para indicar o alinhamento.  
  
## <a name="aligning-a-label-to-a-controls-text"></a>Alinhando um rótulo a um texto do controle  
 Alguns controles oferecem uma guia de alinhamento para alinhar outros controles ao texto exibido.  
  
#### <a name="to-align-a-label-to-a-controls-text"></a>Para alinhar um rótulo a um texto do controle  
  
1.  Arraste uma <xref:System.Windows.Forms.TextBox> controlar do **caixa de ferramentas** para seu formulário. Quando você solta o <xref:System.Windows.Forms.TextBox> controle para o formulário, clique no glifo de marca inteligente e selecione o **definir texto para textBox1** opção. Para obter detalhes, consulte [Instruções passo a passo: realizando tarefas comuns usando smart tags em controles dos Windows Forms](../../../../docs/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls.md).  
  
2.  Arraste uma <xref:System.Windows.Forms.Label> controlar do **caixa de ferramentas** para seu formulário.  
  
3.  Altere o valor da <xref:System.Windows.Forms.Label> do controle <xref:System.Windows.Forms.Control.AutoSize%2A> propriedade `true`. Observe que as bordas do controle são ajustadas para se ajustar ao texto de exibição.  
  
4.  Mover o <xref:System.Windows.Forms.Label> à esquerda do controle do <xref:System.Windows.Forms.TextBox> controlar, para que ele fique alinhado com a borda inferior do <xref:System.Windows.Forms.TextBox> controle. Observe a guia de alinhamento que aparece ao longo das bordas inferiores dos dois controles.  
  
5.  Mover o <xref:System.Windows.Forms.Label> controle um pouco para cima, até que o <xref:System.Windows.Forms.Label> texto e o <xref:System.Windows.Forms.TextBox> texto estão alinhadas. Observe a guia de alinhamento com um estilo diferente que aparece, indicando quando os campos de texto de ambos os controles estão alinhados.  
  
## <a name="using-snaplines-with-keyboard-navigation"></a>Usando guias de alinhamento com navegação do teclado  
 As guias de alinhamento ajudam a alinhar os controles ao organizá-los usando as teclas de direção do teclado.  
  
#### <a name="to-use-snaplines-with-keyboard-navigation"></a>Para usar guias de alinhamento com navegação do teclado  
  
1.  Arraste uma <xref:System.Windows.Forms.Button> controlar do **caixa de ferramentas** para seu formulário. Coloque-o no canto superior esquerdo do formulário.  
  
2.  Pressione CTRL + SETA PARA BAIXO. Observe que o controle se move para baixo no formulário até a primeira posição de alinhamento horizontal disponível.  
  
3.  Pressione CTRL + SETA PARA BAIXO até que o controle atinja a parte inferior do formulário. Observe as posições que ele ocupa conforme se move para baixo no formulário.  
  
4.  Pressione CTRL + SETA PARA DIREITA. Observe que o controle percorre o formulário até a primeira posição de alinhamento vertical disponível.  
  
5.  Pressione CTRL + SETA PARA CIMA até que o controle atinja a lateral do formulário. Observe as posições que ele ocupa conforme se move no formulário.  
  
6.  Mova o controle no formulário com uma combinação de teclas de direção. Observe as posições ocupadas pelo controle e as guias de alinhamento que o acompanham.  
  
7.  Pressione SHIFT + qualquer tecla de seta para redimensionar o <xref:System.Windows.Forms.Button> controle em incrementos de um pixel.  
  
8.  Pressione CTRL + SHIFT + qualquer tecla de seta para redimensionar o <xref:System.Windows.Forms.Button> controle em incrementos de guia de alinhamento.  
  
## <a name="snaplines-and-layout-panels"></a>Guias de alinhamento e painéis de layout  
 As guias de alinhamento são desabilitadas em painéis de layout.  
  
#### <a name="to-selectively-disable-snaplines"></a>Para desabilitar seletivamente as guias de alinhamento  
  
1.  Arraste uma <xref:System.Windows.Forms.TableLayoutPanel> controlar do **caixa de ferramentas** para seu formulário.  
  
2.  Clique duas vezes o <xref:System.Windows.Forms.Button> ícone do controle no **caixa de ferramentas**. Observe que um novo controle de botão aparece no <xref:System.Windows.Forms.TableLayoutPanel> primeira célula do controle.  
  
3.  Clique duas vezes o <xref:System.Windows.Forms.Button> ícone do controle no **caixa de ferramentas** mais duas vezes. Isso deixa uma célula vazia no <xref:System.Windows.Forms.TableLayoutPanel> controle.  
  
4.  Arraste uma <xref:System.Windows.Forms.Button> controlar do **caixa de ferramentas** para a célula vazia do <xref:System.Windows.Forms.TableLayoutPanel> controle. Observe que não aparece nenhuma guia de alinhamento.  
  
5.  Arraste o <xref:System.Windows.Forms.Button> controlar do <xref:System.Windows.Forms.TableLayoutPanel> de controle e movê-lo a <xref:System.Windows.Forms.TableLayoutPanel> controle. Observe que as guias de alinhamento aparecem novamente.  
  
## <a name="disabling-snaplines"></a>Desabilitando guias de alinhamento  
 As guias de alinhamento são habilitadas por padrão. Você pode desabilitar as guias de alinhamento seletivamente ou desabilitá-las no ambiente de design.  
  
#### <a name="to-selectively-disable-snaplines"></a>Para desabilitar seletivamente as guias de alinhamento  
  
-   Pressione a tecla ALT enquanto move um controle no formulário.  
  
     Observe que não aparece nenhuma guia de alinhamento e o controle não se ajusta a nenhuma posição de alinhamento possível.  
  
#### <a name="to-disable-snaplines-in-the-design-environment"></a>Para desabilitar as guias de alinhamento no ambiente de design  
  
1.  No menu **Ferramentas**, abra a caixa de diálogo **Opções**. Abra a caixa de diálogo do Designer de Formulários do Windows. Para obter detalhes, consulte [General, Windows Forms Designer, Options Dialog Box](https://msdn.microsoft.com/library/8dd170af-72f0-4212-b04b-034ceee92834) (Designer de Formulários do Windows, caixa de diálogo Opções).  
  
2.  Selecione o nó **Geral**. Na seção **Modo de Layout**, altere a seleção de **SnapLines** para **SnapToGrid**.  
  
3.  Clique em OK para aplicar a configuração.  
  
4.  Selecione um controle no formulário e mova-o em torno dos outros controles. Observe que as guias de alinhamento não aparecem.  
  
## <a name="next-steps"></a>Próximas etapas  
 As guias de alinhamento oferecem uma forma intuitiva de alinhar controles no formulário. Sugestões para exploração adicional incluem:  
  
-   Experimente o aninhamento de um <xref:System.Windows.Forms.GroupBox> controle dentro de outra <xref:System.Windows.Forms.GroupBox> controle. Coloque um <xref:System.Windows.Forms.Button> controle dentro do filho <xref:System.Windows.Forms.GroupBox> controle e outro dentro do pai <xref:System.Windows.Forms.GroupBox> controle. Mover o <xref:System.Windows.Forms.Button> controles alternativa para ver como os guias de alinhamento cruzam os limites do contêiner.  
  
-   Criar uma coluna de <xref:System.Windows.Forms.TextBox> controles e uma coluna correspondente da <xref:System.Windows.Forms.Label> controles. Defina o valor da <xref:System.Windows.Forms.Label> dos controles <xref:System.Windows.Forms.Control.AutoSize%2A> propriedade `true`. Use guias de alinhamento para mover o <xref:System.Windows.Forms.Label> controla para que o texto exibido alinhado com o texto a <xref:System.Windows.Forms.TextBox> controles.  
  
 Para obter informações sobre o design da interface do usuário do Windows, consulte o livro *Microsoft Windows User Experience, Official Guidelines for User Interface Developers and Designers* (Experiência do usuário do Microsoft Windows, diretrizes oficiais para desenvolvedores e designers da interface do usuário) Redmond, WA: Microsoft Press, 1999. (USBN: 0-7356-0566-1).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.Design.Behavior.SnapLine>  
 [Passo a passo: organizando controles nos Windows Forms utilizando um FlowLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [Passo a passo: organizando controles nos Windows Forms usando um TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [Passo a passo: definindo o layout de controles dos Windows Forms com preenchimento, margens e a propriedade AutoSize](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)  
 [Organizando Controles nos Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)
