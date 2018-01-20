---
title: "Explicação passo a passo: organizando controles no Windows Forms utilizando um FlowLayoutPanel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FlowLayoutPanel control [Windows Forms], walkthroughs
- Windows Forms controls, arranging
- controls [Windows Forms], arranging with FlowLayoutPanel
- layout [Windows Forms], walkthroughs
ms.assetid: a1744323-0316-49c2-992e-ebfc0a976b85
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bb24e6479d60148f21da24ba9f53b6c3a4054e1e
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel"></a>Explicação passo a passo: organizando controles no Windows Forms utilizando um FlowLayoutPanel
Alguns aplicativos exigem um formulário com um layout que se organiza adequadamente à medida que o formulário é redimensionado ou conforme o tamanho do conteúdo é alterado. Quando você precisa de um layout dinâmico e não deseja tratar <xref:System.Windows.Forms.Control.Layout> eventos explicitamente em seu código, considere o uso de um painel de layout.  
  
 O <xref:System.Windows.Forms.FlowLayoutPanel> controle e o <xref:System.Windows.Forms.TableLayoutPanel> controle fornecem maneiras intuitivas para organizar os controles no formulário. Ambos fornecem uma capacidade automática e configurável de controlar as posições relativas dos controles filho contidos neles e ambos oferecem recursos de layout dinâmico em tempo de execução, para que eles possam redimensionar e reposicionar os controles filho conforme as dimensões do formulário pai se alteram. Os painéis de layout podem ser aninhados em painéis de layout, para permitir a realização de interfaces do usuário sofisticadas.  
  
 O <xref:System.Windows.Forms.TableLayoutPanel> organiza seu conteúdo em uma grade, fornecendo funcionalidade semelhante para o HTML \<tabela > elemento. Suas células são organizadas em linhas e colunas, que podem ter diferentes tamanhos. Para obter mais informações, consulte [Passo a passo: organizando controles nos Windows Forms usando um TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).  
  
 O <xref:System.Windows.Forms.FlowLayoutPanel> organiza seu conteúdo em uma direção de fluxo específico: horizontal ou vertical. Seu conteúdo pode ser encapsulado de uma linha à outra ou de uma coluna à próxima. Como alternativa, seu conteúdo pode ser recortado, em vez de encapsulado. As tarefas ilustradas neste passo a passo incluem:  
  
-   Criação de um projeto dos Windows Forms  
  
-   Organizando controles horizontalmente e verticalmente  
  
-   Alterando a direção do fluxo  
  
-   Inserindo quebras de fluxo  
  
-   Organizando controles usando preenchimento e margens  
  
-   Inserindo controles ao clicar duas vezes neles na caixa de ferramentas  
  
-   Inserindo um controle ao desenhar seu contorno  
  
-   Inserindo controles usando o sinal de interpolação  
  
-   Reatribuição de controles existentes a um pai diferente  
  
 Ao terminar, você terá um entendimento da função desempenhada por esses importantes recursos de layout.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-project"></a>Criando o Projeto  
 A primeira etapa é criar o projeto e configurar o formulário.  
  
#### <a name="to-create-the-project"></a>Para criar o projeto  
  
