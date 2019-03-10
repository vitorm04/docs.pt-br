---
title: 'Passo a passo: Organizando controles nos Windows Forms utilizando um TableLayoutPanel'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], arranging with TableLayoutPanel
- TableLayoutPanel control [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d474885e-12cc-4ab7-b997-2a23a643049b
ms.openlocfilehash: 8999dba110ee21b735c79ccc10c5af52dbfcdea9
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57712988"
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel"></a>Passo a passo: Organizando controles nos Windows Forms utilizando um TableLayoutPanel
Alguns aplicativos exigem um formulário com um layout que se organiza adequadamente à medida que o formulário é redimensionado ou conforme o tamanho do conteúdo é alterado. Quando você precisa de um layout dinâmico e não deseja manipular <xref:System.Windows.Forms.Control.Layout> eventos explicitamente no seu código, considere o uso de um painel de layout.  
  
 O <xref:System.Windows.Forms.FlowLayoutPanel> controle e o <xref:System.Windows.Forms.TableLayoutPanel> controle fornecem maneiras intuitivas para organizar os controles no seu formulário. Ambos fornecem uma capacidade automática e configurável de controlar as posições relativas dos controles filho contidos neles e ambos oferecem recursos de layout dinâmico em tempo de execução, para que eles possam redimensionar e reposicionar os controles filho conforme as dimensões do formulário pai se alteram. Os painéis de layout podem ser aninhados em painéis de layout, para permitir a realização de interfaces do usuário sofisticadas.  
  
 O <xref:System.Windows.Forms.FlowLayoutPanel> organiza seu conteúdo em uma direção específica de fluxo: horizontal ou vertical. Seu conteúdo pode ser encapsulado de uma linha à outra ou de uma coluna à próxima. Como alternativa, seu conteúdo pode ser recortado, em vez de encapsulado. Para obter mais informações, confira [Passo a passo: Organizando controles nos Windows Forms utilizando um FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md).  
  
 O <xref:System.Windows.Forms.TableLayoutPanel> organiza seu conteúdo em uma grade, fornecendo funcionalidade semelhante ao HTML \<tabela > elemento. O <xref:System.Windows.Forms.TableLayoutPanel> controle permite que você coloque controles em um layout de grade sem a necessidade de especificar precisamente a posição de cada controle individual. Suas células são organizadas em linhas e colunas, que podem ter diferentes tamanhos. As células podem ser mescladas entre linhas e colunas. As células podem conter qualquer coisa que um formulário pode conter e se comportam, na maioria de outros aspectos, como contêineres.  
  
 O <xref:System.Windows.Forms.TableLayoutPanel> controle também fornece uma funcionalidade de Redimensionamento proporcional em tempo de execução para que seu layout pode ser alterado suavemente conforme seu formulário é redimensionado. Isso faz com que o <xref:System.Windows.Forms.TableLayoutPanel> controle adequado para fins como formulários de entrada de dados e aplicativos localizados. Para obter mais informações, confira [Passo a passo: Criando um formulário do Windows redimensionável para entrada de dados](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100)) e [passo a passo: Criando um formulário do Windows localizáveis](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100)).  
  
 Em geral, você não deve usar um <xref:System.Windows.Forms.TableLayoutPanel> controle como um contêiner para todo o layout. Use <xref:System.Windows.Forms.TableLayoutPanel> controles para fornecer recursos de Redimensionamento proporcional para partes do layout.  
  
 As tarefas ilustradas neste passo a passo incluem:  
  
-   Criação de um projeto dos Windows Forms  
  
-   Organização de controles em linhas e colunas  
  
-   Configuração de propriedades de linha e coluna  
  
-   Extensão de linhas e colunas com um controle  
  
-   Manipulação automática de estouros  
  
-   Inserindo controles ao clicar duas vezes neles na caixa de ferramentas  
  
-   Inserindo um controle ao desenhar seu contorno  
  
