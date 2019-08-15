---
title: 'Passo a passo: Organizar controles nos Windows Forms usando um TableLayoutPanel'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], arranging with TableLayoutPanel
- TableLayoutPanel control [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d474885e-12cc-4ab7-b997-2a23a643049b
ms.openlocfilehash: 7566f19282ffd5a3cac86693a64899f25ce37b9f
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040287"
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel"></a>Passo a passo: Organizar controles nos Windows Forms usando um TableLayoutPanel

Alguns aplicativos exigem um formulário com um layout que se organiza adequadamente à medida que o formulário é redimensionado ou conforme o tamanho do conteúdo é alterado. Quando você precisar de um layout dinâmico e não quiser manipular <xref:System.Windows.Forms.Control.Layout> eventos explicitamente em seu código, considere o uso de um painel de layout.

O <xref:System.Windows.Forms.FlowLayoutPanel> controle e o <xref:System.Windows.Forms.TableLayoutPanel> controle fornecem maneiras intuitivas de organizar controles em seu formulário. Ambos fornecem uma capacidade automática e configurável de controlar as posições relativas dos controles filho contidos neles e ambos oferecem recursos de layout dinâmico em tempo de execução, para que eles possam redimensionar e reposicionar os controles filho conforme as dimensões do formulário pai se alteram. Os painéis de layout podem ser aninhados em painéis de layout, para permitir a realização de interfaces do usuário sofisticadas.

O <xref:System.Windows.Forms.FlowLayoutPanel> organiza seu conteúdo em uma direção de fluxo específica: horizontal ou vertical. Seu conteúdo pode ser encapsulado de uma linha à outra ou de uma coluna à próxima. Como alternativa, seu conteúdo pode ser recortado, em vez de encapsulado. Para obter mais informações, confira [Passo a passo: Organizando controles em Windows Forms usando um FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md).

O <xref:System.Windows.Forms.TableLayoutPanel> organiza seu conteúdo em uma grade, fornecendo uma funcionalidade semelhante à tabela HTML \<> elemento. O <xref:System.Windows.Forms.TableLayoutPanel> controle permite colocar controles em um layout de grade sem exigir que você especifique precisamente a posição de cada controle individual. Suas células são organizadas em linhas e colunas, que podem ter diferentes tamanhos. As células podem ser mescladas entre linhas e colunas. As células podem conter qualquer coisa que um formulário pode conter e se comportam, na maioria de outros aspectos, como contêineres.

O <xref:System.Windows.Forms.TableLayoutPanel> controle também fornece uma capacidade de redimensionamento proporcional em tempo de execução, de modo que o layout pode ser alterado sem problemas à medida que seu formulário é redimensionado. Isso torna o <xref:System.Windows.Forms.TableLayoutPanel> controle bem adequado para fins como formulários de entrada de dados e aplicativos localizados. Para obter mais informações, confira [Passo a passo: Criação de um formulário redimensionável do Windows](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100)) para [entrada de dados e passo a passos: Criar um Windows Form](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100))localizável.

Em geral, você não deve usar um <xref:System.Windows.Forms.TableLayoutPanel> controle como um contêiner para todo o layout. Use <xref:System.Windows.Forms.TableLayoutPanel> controles para fornecer recursos de redimensionamento proporcional a partes do layout.

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

1. Crie um projeto de aplicativo do Windows chamado "TableLayoutPanelExample". Para obter mais informações, confira [Como: Crie um projeto](/visualstudio/ide/step-1-create-a-windows-forms-application-project) de aplicativo Windows Forms.

2. Selecione o formulário no **Designer de Formulários** **do Windows**.

## <a name="arranging-controls-in-rows-and-columns"></a>Organização de controles em linhas e colunas

O <xref:System.Windows.Forms.TableLayoutPanel> controle permite que você organize facilmente os controles em linhas e colunas.

#### <a name="to-arrange-controls-in-rows-and-columns-using-a-tablelayoutpanel"></a>Para organizar controles em linhas e colunas utilizando um TableLayoutPanel

1. Arraste um <xref:System.Windows.Forms.TableLayoutPanel> controle da **caixa de ferramentas** para seu formulário. Observe que, por padrão, o <xref:System.Windows.Forms.TableLayoutPanel> controle tem quatro células.

2. Arraste um <xref:System.Windows.Forms.Button> controle da **caixa de ferramentas** para <xref:System.Windows.Forms.TableLayoutPanel> o controle e solte-o em uma das células. Observe que o <xref:System.Windows.Forms.Button> controle é criado dentro da célula que você selecionou.