1.  Crie um projeto de aplicativo baseado no Windows chamado "FlowLayoutPanelExample". Para obter mais informações, consulte [Como criar um projeto de aplicativos do Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  Selecione o formulário no **Designer de Formulários**.  
  
## <a name="arranging-controls-horizontally-and-vertically"></a>Organizando controles horizontalmente e verticalmente  
 O <xref:System.Windows.Forms.FlowLayoutPanel> controle permite que você coloque controles ao longo de linhas ou colunas sem exigir que você especificar precisamente a posição de cada controle individualmente.  
  
 O <xref:System.Windows.Forms.FlowLayoutPanel> controle pode redimensionar ou fluir seus controles filhos como as dimensões da alteração do formulário pai.  
  
#### <a name="to-arrange-controls-horizontally-and-vertically-using-a-flowlayoutpanel"></a>Para organizar controles horizontalmente e verticalmente usando um FlowLayoutPanel  
  
1.  Arraste um <xref:System.Windows.Forms.FlowLayoutPanel> controlar do **caixa de ferramentas** para seu formulário.  
  
2.  Arraste um <xref:System.Windows.Forms.Button> de controle do **caixa de ferramentas** para o <xref:System.Windows.Forms.FlowLayoutPanel>. Ele é automaticamente movida para o canto superior esquerdo do <xref:System.Windows.Forms.FlowLayoutPanel> controle.  
  
3.  Arraste outro <xref:System.Windows.Forms.Button> controlar do **caixa de ferramentas** para o <xref:System.Windows.Forms.FlowLayoutPanel>. Observe que o <xref:System.Windows.Forms.Button> controle será movido automaticamente para uma posição ao lado da primeira <xref:System.Windows.Forms.Button> controle. Se seu <xref:System.Windows.Forms.FlowLayoutPanel> é muito estreita para ajustar os dois controles na mesma linha, o novo <xref:System.Windows.Forms.Button> controle será movido automaticamente para a próxima linha.  
  
4.  Arraste vários outros <xref:System.Windows.Forms.Button> controla do **caixa de ferramentas** para o <xref:System.Windows.Forms.FlowLayoutPanel>. Continuar a colocação <xref:System.Windows.Forms.Button> controla até que um é quebrada para a próxima linha.  
  
5.  Alterar o valor da <xref:System.Windows.Forms.FlowLayoutPanel> do controle <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> propriedade `false`. Observe que os controles filho não fluem mais para a próxima linha. Em vez disso, eles são movidos para a primeira linha e recortados.  
  
6.  Alterar o valor da <xref:System.Windows.Forms.FlowLayoutPanel> do controle <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> propriedade `true`. Observe que os controles filho quebram novamente para a próxima linha.  
  
7.  Diminuir a largura do <xref:System.Windows.Forms.FlowLayoutPanel> controle até que todos os <xref:System.Windows.Forms.Button> controles são movidos para a primeira coluna.  
  
8.  Aumente a largura do <xref:System.Windows.Forms.FlowLayoutPanel> controle até que todos os <xref:System.Windows.Forms.Button> controles são movidos para a primeira linha. Você pode precisar redimensionar o formulário para acomodar a largura maior.  
  
## <a name="changing-flow-direction"></a>Alterando a direção do fluxo  
 O <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> propriedade permite que você altere a direção em que os controles são organizados. Você pode organizar os controles filho da esquerda para a direita, da direita para a esquerda, de cima para baixo ou de baixo para cima.  
  
#### <a name="to-change-the-flow-direction-in-a-flowlayoutpanel"></a>Para alterar a direção do fluxo em um FlowLayoutPanel  
  
1.  Alterar o valor da <xref:System.Windows.Forms.FlowLayoutPanel> do controle <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> propriedade <xref:System.Windows.Forms.FlowDirection.TopDown>. Observe que os controles filho são reorganizados em uma ou mais colunas, dependendo da altura do controle.  
  
2.  Redimensionar o <xref:System.Windows.Forms.FlowLayoutPanel> para sua altura for menor do que a coluna de <xref:System.Windows.Forms.Button> controles. Observe que o <xref:System.Windows.Forms.FlowLayoutPanel> reorganiza os controles filho para fluir para a próxima coluna. Continue a diminuir a altura e observe que os controles filho fluem para colunas consecutivas. Alterar o valor da <xref:System.Windows.Forms.FlowLayoutPanel> do controle <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> propriedade <xref:System.Windows.Forms.FlowDirection.RightToLeft>. Observe que as posições dos controles filho são revertidas. Observe o layout, quando você alterar o valor da <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> propriedade <xref:System.Windows.Forms.FlowDirection.BottomUp>.  
  
## <a name="inserting-flow-breaks"></a>Inserindo quebras de fluxo  
 O <xref:System.Windows.Forms.FlowLayoutPanel> controle fornece uma propriedade FlowBreak para seus controles filhos. Definir o valor da propriedade FlowBreak para `true` faz com que o <xref:System.Windows.Forms.FlowLayoutPanel> controle parar dispor controles no contorno para a próxima linha ou coluna e direção do fluxo atual.  
  
#### <a name="to-insert-flow-breaks"></a>Para inserir quebras de fluxo  
  
1.  Alterar o valor da <xref:System.Windows.Forms.FlowLayoutPanel> do controle <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> propriedade <xref:System.Windows.Forms.FlowDirection.TopDown>.  
  
2.  Selecione uma da <xref:System.Windows.Forms.Button> controles no meio da coluna mais à esquerda.  
  
3.  Definir o valor de <xref:System.Windows.Forms.Button> FlowBreak propriedade como `true`. Observe que a coluna é interrompida e os controles a seguir selecionado <xref:System.Windows.Forms.Button> controlar o fluxo para a coluna seguinte. Definir o valor de <xref:System.Windows.Forms.Button> FlowBreak propriedade como `false` para retornar para o comportamento original.  
  
## <a name="positioning-controls-using-docking-and-anchoring"></a>Posicionando controles usando encaixe e ancoragem  
 Os comportamentos de encaixe e ancoragem dos controles filho diferem dos comportamentos em outras caixas de controles. O encaixe e a ancoragem são relativos ao maior controle na direção do fluxo.  
  
#### <a name="to-position-controls-using-docking-and-anchoring"></a>Para posicionar controles usando encaixe e ancoragem  
  
1.  Aumentar o tamanho do <xref:System.Windows.Forms.FlowLayoutPanel> até que o <xref:System.Windows.Forms.Button> controles são organizados em uma coluna.  
  
2.  Selecione a primeira <xref:System.Windows.Forms.Button> controle. Aumentar a largura para que seja sobre duas vezes tão grande quanto o outro <xref:System.Windows.Forms.Button> controles.  
  
3.  Selecione a segunda <xref:System.Windows.Forms.Button> controle. Alterar o valor de seu <xref:System.Windows.Forms.Control.Anchor%2A> propriedade <xref:System.Windows.Forms.AnchorStyles.Right>. Observe que ele é movido para que sua borda direita é alinhada com a primeira <xref:System.Windows.Forms.Button> borda direita do controle.  
  
4.  Alterar o valor de seu <xref:System.Windows.Forms.Control.Anchor%2A> propriedade <xref:System.Windows.Forms.AnchorStyles.Right> e <xref:System.Windows.Forms.AnchorStyles.Left>. Observe que ela é dimensionada com a mesma largura que a primeira <xref:System.Windows.Forms.Button> controle.  
  
5.  Selecione a terceira <xref:System.Windows.Forms.Button> controle. Alterar o valor de seu <xref:System.Windows.Forms.Control.Dock%2A> propriedade <xref:System.Windows.Forms.DockStyle.Fill>. Observe que ela é dimensionada com a mesma largura que a primeira <xref:System.Windows.Forms.Button> controle.  
  
## <a name="arranging-controls-using-padding-and-margins"></a>Organizando controles usando preenchimento e margens  
 Você também pode organizar controles em seu <xref:System.Windows.Forms.FlowLayoutPanel> controle alterando o <xref:System.Windows.Forms.Control.Padding%2A> e <xref:System.Windows.Forms.Control.Margin%2A> propriedades.  
  
 O <xref:System.Windows.Forms.Control.Padding%2A> propriedade permite que você controle o posicionamento dos controles dentro de um <xref:System.Windows.Forms.FlowLayoutPanel> célula do controle. Especifica o espaçamento entre controles filho e o <xref:System.Windows.Forms.FlowLayoutPanel> borda do controle.  
  
 O <xref:System.Windows.Forms.Control.Margin%2A> propriedade permite que você controle o espaçamento entre controles.  
  
#### <a name="to-arrange-controls-using-the-padding-and-margin-properties"></a>Para organizar controles usando as propriedades de preenchimento e margem  
  
1.  Alterar o valor da <xref:System.Windows.Forms.FlowLayoutPanel> do controle <xref:System.Windows.Forms.Control.Dock%2A> propriedade <xref:System.Windows.Forms.DockStyle.Fill>. Se o formulário é grande o suficiente, o <xref:System.Windows.Forms.Button> controles serão movidos para a primeira coluna do <xref:System.Windows.Forms.FlowLayoutPanel> controle.  
  
2.  Alterar o valor da <xref:System.Windows.Forms.FlowLayoutPanel> do controle <xref:System.Windows.Forms.Control.Padding%2A> propriedade expandindo o <xref:System.Windows.Forms.Control.Padding%2A> entrada no **propriedades** janela e configuração o <xref:System.Windows.Forms.Padding.All%2A> propriedade **20**. Para obter mais informações, consulte [Passo a passo: definindo o layout de controles dos Windows Forms com preenchimento, margens e a propriedade AutoSize](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md). Observe que os controles filho são movidos para o centro do <xref:System.Windows.Forms.FlowLayoutPanel> controle. O maior valor para o <xref:System.Windows.Forms.Control.Padding%2A> propriedade envia os controles filho fora o <xref:System.Windows.Forms.FlowLayoutPanel> bordas do controle.  
  
3.  Selecionar todos o <xref:System.Windows.Forms.Button> controles no <xref:System.Windows.Forms.FlowLayoutPanel> e defina o valor da <xref:System.Windows.Forms.Control.Margin%2A> propriedade **20**. Observe que o espaçamento entre o <xref:System.Windows.Forms.Button> controla aumenta, para que eles são movidos mais separadas. Você pode precisar redimensionar o <xref:System.Windows.Forms.FlowLayoutPanel> controle maior para ver todos os controles filho.  
  
## <a name="inserting-controls-by-double-clicking-them-in-the-toolbox"></a>Inserindo controles ao clicar duas vezes neles na caixa de ferramentas  
 Você pode preencher sua <xref:System.Windows.Forms.FlowLayoutPanel> controle clicando duas vezes em controles de **caixa de ferramentas**.  
  
#### <a name="to-insert-controls-by-double-clicking-in-the-toolbox"></a>Para inserir controles clicando duas vezes na caixa de ferramentas  
  
1.  Clique duas vezes o <xref:System.Windows.Forms.Button> ícone controle no **caixa de ferramentas**. Observe que um novo <xref:System.Windows.Forms.Button> controle aparece no <xref:System.Windows.Forms.FlowLayoutPanel> controle.  
  
2.  Clique duas vezes em vários outros controles na **Caixa de ferramentas**. Observe que os novos controles aparecem em sucessivamente o <xref:System.Windows.Forms.FlowLayoutPanel> controle.  
  
## <a name="inserting-a-control-by-drawing-its-outline"></a>Inserindo um controle ao desenhar seu contorno  
 Você pode inserir um controle em um <xref:System.Windows.Forms.FlowLayoutPanel> controlar e especifique seu tamanho desenhando seus tópicos em uma célula.  
  
#### <a name="to-insert-a-control-by-drawing-its-outline"></a>Para inserir um controle desenhando seu contorno  
  
1.  No **caixa de ferramentas**, clique no <xref:System.Windows.Forms.Button> ícone do controle. Não o arraste para o formulário.  
  
2.  Mova o ponteiro do mouse sobre o <xref:System.Windows.Forms.FlowLayoutPanel> controle. Observe que o ponteiro mudar para uma cruz com o <xref:System.Windows.Forms.Button> ícone de controle.  
  
3.  Clique e mantenha o botão do mouse pressionado.  
  
4.  Arraste o ponteiro do mouse para desenhar o contorno do <xref:System.Windows.Forms.Button> controle. Quando estiver satisfeito com o tamanho, solte o botão do mouse. Observe que o <xref:System.Windows.Forms.Button> controle é criado no próximo abrir local do <xref:System.Windows.Forms.FlowLayoutPanel> controle.  
  
## <a name="inserting-controls-using-the-insertion-bar"></a>Inserindo controles usando a barra de inserção  
 Você pode inserir controles em uma posição específica em um <xref:System.Windows.Forms.FlowLayoutPanel> controle. Quando você arrasta um controle para o <xref:System.Windows.Forms.FlowLayoutPanel> área do cliente do controle, uma barra de inserção é exibida para indicar onde o controle será inserido.  
  
#### <a name="to-insert-a-control-using-the-caret"></a>Para inserir um controle usando o sinal de interpolação  
  
1.  Arraste um <xref:System.Windows.Forms.Button> controlar do **caixa de ferramentas** no <xref:System.Windows.Forms.FlowLayoutPanel> controlar e aponte para o espaço entre dois <xref:System.Windows.Forms.Button> controles. Observe que uma barra de inserção é desenhada, indicando onde o <xref:System.Windows.Forms.Button> serão colocados quando ele é colocado no <xref:System.Windows.Forms.FlowLayoutPanel> controle. Antes de descartar a nova <xref:System.Windows.Forms.Button> controle para o <xref:System.Windows.Forms.FlowLayoutPanel> controlar, mova o ponteiro do mouse para observar como a barra de inserção se move.  
  
2.  Descartar a nova <xref:System.Windows.Forms.Button> controle para o <xref:System.Windows.Forms.FlowLayoutPanel> controle. Observe que o novo <xref:System.Windows.Forms.Button> controle não está alinhado com os outros, porque seu <xref:System.Windows.Forms.Control.Margin%2A> propriedade tem um valor diferente.  
  
## <a name="reassigning-existing-controls-to-a-different-parent"></a>Reatribuição de controles existentes a um pai diferente  
 Você pode atribuir controles que existem em seu formulário para um novo <xref:System.Windows.Forms.FlowLayoutPanel> controle.  
  
#### <a name="to-reparent-existing-controls"></a>Para reassociar os controles existentes  
  
1.  Arraste três <xref:System.Windows.Forms.Button> controla a partir de **caixa de ferramentas** para o formulário. Posicione-os próximo entre si, mas deixe-os desalinhados.  
  
2.  No **caixa de ferramentas**, clique no <xref:System.Windows.Forms.FlowLayoutPanel> ícone do controle. Não o arraste para o formulário.  
  
3.  Mova o ponteiro do mouse perto de três <xref:System.Windows.Forms.Button> controles. Observe que o ponteiro mudar para uma cruz com o <xref:System.Windows.Forms.FlowLayoutPanel> ícone de controle.  
  
4.  Clique e mantenha o botão do mouse pressionado.  
  
5.  Arraste o ponteiro do mouse para desenhar o contorno do <xref:System.Windows.Forms.FlowLayoutPanel> controle. Desenhar o contorno em torno de três <xref:System.Windows.Forms.Button> controles.  
  
6.  Solte o botão do mouse. Observe que três <xref:System.Windows.Forms.Button> controles são inseridos a <xref:System.Windows.Forms.FlowLayoutPanel> controle.  
  
## <a name="next-steps"></a>Próximas etapas  
 Você pode obter um layout complexo usando uma combinação de controles e painéis de layout. Sugestões para exploração adicional incluem:  
  
-   Redimensionar uma da <xref:System.Windows.Forms.Button> controles para um tamanho maior e observe o efeito no layout.  
  
-   Os painéis de layout podem conter outros painéis de layout. Experiência com descartar um <xref:System.Windows.Forms.TableLayoutPanel> controle no controle existente.  
  
-   Encaixe o <xref:System.Windows.Forms.FlowLayoutPanel> controle para o formulário pai. Redimensione o formulário e observe o efeito no layout.  
  
-   Definir o <xref:System.Windows.Forms.Control.Visible%2A> propriedade de um dos controles para `false` e observe como o <xref:System.Windows.Forms.FlowLayoutPanel> reflui em resposta.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [Passo a passo: organizando controles nos Windows Forms usando um TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [Instruções passo a passo: organizando controles no Windows Forms usando guias de alinhamento](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [Microsoft Windows User Experience, Official Guidelines for User Interface Developers and Designers (Experiência do usuário do Microsoft Windows, diretrizes oficiais para desenvolvedores e designers da interface do usuário). Redmond, WA: Microsoft Press, 1999. (USBN: 0-7356-0566-1)](http://www.microsoft.com/mspress/southpacific/books/book11588.htm)  
 [Visão geral da propriedade AutoSize](../../../../docs/framework/winforms/controls/autosize-property-overview.md)  
 [Como encaixar controles nos Windows Forms](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md)  
 [Como ancorar controles no Windows Forms](../../../../docs/framework/winforms/controls/how-to-anchor-controls-on-windows-forms.md)  
 [Passo a passo: definindo o layout de controles dos Windows Forms com preenchimento, margens e a propriedade AutoSize](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)