-   Reatribuição de controles existentes a um pai diferente  
  
 Ao terminar, você terá um entendimento da função desempenhada por esses importantes recursos de layout.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="creating-the-project"></a>Criando o Projeto  
 A primeira etapa é criar o projeto e configurar o formulário.  
  
#### <a name="to-create-the-project"></a>Para criar o projeto  
  
1.  Crie um projeto de aplicativo do Windows chamado "TableLayoutPanelExample". Para obter mais informações, confira [Como: Criar um projeto de aplicativo do Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) .  
  
2.  Selecione o formulário no **Designer de Formulários** **do Windows**.  
  
## <a name="arranging-controls-in-rows-and-columns"></a>Organização de controles em linhas e colunas  
 O <xref:System.Windows.Forms.TableLayoutPanel> controle permite que você organize facilmente os controles em linhas e colunas.  
  
#### <a name="to-arrange-controls-in-rows-and-columns-using-a-tablelayoutpanel"></a>Para organizar controles em linhas e colunas utilizando um TableLayoutPanel  
  
1.  Arraste uma <xref:System.Windows.Forms.TableLayoutPanel> controlar do **caixa de ferramentas** para seu formulário. Observe que, por padrão, o <xref:System.Windows.Forms.TableLayoutPanel> controle tem quatro células.  
  
2.  Arraste uma <xref:System.Windows.Forms.Button> controlar do **caixa de ferramentas** no <xref:System.Windows.Forms.TableLayoutPanel> controlar e solte-o em uma das células. Observe que o <xref:System.Windows.Forms.Button> controle é criado dentro da célula selecionada.  
  
3.  Arraste mais três <xref:System.Windows.Forms.Button> controles do **caixa de ferramentas** no <xref:System.Windows.Forms.TableLayoutPanel> controlar, para que cada célula contenha um botão.  
  
4.  Pegue na alça de dimensionamento vertical entre as duas colunas e mova-a para a esquerda. Observe que o <xref:System.Windows.Forms.Button> controles na primeira coluna são redimensionados para uma largura menor, enquanto o tamanho do <xref:System.Windows.Forms.Button> controles na segunda coluna é alterado.  
  
5.  Pegue na alça de dimensionamento vertical entre as duas colunas e mova-a para a direita. Observe que o <xref:System.Windows.Forms.Button> controles na primeira coluna retornam ao seu tamanho original, enquanto o <xref:System.Windows.Forms.Button> controles na segunda coluna são movidos para a direita.  
  
6.  Mova a alça de dimensionamento horizontal para cima e para baixo para ver o efeito sobre os controles no painel.  
  
## <a name="positioning-controls-within-cells-using-docking-and-anchoring"></a>Posicionando controles dentro de células usando o encaixe e a ancoragem  
 O comportamento de ancoragem de controles filho em um <xref:System.Windows.Forms.TableLayoutPanel> difere do comportamento em outros controles de contêiner. O comportamento de ancoragem de controles filho é igual a outras caixas de controles.  
  
#### <a name="positioning-controls-within-cells"></a>Posicionando controles em células  
  
1.  Selecione a primeira <xref:System.Windows.Forms.Button> controle. Altere o valor de sua <xref:System.Windows.Forms.Control.Dock%2A> propriedade para <xref:System.Windows.Forms.DockStyle.Fill>. Observe que o <xref:System.Windows.Forms.Button> controle se expande para preencher a célula.  
  
2.  Selecione um dos outros <xref:System.Windows.Forms.Button> controles. Altere o valor de sua <xref:System.Windows.Forms.Control.Anchor%2A> propriedade para <xref:System.Windows.Forms.AnchorStyles.Right>. Observe que ele é movido para que sua borda direita fique próxima à borda direita da célula. A distância entre as bordas é a soma do <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Margin%2A> propriedade e o painel <xref:System.Windows.Forms.Control.Padding%2A> propriedade.  
  
