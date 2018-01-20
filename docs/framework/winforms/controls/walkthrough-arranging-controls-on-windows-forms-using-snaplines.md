---
title: "Instruções passo a passo: organizando controles nos Windows Forms usando linhas de alinhamento"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], arranging with snaplines
- snaplines [Windows Forms], arranging Windows Forms controls
- SnapLine class [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d5c9edc7-cf30-4a97-8ebe-201d569340f8
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bd8bc5e227bd68fc3c5c59d80549322ca742bcf9
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-snaplines"></a>Instruções passo a passo: organizando controles nos Windows Forms usando linhas de alinhamento
O posicionamento exato dos controles no formulário é uma prioridade alta para muitos aplicativos. O Designer de Formulários do Windows fornece várias ferramentas de layout para fazer isso. Uma das mais importantes é a <xref:System.Windows.Forms.Design.Behavior.SnapLine> recurso.  
  
 As guias de alinhamento mostram exatamente onde alinhar os controles com outros controles. Elas também mostram as distâncias recomendadas para as margens entre os controles, conforme é especificado pelas diretrizes da Interface do Usuário do Windows. Para obter detalhes, consulte [User Interface Design and Development](http://go.microsoft.com/FWLink/?LinkId=83878) (Design e desenvolvimento da interface do usuário).  
  
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
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-project"></a>Criando o Projeto  
 A primeira etapa é criar o projeto e configurar o formulário.  
  
#### <a name="to-create-the-project"></a>Para criar o projeto  
  
1.  Crie um projeto de aplicativo baseado no Windows chamado "SnaplineExample". Para obter detalhes, consulte [Como criar um projeto de aplicativo do Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  Selecione o formulário no Designer de Formulários.  
  
## <a name="spacing-and-aligning-controls-using-snaplines"></a>Espaçando e alinhando controles usando guias de alinhamento  
 As guias de alinhamento oferecem uma maneira intuitiva e precisa de alinhar os controles no formulário. Elas aparecem quando você está movendo um controle ou controles selecionados para perto de uma posição que se alinha a outro controle ou conjunto de controles. Sua seleção será "ajustada" para a posição sugerida ao ser movida passando pelos outros controles.  
  
#### <a name="to-arrange-controls-using-snaplines"></a>Para organizar os controles usando guias de alinhamento  
  
1.  Arraste um <xref:System.Windows.Forms.Button> controlar do **caixa de ferramentas** para seu formulário.  
  
2.  Mover o <xref:System.Windows.Forms.Button> controle para o canto inferior direito do formulário. Observe as linhas de ajuste que aparecem como a <xref:System.Windows.Forms.Button> controle se aproximar da parte inferior e direita das bordas do formulário. Essas guias de alinhamento exibem a distância recomendada entre as bordas do controle e o formulário.  
  
3.  Mover o <xref:System.Windows.Forms.Button> controle as bordas do formulário e observe onde as linhas de ajuste são exibidos. Quando tiver terminado, mova o <xref:System.Windows.Forms.Button> controle próximo ao centro do formulário.  
  
4.  Arraste outro <xref:System.Windows.Forms.Button> controlar do **caixa de ferramentas** para seu formulário.  
  
5.  Mover a segunda <xref:System.Windows.Forms.Button> controle até que ele está quase nível com a primeira. Observe a guia de alinhamento que aparece na linha de base de texto de ambos os botões e observe que o controle que você está movendo se ajusta para uma posição nivelada exatamente com o outro controle.  
  
6.  Mover a segunda <xref:System.Windows.Forms.Button> controle até que ele seja posicionado diretamente acima, o primeiro. Observe as guias de alinhamento que aparecem ao longo das bordas esquerda e direita de ambos os botões e observe que o controle que você está movendo se ajusta para uma posição alinhada exatamente com o outro controle.  
  
7.  Selecione uma da <xref:System.Windows.Forms.Button> controla e movê-la perto de outra, até que eles são quase tocar. Observe a guia de alinhamento que aparece entre eles. Essa é a distância recomendada entre as bordas dos controles. Observe também que o controle que você está movendo se encaixa nessa posição.  
  
8.  Arraste dois <xref:System.Windows.Forms.Panel> controla a partir de **caixa de ferramentas** para seu formulário.  
  
9. Mover uma da <xref:System.Windows.Forms.Panel> controla até que ela esteja quase nível com a primeira. Observe as guias de alinhamento que aparecem ao longo das bordas superior e inferior de ambos os controles e observe que o controle que você está movendo se ajusta para uma posição alinhada exatamente com o outro controle.  
  
## <a name="aligning-to-form-and-container-margins"></a>Alinhando às margens do formulário e do contêiner  
 As guias de alinhamento ajudam a alinhar os controles às margens do formulário e do contêiner de uma maneira consistente.  
  
#### <a name="to-align-controls-to-form-and-container-margins"></a>Para alinhar controles às margens do formulário e do contêiner  
  
1.  Selecione uma da <xref:System.Windows.Forms.Button> controla e movê-lo próximo a borda direita do formulário até que um snapline aparece. Distância do guia de alinhamento de borda direita é a soma do controle <xref:System.Windows.Forms.Control.Margin%2A> propriedade e o formulário <xref:System.Windows.Forms.Control.Padding%2A> valores de propriedade.  
  
> [!NOTE]
>  Se o formulário <xref:System.Windows.Forms.Control.Padding%2A> está definida como 0,0,0,0, Designer de formulários do Windows fornece o formulário como um sombreado <xref:System.Windows.Forms.Control.Padding%2A> valor 9,9,9,9. Para substituir esse comportamento, atribua um valor diferente de 0,0,0,0.  
  
1.  Alterar o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Margin%2A> propriedade expandindo o <xref:System.Windows.Forms.Control.Margin%2A> entrada no **propriedades** janela e configuração de <xref:System.Windows.Forms.Padding.All%2A> propriedade como 0. Para obter detalhes, consulte [Instruções passo a passo: projetando controles dos Windows Forms com preenchimento, margens e a propriedade AutoSize](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md).  
  
2.  Mover o <xref:System.Windows.Forms.Button> controle próximo a borda direita do formulário até que um snapline aparece. Essa distância agora é determinada pelo valor no formato <xref:System.Windows.Forms.Control.Padding%2A> propriedade.  
  
3.  Arraste um <xref:System.Windows.Forms.GroupBox> controlar do **caixa de ferramentas** para seu formulário.  
  
4.  Alterar o valor da <xref:System.Windows.Forms.GroupBox> do controle <xref:System.Windows.Forms.Control.Padding%2A> propriedade expandindo o <xref:System.Windows.Forms.Control.Padding%2A> entrada no **propriedades** janela e configuração o <xref:System.Windows.Forms.Padding.All%2A> propriedade como 10.  
  
5.  Arraste um <xref:System.Windows.Forms.Button> de controle do **caixa de ferramentas** para o <xref:System.Windows.Forms.GroupBox> controle.  
  
6.  Mover o <xref:System.Windows.Forms.Button> controle próximo a borda direita do <xref:System.Windows.Forms.GroupBox> controlar até que um snapline aparece. Mover o <xref:System.Windows.Forms.Button> controle dentro de <xref:System.Windows.Forms.GroupBox> controle e observe onde as linhas de ajuste são exibidos.  
  
## <a name="aligning-to-grouped-controls"></a>Alinhando a controles agrupados  
 Você pode usar guias de alinhamento para alinhar controles agrupados, bem como controles dentro de um <xref:System.Windows.Forms.GroupBox> controle.  
  
#### <a name="to-align-to-grouped-controls"></a>Para alinhar controles agrupados  
  
1.  Selecione dois dos controles no formulário. Mova um pouco a seleção e observe as guias de alinhamento que aparecem entre a seleção e os outros controles.  
  
2.  Arraste um <xref:System.Windows.Forms.GroupBox> controlar do **caixa de ferramentas** para seu formulário.  
  
3.  Arraste um <xref:System.Windows.Forms.Button> de controle do **caixa de ferramentas** para o <xref:System.Windows.Forms.GroupBox> controle.  
  
4.  Selecione uma da <xref:System.Windows.Forms.Button> controla e mova-o <xref:System.Windows.Forms.GroupBox> controle. Observe as linhas de ajuste que aparecem nas extremidades do <xref:System.Windows.Forms.GroupBox> controle. Observe também as linhas de ajuste que aparecem nas extremidades do <xref:System.Windows.Forms.Button> controle que contém o <xref:System.Windows.Forms.GroupBox> controle. Os controles que são filhos de uma caixa de controles também dão suporte a guias de alinhamento.  
  
## <a name="using-snaplines-to-place-a-control-by-outlining-its-size"></a>Usando guias de alinhamento para posicionar um controle descrevendo seu tamanho  
 As guias de alinhamento ajudam a alinhar os controles quando você os coloca em um formulário pela primeira vez.  
  
#### <a name="to-use-snaplines-to-place-a-control-by-outlining-its-size"></a>Para usar guias de alinhamento para posicionar um controle descrevendo seu tamanho  
  
1.  No **caixa de ferramentas**, clique no <xref:System.Windows.Forms.Button> ícone do controle. Não o arraste para o formulário.  
  
2.  Mova o ponteiro do mouse sobre a superfície de design do formulário. Observe que o ponteiro mudar para uma cruz com o <xref:System.Windows.Forms.Button> ícone de controle. Observe também as linhas de ajuste que aparecem para sugerir posições alinhadas para a <xref:System.Windows.Forms.Button> controle.  
  
3.  Clique e mantenha o botão do mouse pressionado.  
  
4.  Arraste o ponteiro do mouse sobre o formulário. Observe que uma estrutura de tópicos é desenhada, indicando a posição e o tamanho do controle.  
  
5.  Arraste o ponteiro até que ele se alinhe com o outro controle no formulário. Observe que aparece uma guia de alinhamento para indicar o alinhamento.  
  
6.  Solte o botão do mouse. O controle é criado com a posição e com o tamanho indicados pela estrutura de tópicos.  
  
## <a name="using-snaplines-when-dragging-a-control-from-the-toolbox"></a>Usando guias de alinhamento ao arrastar um controle da caixa de ferramentas  
 As guias de alinhamento ajudam a alinhar os controles quando você os arrasta da **Caixa de ferramentas** para seu formulário.  
  
#### <a name="to-use-snaplines-when-dragging-a-control-from-the-toolbox"></a>Para usar guias de alinhamento ao arrastar um controle da caixa de ferramentas  
  
1.  Arraste um <xref:System.Windows.Forms.Button> controlar do **caixa de ferramentas** para seu formulário, mas não solte o botão do mouse.  
  
2.  Mova o ponteiro do mouse sobre a superfície de design do formulário. Observe que o ponteiro é alterado para indicar a posição na qual o novo <xref:System.Windows.Forms.Button> controle será criado.  
  
3.  Arraste o ponteiro do mouse sobre o formulário. Observe as linhas de ajuste que aparecem para sugerir posições alinhadas para a <xref:System.Windows.Forms.Button> controle. Localize uma posição que esteja alinhada com outros controles.  
  
4.  Solte o botão do mouse. O controle é criado na posição indicada pela guia de alinhamento.  
  
## <a name="resizing-controls-using-snaplines"></a>Redimensionando controles usando guias de alinhamento  
 As guias de alinhamento ajudam a alinhar os controles à medida que você os redimensiona.  
  
#### <a name="to-resize-a-control-using-snaplines"></a>Para redimensionar um controle usando guias de alinhamento  
  
1.  Arraste um <xref:System.Windows.Forms.Button> controlar do **caixa de ferramentas** para seu formulário.  
  
2.  Redimensionar o <xref:System.Windows.Forms.Button> controle captura um canto alças de redimensionamento e arrastando. Para obter detalhes, consulte [Instruções: redimensionar controles nos Windows Forms](../../../../docs/framework/winforms/controls/how-to-resize-controls-on-windows-forms.md).  
  
3.  Arraste a alça de dimensionamento até que uma da <xref:System.Windows.Forms.Button> bordas do controle está alinhado com outro controle. Observe que uma guia de alinhamento aparece. Observe também que a alça de dimensionamento se encaixa na posição indicada pela guia de alinhamento.  
  
4.  Redimensionar o <xref:System.Windows.Forms.Button> controlar em direções diferentes e alinhar a alça de dimensionamento para controles diferentes. Observe como as guias de alinhamento aparecem em várias orientações para indicar o alinhamento.  
  
## <a name="aligning-a-label-to-a-controls-text"></a>Alinhando um rótulo a um texto do controle  
 Alguns controles oferecem uma guia de alinhamento para alinhar outros controles ao texto exibido.  
  
#### <a name="to-align-a-label-to-a-controls-text"></a>Para alinhar um rótulo a um texto do controle  
  
1.  Arraste um <xref:System.Windows.Forms.TextBox> controlar do **caixa de ferramentas** para seu formulário. Quando você solta o <xref:System.Windows.Forms.TextBox> de controle para o formulário, clique no glifo de marca inteligente e selecione o **definir texto TextBox1** opção. Para obter detalhes, consulte [Instruções passo a passo: realizando tarefas comuns usando smart tags em controles dos Windows Forms](../../../../docs/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls.md).  
  
2.  Arraste um <xref:System.Windows.Forms.Label> controlar do **caixa de ferramentas** para seu formulário.  
  
3.  Alterar o valor da <xref:System.Windows.Forms.Label> do controle <xref:System.Windows.Forms.Control.AutoSize%2A> propriedade `true`. Observe que as bordas do controle são ajustadas para se ajustar ao texto de exibição.  
  
4.  Mover o <xref:System.Windows.Forms.Label> controle à esquerda do <xref:System.Windows.Forms.TextBox> controle, para que ele será alinhado com a borda inferior do <xref:System.Windows.Forms.TextBox> controle. Observe a guia de alinhamento que aparece ao longo das bordas inferiores dos dois controles.  
  
5.  Mover o <xref:System.Windows.Forms.Label> controle um pouco para cima, até que o <xref:System.Windows.Forms.Label> texto e o <xref:System.Windows.Forms.TextBox> texto estão alinhadas. Observe a guia de alinhamento com um estilo diferente que aparece, indicando quando os campos de texto de ambos os controles estão alinhados.  
  
## <a name="using-snaplines-with-keyboard-navigation"></a>Usando guias de alinhamento com navegação do teclado  
 As guias de alinhamento ajudam a alinhar os controles ao organizá-los usando as teclas de direção do teclado.  
  
#### <a name="to-use-snaplines-with-keyboard-navigation"></a>Para usar guias de alinhamento com navegação do teclado  
  
1.  Arraste um <xref:System.Windows.Forms.Button> controlar do **caixa de ferramentas** para seu formulário. Coloque-o no canto superior esquerdo do formulário.  
  
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
  
1.  Arraste um <xref:System.Windows.Forms.TableLayoutPanel> controlar do **caixa de ferramentas** para seu formulário.  
  
2.  Clique duas vezes o <xref:System.Windows.Forms.Button> ícone controle no **caixa de ferramentas**. Observe que um novo controle de botão aparece no <xref:System.Windows.Forms.TableLayoutPanel> primeira célula do controle.  
  
3.  Clique duas vezes o <xref:System.Windows.Forms.Button> ícone controle no **caixa de ferramentas** mais duas vezes. Isso deixa uma célula vazia no <xref:System.Windows.Forms.TableLayoutPanel> controle.  
  
4.  Arraste um <xref:System.Windows.Forms.Button> controlar do **caixa de ferramentas** na célula vazia a <xref:System.Windows.Forms.TableLayoutPanel> controle. Observe que não aparece nenhuma guia de alinhamento.  
  
5.  Arraste o <xref:System.Windows.Forms.Button> de controle do <xref:System.Windows.Forms.TableLayoutPanel> controlar e mova-o <xref:System.Windows.Forms.TableLayoutPanel> controle. Observe que as guias de alinhamento aparecem novamente.  
  
## <a name="disabling-snaplines"></a>Desabilitando guias de alinhamento  
 As guias de alinhamento são habilitadas por padrão. Você pode desabilitar as guias de alinhamento seletivamente ou desabilitá-las no ambiente de design.  
  
#### <a name="to-selectively-disable-snaplines"></a>Para desabilitar seletivamente as guias de alinhamento  
  
-   Pressione a tecla ALT enquanto move um controle no formulário.  
  
     Observe que não aparece nenhuma guia de alinhamento e o controle não se ajusta a nenhuma posição de alinhamento possível.  
  
#### <a name="to-disable-snaplines-in-the-design-environment"></a>Para desabilitar as guias de alinhamento no ambiente de design  
  
1.  No menu **Ferramentas**, abra a caixa de diálogo **Opções**. Abra a caixa de diálogo do Designer de Formulários do Windows. Para obter detalhes, consulte [General, Windows Forms Designer, Options Dialog Box](http://msdn.microsoft.com/library/8dd170af-72f0-4212-b04b-034ceee92834) (Designer de Formulários do Windows, caixa de diálogo Opções).  
  
2.  Selecione o nó **Geral**. Na seção **Modo de Layout**, altere a seleção de **SnapLines** para **SnapToGrid**.  
  
3.  Clique em OK para aplicar a configuração.  
  
4.  Selecione um controle no formulário e mova-o em torno dos outros controles. Observe que as guias de alinhamento não aparecem.  
  
## <a name="next-steps"></a>Próximas etapas  
 As guias de alinhamento oferecem uma forma intuitiva de alinhar controles no formulário. Sugestões para exploração adicional incluem:  
  
-   Tente aninhamento um <xref:System.Windows.Forms.GroupBox> controle dentro de outra <xref:System.Windows.Forms.GroupBox> controle. Coloque um <xref:System.Windows.Forms.Button> controle dentro do filho <xref:System.Windows.Forms.GroupBox> controle e outra no pai <xref:System.Windows.Forms.GroupBox> controle. Mover o <xref:System.Windows.Forms.Button> controles para ver como as linhas de ajuste ultrapassam os limites de contêiner.  
  
-   Criar uma coluna de <xref:System.Windows.Forms.TextBox> controles e uma coluna correspondente do <xref:System.Windows.Forms.Label> controles. Defina o valor da <xref:System.Windows.Forms.Label> dos controles <xref:System.Windows.Forms.Control.AutoSize%2A> propriedade `true`. Use guias de alinhamento para mover o <xref:System.Windows.Forms.Label> controla para que seu texto exibido está alinhado com o texto a <xref:System.Windows.Forms.TextBox> controles.  
  
 Para obter informações sobre o design da interface do usuário do Windows, consulte o livro *Microsoft Windows User Experience, Official Guidelines for User Interface Developers and Designers* (Experiência do usuário do Microsoft Windows, diretrizes oficiais para desenvolvedores e designers da interface do usuário) Redmond, WA: Microsoft Press, 1999. (USBN: 0-7356-0566-1).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.Design.Behavior.SnapLine>  
 [Passo a passo: organizando controles nos Windows Forms utilizando um FlowLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [Passo a passo: organizando controles nos Windows Forms usando um TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [Passo a passo: definindo o layout de controles dos Windows Forms com preenchimento, margens e a propriedade AutoSize](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)  
 [Organizando Controles nos Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)
