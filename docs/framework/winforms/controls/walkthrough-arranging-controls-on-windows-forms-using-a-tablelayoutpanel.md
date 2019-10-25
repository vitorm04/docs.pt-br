---
title: 'Explicação passo a passo: organizando controles no Windows Forms utilizando um TableLayoutPanel'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], arranging with TableLayoutPanel
- TableLayoutPanel control [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d474885e-12cc-4ab7-b997-2a23a643049b
ms.openlocfilehash: 7b7380690d8668f46b98272e1d42640f23679b19
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72799118"
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel"></a>Explicação passo a passo: organizando controles no Windows Forms utilizando um TableLayoutPanel

Alguns aplicativos exigem um formulário com um layout que se organiza adequadamente à medida que o formulário é redimensionado ou conforme o tamanho do conteúdo é alterado. Quando você precisar de um layout dinâmico e não quiser manipular <xref:System.Windows.Forms.Control.Layout> eventos explicitamente em seu código, considere o uso de um painel de layout.

O controle de <xref:System.Windows.Forms.FlowLayoutPanel> e o controle de <xref:System.Windows.Forms.TableLayoutPanel> fornecem maneiras intuitivas de organizar controles em seu formulário. Ambos fornecem uma capacidade automática e configurável de controlar as posições relativas dos controles filho contidos neles e ambos oferecem recursos de layout dinâmico em tempo de execução, para que eles possam redimensionar e reposicionar os controles filho conforme as dimensões do formulário pai se alteram. Os painéis de layout podem ser aninhados em painéis de layout, para permitir a realização de interfaces do usuário sofisticadas.

O <xref:System.Windows.Forms.FlowLayoutPanel> organiza seu conteúdo em uma direção de fluxo específica: horizontal ou vertical. Seu conteúdo pode ser encapsulado de uma linha à outra ou de uma coluna à próxima. Como alternativa, seu conteúdo pode ser recortado, em vez de encapsulado. Para obter mais informações, consulte [Passo a passo: organizando controles nos Windows Forms usando um FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md).

O <xref:System.Windows.Forms.TableLayoutPanel> organiza seu conteúdo em uma grade, fornecendo uma funcionalidade semelhante ao elemento HTML \<tabela >. O controle <xref:System.Windows.Forms.TableLayoutPanel> permite colocar controles em um layout de grade sem exigir que você especifique precisamente a posição de cada controle individual. Suas células são organizadas em linhas e colunas, que podem ter diferentes tamanhos. As células podem ser mescladas entre linhas e colunas. As células podem conter qualquer coisa que um formulário pode conter e se comportam, na maioria de outros aspectos, como contêineres.

O controle de <xref:System.Windows.Forms.TableLayoutPanel> também fornece uma capacidade de redimensionamento proporcional em tempo de execução, de modo que o layout pode ser alterado sem problemas à medida que seu formulário é redimensionado. Isso torna o controle de <xref:System.Windows.Forms.TableLayoutPanel> bem adequado para fins como formulários de entrada de dados e aplicativos localizados. Para obter mais informações, consulte [Passo a passo: criando um Windows Form redimensionável para entrada de dados](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100)) e [Passo a passo: criando um Windows Form localizável](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100)).

Em geral, você não deve usar um controle de <xref:System.Windows.Forms.TableLayoutPanel> como um contêiner para todo o layout. Use controles de <xref:System.Windows.Forms.TableLayoutPanel> para fornecer recursos de redimensionamento proporcional a partes do layout.

As tarefas ilustradas neste passo a passo incluem:

- Criação de um projeto dos Windows Forms

- Organização de controles em linhas e colunas

- Configuração de propriedades de linha e coluna

- Extensão de linhas e colunas com um controle

- Manipulação automática de estouros

- Inserindo controles ao clicar duas vezes neles na caixa de ferramentas

- Inserindo um controle ao desenhar seu contorno

- Reatribuição de controles existentes a um pai diferente

Ao terminar, você terá um entendimento da função desempenhada por esses importantes recursos de layout.

## <a name="creating-the-project"></a>Criando o Projeto

A primeira etapa é criar o projeto e configurar o formulário.

#### <a name="to-create-the-project"></a>Para criar o projeto

1. Crie um projeto de aplicativo do Windows chamado "TableLayoutPanelExample". Para obter mais informações, consulte [como: criar um projeto de aplicativo Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) .

2. Selecione o formulário no **Designer de Formulários** **do Windows**.

## <a name="arranging-controls-in-rows-and-columns"></a>Organização de controles em linhas e colunas

O controle <xref:System.Windows.Forms.TableLayoutPanel> permite que você organize facilmente os controles em linhas e colunas.