3.  Altere o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Anchor%2A> propriedade <xref:System.Windows.Forms.AnchorStyles.Right> e <xref:System.Windows.Forms.AnchorStyles.Left>. Observe que o controle é dimensionado para a largura da célula, com o <xref:System.Windows.Forms.Control.Margin%2A> e <xref:System.Windows.Forms.Control.Padding%2A> valores levadas em conta.  
  
4.  Repita as etapas 2 e 3 com a <xref:System.Windows.Forms.AnchorStyles.Top> e <xref:System.Windows.Forms.AnchorStyles.Bottom> estilos.  
  
## <a name="setting-row-and-column-properties"></a>Configuração de propriedades de linha e coluna  
 Você pode definir propriedades individuais de linhas e colunas usando o <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> e <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> coleções.  
  
#### <a name="to-set-row-and-column-properties"></a>Para definir as propriedades de linha e coluna  
  
1.  Selecione o <xref:System.Windows.Forms.TableLayoutPanel> no controlar os **Designer de formulários do Windows**.  
  
2.  No **propriedades** windows, abra o <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> coleção clicando no botão de reticências (![captura de tela de VisualStudioEllipsesButton](../media/vbellipsesbutton.png "vbEllipsesButton")) botão ao lado de **colunas** entrada.  
  
3.  Selecione a primeira coluna e altere o valor de sua <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> propriedade para <xref:System.Windows.Forms.SizeType.AutoSize>. Clique em **OK** para aceitar a alteração. Observe que a largura da primeira coluna é reduzida para ajustar o <xref:System.Windows.Forms.Button> controle. Observe também que a largura da coluna não é redimensionável.  
  
4.  No **propriedades** janela, abra o <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> coleção e selecione a primeira coluna. Altere o valor de sua <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> propriedade para <xref:System.Windows.Forms.SizeType.Percent>. Clique em **OK** para aceitar a alteração. Redimensionar o <xref:System.Windows.Forms.TableLayoutPanel> o controle para uma largura maior e observe que a largura da primeira coluna se expande. Redimensionar o <xref:System.Windows.Forms.TableLayoutPanel> controlar para uma largura menor e observe que os botões na primeira coluna são dimensionados para caber na célula. Observe também que a largura da coluna é redimensionável.  
  
5.  No **propriedades** janela, abra o <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> coleção e selecione todas as colunas listadas. Defina o valor de cada <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> propriedade para <xref:System.Windows.Forms.SizeType.Percent>. Clique em **OK** para aceitar a alteração. Repita com o <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> coleção.  
  
6.  Pegue um do alças de redimensionamento de canto e redimensione a largura e a altura do <xref:System.Windows.Forms.TableLayoutPanel> controle. Observe que as linhas e colunas são redimensionadas conforme o <xref:System.Windows.Forms.TableLayoutPanel> alterações de tamanho do controle. Observe também que as linhas e colunas são redimensionáveis com as alças de dimensionamento horizontal e vertical.  
  
## <a name="spanning-rows-and-columns-with-a-control"></a>Extensão de linhas e colunas com um controle  
 O <xref:System.Windows.Forms.TableLayoutPanel> controle adiciona várias propriedades novas aos controles em tempo de design. Duas dessas propriedades são a `RowSpan` e `ColumnSpan`. Você pode usar essas propriedades para fazer um controle estender-se por mais de uma linha ou coluna.  
  
#### <a name="to-span-rows-and-columns-with-a-control"></a>Para estender linhas e colunas com um controle  
  
1.  Selecione o <xref:System.Windows.Forms.Button> controle na primeira linha e primeira coluna.  
  
2.  Na janela **Propriedades**, altere o valor da propriedade `ColumnSpan` para **2**. Observe que o <xref:System.Windows.Forms.Button> controle preenche a primeira coluna e a segunda coluna. Observe também que uma linha extra foi adicionada para acomodar essa alteração.  
  
3.  Repita a etapa 2 para a propriedade `RowSpan`.  
  