3. Arraste mais <xref:System.Windows.Forms.Button> três controles da **caixa de ferramentas** para <xref:System.Windows.Forms.TableLayoutPanel> o controle, para que cada célula contenha um botão.

4. Pegue na alça de dimensionamento vertical entre as duas colunas e mova-a para a esquerda. Observe que os <xref:System.Windows.Forms.Button> controles na primeira coluna são redimensionados para uma largura menor, enquanto o <xref:System.Windows.Forms.Button> tamanho dos controles na segunda coluna é inalterado.

5. Pegue na alça de dimensionamento vertical entre as duas colunas e mova-a para a direita. Observe que os <xref:System.Windows.Forms.Button> controles na primeira coluna retornam ao seu tamanho original, enquanto os <xref:System.Windows.Forms.Button> controles na segunda coluna são movidos para a direita.

6. Mova a alça de dimensionamento horizontal para cima e para baixo para ver o efeito sobre os controles no painel.

## <a name="positioning-controls-within-cells-using-docking-and-anchoring"></a>Posicionando controles dentro de células usando o encaixe e a ancoragem

O comportamento de ancoragem dos controles filho em <xref:System.Windows.Forms.TableLayoutPanel> um difere do comportamento em outros controles de contêiner. O comportamento de ancoragem de controles filho é igual a outras caixas de controles.

#### <a name="positioning-controls-within-cells"></a>Posicionando controles em células

1. Selecione o primeiro <xref:System.Windows.Forms.Button> controle. Altere o valor de sua <xref:System.Windows.Forms.Control.Dock%2A> propriedade para <xref:System.Windows.Forms.DockStyle.Fill>. Observe que o <xref:System.Windows.Forms.Button> controle se expande para preencher sua célula.

2. Selecione um dos outros <xref:System.Windows.Forms.Button> controles. Altere o valor de sua <xref:System.Windows.Forms.Control.Anchor%2A> propriedade para <xref:System.Windows.Forms.AnchorStyles.Right>. Observe que ele é movido para que sua borda direita fique próxima à borda direita da célula. A distância entre as bordas é a soma da <xref:System.Windows.Forms.Button> Propriedade do <xref:System.Windows.Forms.Control.Margin%2A> controle e da Propriedade do <xref:System.Windows.Forms.Control.Padding%2A> painel.

3. Altere <xref:System.Windows.Forms.Button> o valor da Propriedade do <xref:System.Windows.Forms.Control.Anchor%2A> controle para <xref:System.Windows.Forms.AnchorStyles.Right> e <xref:System.Windows.Forms.AnchorStyles.Left>. Observe que o controle é dimensionado para a largura da célula, com os <xref:System.Windows.Forms.Control.Margin%2A> valores e <xref:System.Windows.Forms.Control.Padding%2A> levados em conta.

4. Repita as etapas 2 e 3 com <xref:System.Windows.Forms.AnchorStyles.Top> os <xref:System.Windows.Forms.AnchorStyles.Bottom> estilos e.

## <a name="setting-row-and-column-properties"></a>Configuração de propriedades de linha e coluna

Você pode definir propriedades individuais de linhas e colunas usando as <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> coleções e. <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A>

#### <a name="to-set-row-and-column-properties"></a>Para definir as propriedades de linha e coluna

1. Selecione o <xref:System.Windows.Forms.TableLayoutPanel> controle na **Designer de formulários do Windows**.

2. Nas janelas **Propriedades** , abra a <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> coleção clicando nas reticências (![o botão de reticências (...) no botão janela Propriedades do Visual Studio](./media/visual-studio-ellipsis-button.png).) ao lado da entrada **colunas** .

3. Selecione a primeira coluna e altere o valor de sua <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> propriedade para <xref:System.Windows.Forms.SizeType.AutoSize>. Clique em **OK** para aceitar a alteração. Observe que a largura da primeira coluna é reduzida para se ajustar <xref:System.Windows.Forms.Button> ao controle. Observe também que a largura da coluna não é redimensionável.

4. Na janela **Propriedades** , abra a <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> coleção e selecione a primeira coluna. Altere o valor de sua <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> propriedade para <xref:System.Windows.Forms.SizeType.Percent>. Clique em **OK** para aceitar a alteração. Redimensione o <xref:System.Windows.Forms.TableLayoutPanel> controle para uma largura maior e observe que a largura da primeira coluna se expande. Redimensione o <xref:System.Windows.Forms.TableLayoutPanel> controle para uma largura menor e observe que os botões na primeira coluna são dimensionados para caber na célula. Observe também que a largura da coluna é redimensionável.