#### <a name="to-arrange-controls-in-rows-and-columns-using-a-tablelayoutpanel"></a>Para organizar controles em linhas e colunas utilizando um TableLayoutPanel

1. Arraste um controle de <xref:System.Windows.Forms.TableLayoutPanel> da **caixa de ferramentas** para seu formulário. Observe que, por padrão, o controle de <xref:System.Windows.Forms.TableLayoutPanel> tem quatro células.

2. Arraste um controle de <xref:System.Windows.Forms.Button> da **caixa de ferramentas** para o controle de <xref:System.Windows.Forms.TableLayoutPanel> e solte-o em uma das células. Observe que o controle de <xref:System.Windows.Forms.Button> é criado dentro da célula que você selecionou.

3. Arraste mais três controles de <xref:System.Windows.Forms.Button> da **caixa de ferramentas** para o controle de <xref:System.Windows.Forms.TableLayoutPanel>, de forma que cada célula contenha um botão.

4. Pegue na alça de dimensionamento vertical entre as duas colunas e mova-a para a esquerda. Observe que os controles de <xref:System.Windows.Forms.Button> na primeira coluna são redimensionados para uma largura menor, enquanto o tamanho dos controles de <xref:System.Windows.Forms.Button> na segunda coluna é inalterado.

5. Pegue na alça de dimensionamento vertical entre as duas colunas e mova-a para a direita. Observe que os controles de <xref:System.Windows.Forms.Button> na primeira coluna retornam ao seu tamanho original, enquanto os controles de <xref:System.Windows.Forms.Button> na segunda coluna são movidos para a direita.

6. Mova a alça de dimensionamento horizontal para cima e para baixo para ver o efeito sobre os controles no painel.

## <a name="positioning-controls-within-cells-using-docking-and-anchoring"></a>Posicionando controles dentro de células usando o encaixe e a ancoragem

O comportamento de ancoragem dos controles filho em uma <xref:System.Windows.Forms.TableLayoutPanel> difere do comportamento em outros controles de contêiner. O comportamento de ancoragem de controles filho é igual a outras caixas de controles.

#### <a name="positioning-controls-within-cells"></a>Posicionando controles em células

1. Selecione o primeiro controle de <xref:System.Windows.Forms.Button>. Altere o valor de sua propriedade <xref:System.Windows.Forms.Control.Dock%2A> para <xref:System.Windows.Forms.DockStyle.Fill>. Observe que o controle de <xref:System.Windows.Forms.Button> se expande para preencher sua célula.

2. Selecione um dos outros controles de <xref:System.Windows.Forms.Button>. Altere o valor de sua propriedade <xref:System.Windows.Forms.Control.Anchor%2A> para <xref:System.Windows.Forms.AnchorStyles.Right>. Observe que ele é movido para que sua borda direita fique próxima à borda direita da célula. A distância entre as bordas é a soma da propriedade <xref:System.Windows.Forms.Control.Margin%2A> do controle de <xref:System.Windows.Forms.Button> e da propriedade de <xref:System.Windows.Forms.Control.Padding%2A> do painel.

3. Altere o valor da propriedade <xref:System.Windows.Forms.Control.Anchor%2A> do controle de <xref:System.Windows.Forms.Button> para <xref:System.Windows.Forms.AnchorStyles.Right> e <xref:System.Windows.Forms.AnchorStyles.Left>. Observe que o controle é dimensionado para a largura da célula, com a <xref:System.Windows.Forms.Control.Margin%2A> e <xref:System.Windows.Forms.Control.Padding%2A> valores levados em conta.

4. Repita as etapas 2 e 3 com os estilos de <xref:System.Windows.Forms.AnchorStyles.Top> e <xref:System.Windows.Forms.AnchorStyles.Bottom>.

## <a name="setting-row-and-column-properties"></a>Configuração de propriedades de linha e coluna

Você pode definir propriedades individuais de linhas e colunas usando as coleções <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> e <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A>.

#### <a name="to-set-row-and-column-properties"></a>Para definir as propriedades de linha e coluna

1. Selecione o controle de <xref:System.Windows.Forms.TableLayoutPanel> no **Designer de formulários do Windows**.

2. Nas janelas de **Propriedades** , abra a coleção de <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> clicando nas reticências (![o botão de reticências (...) no botão janela Propriedades do Visual Studio.](./media/visual-studio-ellipsis-button.png)) ao lado da entrada **colunas** .

3. Selecione a primeira coluna e altere o valor de sua propriedade <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> para <xref:System.Windows.Forms.SizeType.AutoSize>. Clique em **OK** para aceitar a alteração. Observe que a largura da primeira coluna é reduzida para se ajustar ao controle de <xref:System.Windows.Forms.Button>. Observe também que a largura da coluna não é redimensionável.