## <a name="inserting-controls-by-double-clicking-them-in-the-toolbox"></a>Inserindo controles ao clicar duas vezes neles na caixa de ferramentas  
 Você pode popular seu <xref:System.Windows.Forms.TableLayoutPanel> controle clicando duas vezes em controles na **caixa de ferramentas**.  
  
#### <a name="to-insert-controls-by-double-clicking-in-the-toolbox"></a>Para inserir controles clicando duas vezes na caixa de ferramentas  
  
1.  Arraste uma <xref:System.Windows.Forms.TableLayoutPanel> controlar do **caixa de ferramentas** para seu formulário.  
  
2.  Clique duas vezes o <xref:System.Windows.Forms.Button> ícone do controle no **caixa de ferramentas**. Observe que um novo controle de botão aparece no <xref:System.Windows.Forms.TableLayoutPanel> primeira célula do controle.  
  
3.  Clique duas vezes em vários outros controles na **Caixa de ferramentas**. Observe que os novos controles aparecem sucessivamente no <xref:System.Windows.Forms.TableLayoutPanel> células desocupadas do controle. Observe também que o <xref:System.Windows.Forms.TableLayoutPanel> controle se expande para acomodar os novos controles se nenhuma célula aberta estiver disponível.  
  
## <a name="automatic-handling-of-overflows"></a>Manipulação automática de estouros  
 Quando você estiver inserindo controles para o <xref:System.Windows.Forms.TableLayoutPanel> controle, você poderá ficar sem células vazias para seus novos controles. O <xref:System.Windows.Forms.TableLayoutPanel> controle manipula essa situação automaticamente, aumentando o número de células.  
  
#### <a name="to-observe-automatic-handling-of-overflows"></a>Observar a manipulação automática de estouros  
  
1.  Se houver células vazias ainda a <xref:System.Windows.Forms.TableLayoutPanel> controlar, continue inserindo uma nova <xref:System.Windows.Forms.Button> controla até que o <xref:System.Windows.Forms.TableLayoutPanel> controle está cheio.  
  
2.  Uma vez a <xref:System.Windows.Forms.TableLayoutPanel> controle está cheio, clique duas vezes o <xref:System.Windows.Forms.Button> ícone na **caixa de ferramentas** inserir outro <xref:System.Windows.Forms.Button> controle. Observe que o <xref:System.Windows.Forms.TableLayoutPanel> controle cria novas células para acomodar o novo controle. Insira mais alguns controles e observe o comportamento de redimensionamento.  
  
3.  Altere o valor da <xref:System.Windows.Forms.TableLayoutPanel> do controle <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> propriedade <xref:System.Windows.Forms.TableLayoutPanelGrowStyle.FixedSize>. Clique duas vezes o <xref:System.Windows.Forms.Button> ícone na **caixa de ferramentas** inserir <xref:System.Windows.Forms.Button> controla até que o <xref:System.Windows.Forms.TableLayoutPanel> controle está cheio. Clique duas vezes o <xref:System.Windows.Forms.Button> ícone na **caixa de ferramentas** novamente. Observe que você receberá uma mensagem de erro do **Designer de Formulários do Windows**, informando que não possível criar mais linhas e colunas.  
  
## <a name="inserting-a-control-by-drawing-its-outline"></a>Inserindo um controle ao desenhar seu contorno  
 Você pode inserir um controle em um <xref:System.Windows.Forms.TableLayoutPanel> controlar e especificar seu tamanho, desenhando seu contorno em uma célula.  
  
#### <a name="to-insert-a-control-by-drawing-its-outline"></a>Para inserir um controle desenhando seu contorno  
  
1.  Arraste uma <xref:System.Windows.Forms.TableLayoutPanel> controlar do **caixa de ferramentas** para seu formulário.  
  
2.  No **caixa de ferramentas**, clique no <xref:System.Windows.Forms.Button> ícone do controle. Não o arraste para o formulário.  
  