5. Na janela **Propriedades** , abra a <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> coleção e selecione todas as colunas listadas. Defina o valor de cada <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> Propriedade como <xref:System.Windows.Forms.SizeType.Percent>. Clique em **OK** para aceitar a alteração. Repita com a <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> coleção.

6. Pegue um dos identificadores de redimensionamento de canto e redimensione a <xref:System.Windows.Forms.TableLayoutPanel> largura e a altura do controle. Observe que as linhas e colunas são redimensionadas conforme o <xref:System.Windows.Forms.TableLayoutPanel> tamanho do controle é alterado. Observe também que as linhas e colunas são redimensionáveis com as alças de dimensionamento horizontal e vertical.

## <a name="spanning-rows-and-columns-with-a-control"></a>Extensão de linhas e colunas com um controle

O <xref:System.Windows.Forms.TableLayoutPanel> controle adiciona várias novas propriedades a controles em tempo de design. Duas dessas propriedades são a `RowSpan` e `ColumnSpan`. Você pode usar essas propriedades para fazer um controle estender-se por mais de uma linha ou coluna.

#### <a name="to-span-rows-and-columns-with-a-control"></a>Para estender linhas e colunas com um controle

1. Selecione o <xref:System.Windows.Forms.Button> controle na primeira linha e na primeira coluna.

2. Na janela **Propriedades**, altere o valor da propriedade `ColumnSpan` para **2**. Observe que o <xref:System.Windows.Forms.Button> controle preenche a primeira coluna e a segunda coluna. Observe também que uma linha extra foi adicionada para acomodar essa alteração.

3. Repita a etapa 2 para a propriedade `RowSpan`.

## <a name="inserting-controls-by-double-clicking-them-in-the-toolbox"></a>Inserindo controles ao clicar duas vezes neles na caixa de ferramentas

Você pode preencher seu <xref:System.Windows.Forms.TableLayoutPanel> controle clicando duas vezes em controles na **caixa de ferramentas**.

#### <a name="to-insert-controls-by-double-clicking-in-the-toolbox"></a>Para inserir controles clicando duas vezes na caixa de ferramentas

1. Arraste um <xref:System.Windows.Forms.TableLayoutPanel> controle da **caixa de ferramentas** para seu formulário.

2. Clique duas vezes no <xref:System.Windows.Forms.Button> ícone de controle na **caixa de ferramentas**. Observe que um novo controle de botão aparece na <xref:System.Windows.Forms.TableLayoutPanel> primeira célula do controle.

3. Clique duas vezes em vários outros controles na **Caixa de ferramentas**. Observe que os novos controles aparecem sucessivamente nas <xref:System.Windows.Forms.TableLayoutPanel> células desocupadas do controle. Observe também que o <xref:System.Windows.Forms.TableLayoutPanel> controle se expande para acomodar os novos controles se nenhuma célula aberta estiver disponível.

## <a name="automatic-handling-of-overflows"></a>Manipulação automática de estouros

Quando você estiver inserindo controles no <xref:System.Windows.Forms.TableLayoutPanel> controle, poderá ficar sem células vazias para seus novos controles. O <xref:System.Windows.Forms.TableLayoutPanel> controle manipula essa situação automaticamente aumentando o número de células.

#### <a name="to-observe-automatic-handling-of-overflows"></a>Observar a manipulação automática de estouros

1. Se ainda houver células vazias no <xref:System.Windows.Forms.TableLayoutPanel> controle, continue a inserir novos <xref:System.Windows.Forms.Button> controles até que o <xref:System.Windows.Forms.TableLayoutPanel> controle esteja cheio.

2. Quando o <xref:System.Windows.Forms.TableLayoutPanel> controle estiver cheio <xref:System.Windows.Forms.Button> , clique duas vezes no ícone na **caixa de ferramentas** para inserir <xref:System.Windows.Forms.Button> outro controle. Observe que o <xref:System.Windows.Forms.TableLayoutPanel> controle cria novas células para acomodar o novo controle. Insira mais alguns controles e observe o comportamento de redimensionamento.

3. Altere o valor da <xref:System.Windows.Forms.TableLayoutPanel> Propriedade do <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> controle para <xref:System.Windows.Forms.TableLayoutPanelGrowStyle.FixedSize>. Clique <xref:System.Windows.Forms.Button> duas vezes no ícone na **caixa de ferramentas** para <xref:System.Windows.Forms.Button> inserir controles até <xref:System.Windows.Forms.TableLayoutPanel> que o controle esteja cheio. Clique <xref:System.Windows.Forms.Button> duas vezes no ícone na **caixa de ferramentas** novamente. Observe que você receberá uma mensagem de erro do **Designer de Formulários do Windows**, informando que não possível criar mais linhas e colunas.