4. Na janela **Propriedades** , abra a coleção de <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> e selecione a primeira coluna. Altere o valor de sua propriedade <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> para <xref:System.Windows.Forms.SizeType.Percent>. Clique em **OK** para aceitar a alteração. Redimensione o controle de <xref:System.Windows.Forms.TableLayoutPanel> para uma largura maior e observe que a largura da primeira coluna se expande. Redimensione o controle de <xref:System.Windows.Forms.TableLayoutPanel> para uma largura menor e observe que os botões na primeira coluna são dimensionados para se ajustarem à célula. Observe também que a largura da coluna é redimensionável.

5. Na janela **Propriedades** , abra a coleção de <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> e selecione todas as colunas listadas. Defina o valor de cada propriedade <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> como <xref:System.Windows.Forms.SizeType.Percent>. Clique em **OK** para aceitar a alteração. Repita com a coleção de <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A>.

6. Pegue um dos identificadores de redimensionamento de canto e redimensione a largura e a altura do controle de <xref:System.Windows.Forms.TableLayoutPanel>. Observe que as linhas e colunas são redimensionadas à medida que o tamanho do controle de <xref:System.Windows.Forms.TableLayoutPanel> é alterado. Observe também que as linhas e colunas são redimensionáveis com as alças de dimensionamento horizontal e vertical.

## <a name="spanning-rows-and-columns-with-a-control"></a>Extensão de linhas e colunas com um controle

O controle <xref:System.Windows.Forms.TableLayoutPanel> adiciona várias propriedades novas a controles em tempo de design. Duas dessas propriedades são a `RowSpan` e `ColumnSpan`. Você pode usar essas propriedades para fazer um controle estender-se por mais de uma linha ou coluna.

#### <a name="to-span-rows-and-columns-with-a-control"></a>Para estender linhas e colunas com um controle

1. Selecione o controle de <xref:System.Windows.Forms.Button> na primeira linha e a primeira coluna.

2. Na janela **Propriedades**, altere o valor da propriedade `ColumnSpan` para **2**. Observe que o controle de <xref:System.Windows.Forms.Button> preenche a primeira coluna e a segunda coluna. Observe também que uma linha extra foi adicionada para acomodar essa alteração.

3. Repita a etapa 2 para a propriedade `RowSpan`.

## <a name="inserting-controls-by-double-clicking-them-in-the-toolbox"></a>Inserindo controles ao clicar duas vezes neles na caixa de ferramentas

Você pode preencher o controle de <xref:System.Windows.Forms.TableLayoutPanel> clicando duas vezes em controles na **caixa de ferramentas**.

#### <a name="to-insert-controls-by-double-clicking-in-the-toolbox"></a>Para inserir controles clicando duas vezes na caixa de ferramentas

1. Arraste um controle de <xref:System.Windows.Forms.TableLayoutPanel> da **caixa de ferramentas** para seu formulário.

2. Clique duas vezes no ícone de controle de <xref:System.Windows.Forms.Button> na **caixa de ferramentas**. Observe que um novo controle de botão aparece na primeira célula do controle de <xref:System.Windows.Forms.TableLayoutPanel>.

3. Clique duas vezes em vários outros controles na **Caixa de ferramentas**. Observe que os novos controles aparecem sucessivamente nas células desocupadas do controle de <xref:System.Windows.Forms.TableLayoutPanel>. Observe também que o controle de <xref:System.Windows.Forms.TableLayoutPanel> se expande para acomodar os novos controles se nenhuma célula aberta estiver disponível.

## <a name="automatic-handling-of-overflows"></a>Manipulação automática de estouros

Ao inserir controles no controle de <xref:System.Windows.Forms.TableLayoutPanel>, você pode ficar sem células vazias para os novos controles. O controle de <xref:System.Windows.Forms.TableLayoutPanel> manipula essa situação automaticamente aumentando o número de células.

#### <a name="to-observe-automatic-handling-of-overflows"></a>Observar a manipulação automática de estouros

1. Se ainda houver células vazias no controle de <xref:System.Windows.Forms.TableLayoutPanel>, continue inserindo novos controles de <xref:System.Windows.Forms.Button> até que o controle de <xref:System.Windows.Forms.TableLayoutPanel> esteja cheio.

2. Quando o controle de <xref:System.Windows.Forms.TableLayoutPanel> estiver cheio, clique duas vezes no ícone de <xref:System.Windows.Forms.Button> na **caixa de ferramentas** para inserir outro controle de <xref:System.Windows.Forms.Button>. Observe que o controle de <xref:System.Windows.Forms.TableLayoutPanel> cria novas células para acomodar o novo controle. Insira mais alguns controles e observe o comportamento de redimensionamento.