3.  Mova o ponteiro do mouse sobre o <xref:System.Windows.Forms.TableLayoutPanel> controle. Observe que o ponteiro muda para uma mira com o <xref:System.Windows.Forms.Button> ícone do controle anexado.  
  
4.  Clique e mantenha o botão do mouse pressionado.  
  
5.  Arraste o ponteiro do mouse para desenhar o contorno do <xref:System.Windows.Forms.Button> controle. Quando estiver satisfeito com o tamanho, solte o botão do mouse. Observe que o <xref:System.Windows.Forms.Button> controle é criado na célula em que você desenhou o contorno do controle.  
  
## <a name="multiple-controls-within-cells-are-not-permitted"></a>Vários controles dentro de células não são permitidos  
 O <xref:System.Windows.Forms.TableLayoutPanel> controle pode conter apenas um controle filho por célula.  
  
#### <a name="to-demonstrate-that-multiple-controls-within-cells-are-not-permitted"></a>Para demonstrar que vários controles dentro de células não são permitidos  
  
-   Arraste uma <xref:System.Windows.Forms.Button> controlar do **caixa de ferramentas** no <xref:System.Windows.Forms.TableLayoutPanel> controlar e solte-o em uma das células ocupadas. Observe que o <xref:System.Windows.Forms.TableLayoutPanel> controle não permite que você remover o <xref:System.Windows.Forms.Button> controle na célula ocupada.  
  
## <a name="swapping-controls"></a>Trocando controles  
 O <xref:System.Windows.Forms.TableLayoutPanel> controle permite que você troque os controles que ocupam duas células diferentes.  
  
#### <a name="to-swap-controls"></a>Para trocar controles  
  
-   Arraste um do <xref:System.Windows.Forms.Button> controles de uma célula ocupada e solte para outra célula ocupada. Observe que os dois controles são movidos de uma célula para a outra.  
  
## <a name="next-steps"></a>Próximas etapas  
 Você pode obter um layout complexo usando uma combinação de controles e painéis de layout. Sugestões para exploração adicional incluem:  
  
-   Tente redimensionar um do <xref:System.Windows.Forms.Button> controles para um tamanho maior e observe o efeito no layout.  
  
-   Cole uma seleção de vários controles para o <xref:System.Windows.Forms.TableLayoutPanel> controlar e observe como os controles são inseridos.  
  
-   Os painéis de layout podem conter outros painéis de layout. Experimente soltar um <xref:System.Windows.Forms.TableLayoutPanel> controle no controle existente.  
  
-   Encaixe o <xref:System.Windows.Forms.TableLayoutPanel> controle ao formulário pai. Redimensione o formulário e observe o efeito no layout.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [Passo a passo: Organizando controles nos Windows Forms utilizando um FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Passo a passo: Organizando controles nos formulários do Windows usando guias de alinhamento](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [Microsoft Windows User Experience, Official Guidelines for User Interface Developers and Designers (Experiência do usuário do Microsoft Windows, diretrizes oficiais para desenvolvedores e designers da interface do usuário). Redmond, WA: Microsoft Press, 1999. (USBN: 0-7356-0566-1)](https://www.microsoft.com/mspress/southpacific/books/book11588.htm)
- [Passo a passo: Criando um formulário do Windows redimensionável para entrada de dados](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))
- [Passo a passo: Criando um formulário do Windows localizáveis](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100))
- [Práticas recomendadas para o controle TableLayoutPanel](best-practices-for-the-tablelayoutpanel-control.md)
- [Visão geral da propriedade AutoSize](autosize-property-overview.md)
- [Como: Encaixar controles nos Windows Forms](how-to-dock-controls-on-windows-forms.md)
- [Como: Ancoragem de controles nos Windows Forms](how-to-anchor-controls-on-windows-forms.md)
- [Passo a passo: Definindo o layout dos Windows Forms controles com preenchimento, margens e a propriedade AutoSize](windows-forms-controls-padding-autosize.md)