## <a name="inserting-a-control-by-drawing-its-outline"></a>Inserindo um controle ao desenhar seu contorno

Você pode inserir um controle em um <xref:System.Windows.Forms.TableLayoutPanel> controle e especificar seu tamanho desenhando seu contorno em uma célula.

#### <a name="to-insert-a-control-by-drawing-its-outline"></a>Para inserir um controle desenhando seu contorno

1. Arraste um <xref:System.Windows.Forms.TableLayoutPanel> controle da **caixa de ferramentas** para seu formulário.

2. Na **caixa de ferramentas**, clique <xref:System.Windows.Forms.Button> no ícone de controle. Não o arraste para o formulário.

3. Mova o ponteiro do mouse sobre <xref:System.Windows.Forms.TableLayoutPanel> o controle. Observe que o ponteiro muda para um cruzado com <xref:System.Windows.Forms.Button> o ícone de controle anexado.

4. Clique e mantenha o botão do mouse pressionado.

5. Arraste o ponteiro do mouse para desenhar a estrutura de <xref:System.Windows.Forms.Button> tópicos do controle. Quando estiver satisfeito com o tamanho, solte o botão do mouse. Observe que o <xref:System.Windows.Forms.Button> controle é criado na célula em que você desenhou a estrutura de tópicos do controle.

## <a name="multiple-controls-within-cells-are-not-permitted"></a>Vários controles dentro de células não são permitidos

O <xref:System.Windows.Forms.TableLayoutPanel> controle pode conter apenas um controle filho por célula.

#### <a name="to-demonstrate-that-multiple-controls-within-cells-are-not-permitted"></a>Para demonstrar que vários controles dentro de células não são permitidos

- Arraste um <xref:System.Windows.Forms.Button> controle da **caixa de ferramentas** para <xref:System.Windows.Forms.TableLayoutPanel> o controle e solte-o em uma das células ocupadas. Observe que o <xref:System.Windows.Forms.TableLayoutPanel> controle não permite que você descarte o <xref:System.Windows.Forms.Button> controle na célula ocupada.

## <a name="swapping-controls"></a>Trocando controles

O <xref:System.Windows.Forms.TableLayoutPanel> controle permite que você troque os controles que ocupam duas células diferentes.

#### <a name="to-swap-controls"></a>Para trocar controles

- Arraste um dos controles <xref:System.Windows.Forms.Button> de uma célula ocupada e solte-o em outra célula ocupada. Observe que os dois controles são movidos de uma célula para a outra.

## <a name="next-steps"></a>Próximas etapas

Você pode obter um layout complexo usando uma combinação de controles e painéis de layout. Sugestões para exploração adicional incluem:

- Tente redimensionar um dos <xref:System.Windows.Forms.Button> controles para um tamanho maior e observe o efeito no layout.

- Cole uma seleção de vários controles no <xref:System.Windows.Forms.TableLayoutPanel> controle e observe como os controles são inseridos.

- Os painéis de layout podem conter outros painéis de layout. Experimente soltar um <xref:System.Windows.Forms.TableLayoutPanel> controle no controle existente.

- Encaixar o <xref:System.Windows.Forms.TableLayoutPanel> controle no formulário pai. Redimensione o formulário e observe o efeito no layout.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [Passo a passo: Organizando controles em Windows Forms usando um FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Passo a passo: Organizando controles em Windows Forms usando Snaplines](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [Microsoft Windows User Experience, Official Guidelines for User Interface Developers and Designers (Experiência do usuário do Microsoft Windows, diretrizes oficiais para desenvolvedores e designers da interface do usuário). Redmond, WA: Microsoft Press, 1999. (USBN: 0-7356-0566-1)](https://www.microsoft.com/mspress/southpacific/books/book11588.htm)
- [Passo a passo: Criando um formulário redimensionável do Windows para entrada de dados](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))
- [Passo a passo: Criando um formulário do Windows localizável](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100))
- [Práticas recomendadas para o controle TableLayoutPanel](best-practices-for-the-tablelayoutpanel-control.md)
- [Visão geral da propriedade AutoSize](autosize-property-overview.md)
- [Como: Encaixar controles em Windows Forms](how-to-dock-controls-on-windows-forms.md)
- [Como: Controles de ancoragem em Windows Forms](how-to-anchor-controls-on-windows-forms.md)
- [Passo a passo: Dispor Windows Forms controles com preenchimento, margens e a propriedade AutoSize](windows-forms-controls-padding-autosize.md)