3. Altere o valor da propriedade <xref:System.Windows.Forms.TableLayoutPanel> do controle <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> para <xref:System.Windows.Forms.TableLayoutPanelGrowStyle.FixedSize>. Clique duas vezes no ícone de <xref:System.Windows.Forms.Button> na **caixa de ferramentas** para inserir <xref:System.Windows.Forms.Button> controles até que o controle de <xref:System.Windows.Forms.TableLayoutPanel> esteja cheio. Clique duas vezes no ícone de <xref:System.Windows.Forms.Button> na **caixa de ferramentas** novamente. Observe que você receberá uma mensagem de erro do **Designer de Formulários do Windows**, informando que não possível criar mais linhas e colunas.

## <a name="inserting-a-control-by-drawing-its-outline"></a>Inserindo um controle ao desenhar seu contorno

Você pode inserir um controle em um controle de <xref:System.Windows.Forms.TableLayoutPanel> e especificar seu tamanho, desenhando seu contorno em uma célula.

#### <a name="to-insert-a-control-by-drawing-its-outline"></a>Para inserir um controle desenhando seu contorno

1. Arraste um controle de <xref:System.Windows.Forms.TableLayoutPanel> da **caixa de ferramentas** para seu formulário.

2. Na **caixa de ferramentas**, clique no ícone controle de <xref:System.Windows.Forms.Button>. Não o arraste para o formulário.

3. Mova o ponteiro do mouse sobre o controle de <xref:System.Windows.Forms.TableLayoutPanel>. Observe que o ponteiro muda para um cruz com o ícone de controle de <xref:System.Windows.Forms.Button> anexado.

4. Clique e mantenha o botão do mouse pressionado.

5. Arraste o ponteiro do mouse para desenhar a estrutura de tópicos do controle de <xref:System.Windows.Forms.Button>. Quando estiver satisfeito com o tamanho, solte o botão do mouse. Observe que o controle de <xref:System.Windows.Forms.Button> é criado na célula em que você desenhou a estrutura de tópicos do controle.

## <a name="multiple-controls-within-cells-are-not-permitted"></a>Vários controles dentro de células não são permitidos

O controle <xref:System.Windows.Forms.TableLayoutPanel> pode conter apenas um controle filho por célula.

#### <a name="to-demonstrate-that-multiple-controls-within-cells-are-not-permitted"></a>Para demonstrar que vários controles dentro de células não são permitidos

- Arraste um controle de <xref:System.Windows.Forms.Button> da **caixa de ferramentas** para o controle de <xref:System.Windows.Forms.TableLayoutPanel> e solte-o em uma das células ocupadas. Observe que o controle de <xref:System.Windows.Forms.TableLayoutPanel> não permite que você descarte o controle de <xref:System.Windows.Forms.Button> na célula ocupada.

## <a name="swapping-controls"></a>Trocando controles

O controle <xref:System.Windows.Forms.TableLayoutPanel> permite que você troque os controles que ocupam duas células diferentes.

#### <a name="to-swap-controls"></a>Para trocar controles

- Arraste um dos controles <xref:System.Windows.Forms.Button> de uma célula ocupada e solte-o em outra célula ocupada. Observe que os dois controles são movidos de uma célula para a outra.

## <a name="next-steps"></a>Próximas etapas

Você pode obter um layout complexo usando uma combinação de controles e painéis de layout. Sugestões para exploração adicional incluem:

- Tente redimensionar um dos controles de <xref:System.Windows.Forms.Button> para um tamanho maior e observe o efeito no layout.

- Cole uma seleção de vários controles no controle de <xref:System.Windows.Forms.TableLayoutPanel> e observe como os controles são inseridos.

- Os painéis de layout podem conter outros painéis de layout. Experimente soltar um controle de <xref:System.Windows.Forms.TableLayoutPanel> no controle existente.

- Encaixe o controle de <xref:System.Windows.Forms.TableLayoutPanel> no formulário pai. Redimensione o formulário e observe o efeito no layout.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [Passo a passo: organizando controles nos Windows Forms utilizando um FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Instruções passo a passo: organizando controles no Windows Forms usando guias de alinhamento](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [Walkthrough: Criando um formulário redimensionável do Windows para entrada de dados](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))
- [Walkthrough: Criando um formulário do Windows localizável](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100))
- [Práticas recomendadas para o controle TableLayoutPanel](best-practices-for-the-tablelayoutpanel-control.md)
- [Visão geral da propriedade AutoSize](autosize-property-overview.md)
- [Como encaixar controles nos Windows Forms](how-to-dock-controls-on-windows-forms.md)
- [Como ancorar controles no Windows Forms](how-to-anchor-controls-on-windows-forms.md)
- [Passo a passo: definindo o layout de controles dos Windows Forms com preenchimento, margens e a propriedade AutoSize](windows-forms-controls-padding-autosize.md)
