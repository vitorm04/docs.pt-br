---
title: 'Passo a passo: Organizar controles nos Windows Forms usando linhas de alinhamento'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], arranging with snaplines
- snaplines [Windows Forms], arranging Windows Forms controls
- SnapLine class [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d5c9edc7-cf30-4a97-8ebe-201d569340f8
ms.openlocfilehash: 8ac1ba6b8121aabea3c992ca5b943f231fc19ce2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950067"
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-snaplines"></a>Passo a passo: Organizar controles nos Windows Forms usando linhas de alinhamento
O posicionamento exato dos controles no formulário é uma prioridade alta para muitos aplicativos. O Designer de Formulários do Windows fornece várias ferramentas de layout para fazer isso. Uma das mais importantes é o <xref:System.Windows.Forms.Design.Behavior.SnapLine> recurso.

 As guias de alinhamento mostram exatamente onde alinhar os controles com outros controles. Elas também mostram as distâncias recomendadas para as margens entre os controles, conforme é especificado pelas diretrizes da Interface do Usuário do Windows. Para obter detalhes, consulte [User Interface Design and Development](https://go.microsoft.com/FWLink/?LinkId=83878) (Design e desenvolvimento da interface do usuário).

 As guias de alinhamento facilitam o alinhamento dos controles para garantir uma aparência e um comportamento claros e profissionais.

 As tarefas ilustradas neste passo a passo incluem:

- Criação de um projeto dos Windows Forms

- Espaçando e alinhando controles usando guias de alinhamento

- Alinhando às margens do formulário e do contêiner

- Alinhando a controles agrupados

- Usando guias de alinhamento para posicionar um controle descrevendo seu tamanho

- Usando guias de alinhamento ao arrastar um controle da caixa de ferramentas

- Redimensionando controles usando guias de alinhamento

- Alinhando um rótulo a um texto do controle

- Usando guias de alinhamento com navegação do teclado

- Guias de alinhamento e painéis de layout

- Desabilitando guias de alinhamento

 Ao terminar, você terá um entendimento da função de layout desempenhada pelo recurso de guias de alinhamento.

## <a name="creating-the-project"></a>Criando o Projeto
 A primeira etapa é criar o projeto e configurar o formulário.

### <a name="to-create-the-project"></a>Para criar o projeto

1. Crie um projeto de aplicativo baseado no Windows chamado "SnaplineExample" (**arquivo** > **novo** > **projeto** >  **C# Visual** ou **Visual Basic** > **clássico** Desktop > **Windows Forms aplicativo**).

2. Selecione o formulário no Designer de Formulários.

## <a name="spacing-and-aligning-controls-using-snaplines"></a>Espaçando e alinhando controles usando guias de alinhamento
 As guias de alinhamento oferecem uma maneira intuitiva e precisa de alinhar os controles no formulário. Elas aparecem quando você está movendo um controle ou controles selecionados para perto de uma posição que se alinha a outro controle ou conjunto de controles. Sua seleção será "ajustada" para a posição sugerida ao ser movida passando pelos outros controles.

### <a name="to-arrange-controls-using-snaplines"></a>Para organizar os controles usando guias de alinhamento

1. Arraste um <xref:System.Windows.Forms.Button> controle da **caixa de ferramentas** para seu formulário.

2. Mova o <xref:System.Windows.Forms.Button> controle para o canto inferior direito do formulário. Observe que as snaplines que aparecem como <xref:System.Windows.Forms.Button> o controle se aproximam das bordas inferior e direita do formulário. Essas guias de alinhamento exibem a distância recomendada entre as bordas do controle e o formulário.

3. Mova o <xref:System.Windows.Forms.Button> controle em torno das bordas do formulário e observe onde as snaplines são exibidas. Quando tiver terminado, mova o <xref:System.Windows.Forms.Button> controle próximo ao centro do formulário.

4. Arraste outro <xref:System.Windows.Forms.Button> controle da **caixa de ferramentas** para o formulário.

5. Mova o segundo <xref:System.Windows.Forms.Button> controle até que ele seja quase nível com o primeiro. Observe a guia de alinhamento que aparece na linha de base de texto de ambos os botões e observe que o controle que você está movendo se ajusta para uma posição nivelada exatamente com o outro controle.

6. Mova o segundo <xref:System.Windows.Forms.Button> controle até que ele seja posicionado diretamente acima do primeiro. Observe as guias de alinhamento que aparecem ao longo das bordas esquerda e direita de ambos os botões e observe que o controle que você está movendo se ajusta para uma posição alinhada exatamente com o outro controle.

7. Selecione um dos <xref:System.Windows.Forms.Button> controles e mova-o para o outro, até que esteja quase tocando. Observe a guia de alinhamento que aparece entre eles. Essa é a distância recomendada entre as bordas dos controles. Observe também que o controle que você está movendo se encaixa nessa posição.

8. Arraste dois <xref:System.Windows.Forms.Panel> controles da **caixa de ferramentas** para o formulário.

9. Mova um dos <xref:System.Windows.Forms.Panel> controles até que ele seja quase nível com o primeiro. Observe as guias de alinhamento que aparecem ao longo das bordas superior e inferior de ambos os controles e observe que o controle que você está movendo se ajusta para uma posição alinhada exatamente com o outro controle.

## <a name="aligning-to-form-and-container-margins"></a>Alinhando às margens do formulário e do contêiner
 As guias de alinhamento ajudam a alinhar os controles às margens do formulário e do contêiner de uma maneira consistente.

### <a name="to-align-controls-to-form-and-container-margins"></a>Para alinhar controles às margens do formulário e do contêiner

1. Selecione um dos <xref:System.Windows.Forms.Button> controles e mova-o para a borda direita do formulário até que um snapline seja exibido. A distância do snapline da borda direita é a soma da Propriedade do <xref:System.Windows.Forms.Control.Margin%2A> controle e os valores de Propriedade do <xref:System.Windows.Forms.Control.Padding%2A> formulário.

> [!NOTE]
> Se a propriedade do <xref:System.Windows.Forms.Control.Padding%2A> formulário for definida como 0, 0, 0, a designer de formulários do Windows dará ao formulário um <xref:System.Windows.Forms.Control.Padding%2A> valor sombreado de 9, 9, 9, 9. Para substituir esse comportamento, atribua um valor diferente de 0,0,0,0.

1. <xref:System.Windows.Forms.Button> Altere o valor da Propriedade do <xref:System.Windows.Forms.Control.Margin%2A> controle expandindo a <xref:System.Windows.Forms.Control.Margin%2A> entrada na janela **Propriedades** e definindo a <xref:System.Windows.Forms.Padding.All%2A> Propriedade como 0. Para obter detalhes, [consulte Passo a passos: Dispor Windows Forms controles com preenchimento, margens e a propriedade](windows-forms-controls-padding-autosize.md)AutoSize.

2. Mova o <xref:System.Windows.Forms.Button> controle próximo à borda direita do formulário até que um snapline seja exibido. Essa distância agora é fornecida pelo valor da Propriedade do <xref:System.Windows.Forms.Control.Padding%2A> formulário.

3. Arraste um <xref:System.Windows.Forms.GroupBox> controle da **caixa de ferramentas** para seu formulário.

4. <xref:System.Windows.Forms.GroupBox> Altere o valor da Propriedade do <xref:System.Windows.Forms.Control.Padding%2A> controle expandindo a <xref:System.Windows.Forms.Control.Padding%2A> entrada na janela **Propriedades** e definindo a <xref:System.Windows.Forms.Padding.All%2A> Propriedade como 10.

5. Arraste um <xref:System.Windows.Forms.Button> controle da **caixa de ferramentas** para <xref:System.Windows.Forms.GroupBox> o controle.

6. Mova o <xref:System.Windows.Forms.Button> controle próximo à borda direita <xref:System.Windows.Forms.GroupBox> do controle até que um snapline seja exibido. Mova o <xref:System.Windows.Forms.Button> controle dentro do <xref:System.Windows.Forms.GroupBox> controle e observe onde as snaplines são exibidas.

## <a name="aligning-to-grouped-controls"></a>Alinhando a controles agrupados
 Você pode usar snaplines para alinhar controles agrupados, bem como controles dentro <xref:System.Windows.Forms.GroupBox> de um controle.

### <a name="to-align-to-grouped-controls"></a>Para alinhar controles agrupados

1. Selecione dois dos controles no formulário. Mova um pouco a seleção e observe as guias de alinhamento que aparecem entre a seleção e os outros controles.

2. Arraste um <xref:System.Windows.Forms.GroupBox> controle da **caixa de ferramentas** para seu formulário.

3. Arraste um <xref:System.Windows.Forms.Button> controle da **caixa de ferramentas** para <xref:System.Windows.Forms.GroupBox> o controle.

4. Selecione um dos <xref:System.Windows.Forms.Button> controles e mova-o para o <xref:System.Windows.Forms.GroupBox> controle. Observe as snaplines que aparecem nas bordas do <xref:System.Windows.Forms.GroupBox> controle. Observe também as snaplines que aparecem nas bordas do <xref:System.Windows.Forms.Button> controle que estão contidas <xref:System.Windows.Forms.GroupBox> no controle. Os controles que são filhos de uma caixa de controles também dão suporte a guias de alinhamento.

## <a name="using-snaplines-to-place-a-control-by-outlining-its-size"></a>Usando guias de alinhamento para posicionar um controle descrevendo seu tamanho
 As guias de alinhamento ajudam a alinhar os controles quando você os coloca em um formulário pela primeira vez.

### <a name="to-use-snaplines-to-place-a-control-by-outlining-its-size"></a>Para usar guias de alinhamento para posicionar um controle descrevendo seu tamanho

1. Na **caixa de ferramentas**, clique <xref:System.Windows.Forms.Button> no ícone de controle. Não o arraste para o formulário.

2. Mova o ponteiro do mouse sobre a superfície de design do formulário. Observe que o ponteiro muda para um cruzado com <xref:System.Windows.Forms.Button> o ícone de controle anexado. Observe também as snaplines que parecem sugerir posições alinhadas para o <xref:System.Windows.Forms.Button> controle.

3. Clique e mantenha o botão do mouse pressionado.

4. Arraste o ponteiro do mouse sobre o formulário. Observe que uma estrutura de tópicos é desenhada, indicando a posição e o tamanho do controle.

5. Arraste o ponteiro até que ele se alinhe com o outro controle no formulário. Observe que aparece uma guia de alinhamento para indicar o alinhamento.

6. Solte o botão do mouse. O controle é criado com a posição e com o tamanho indicados pela estrutura de tópicos.

## <a name="using-snaplines-when-dragging-a-control-from-the-toolbox"></a>Usando guias de alinhamento ao arrastar um controle da caixa de ferramentas
 As guias de alinhamento ajudam a alinhar os controles quando você os arrasta da **Caixa de ferramentas** para seu formulário.

### <a name="to-use-snaplines-when-dragging-a-control-from-the-toolbox"></a>Para usar guias de alinhamento ao arrastar um controle da caixa de ferramentas

1. Arraste um <xref:System.Windows.Forms.Button> controle da **caixa de ferramentas** para seu formulário, mas não solte o botão do mouse.

2. Mova o ponteiro do mouse sobre a superfície de design do formulário. Observe que o ponteiro muda para indicar a posição na qual o novo <xref:System.Windows.Forms.Button> controle será criado.

3. Arraste o ponteiro do mouse sobre o formulário. Observe as snaplines que parecem sugerir posições alinhadas para o <xref:System.Windows.Forms.Button> controle. Localize uma posição que esteja alinhada com outros controles.

4. Solte o botão do mouse. O controle é criado na posição indicada pela guia de alinhamento.

## <a name="resizing-controls-using-snaplines"></a>Redimensionando controles usando guias de alinhamento
 As guias de alinhamento ajudam a alinhar os controles à medida que você os redimensiona.

### <a name="to-resize-a-control-using-snaplines"></a>Para redimensionar um controle usando guias de alinhamento

1. Arraste um <xref:System.Windows.Forms.Button> controle da **caixa de ferramentas** para seu formulário.

2. Redimensione o <xref:System.Windows.Forms.Button> controle capturando uma das alças de dimensionamento de canto e arrastando. Para obter detalhes, confira [Como: Redimensionar controles em](how-to-resize-controls-on-windows-forms.md)Windows Forms.

3. Arraste a alça de dimensionamento até que <xref:System.Windows.Forms.Button> uma das bordas do controle seja alinhada com outro controle. Observe que uma guia de alinhamento aparece. Observe também que a alça de dimensionamento se encaixa na posição indicada pela guia de alinhamento.

4. Redimensione o <xref:System.Windows.Forms.Button> controle em direções diferentes e alinhe o identificador de dimensionamento a controles diferentes. Observe como as guias de alinhamento aparecem em várias orientações para indicar o alinhamento.

## <a name="aligning-a-label-to-a-controls-text"></a>Alinhando um rótulo a um texto do controle
 Alguns controles oferecem uma guia de alinhamento para alinhar outros controles ao texto exibido.

### <a name="to-align-a-label-to-a-controls-text"></a>Para alinhar um rótulo a um texto do controle

1. Arraste um <xref:System.Windows.Forms.TextBox> controle da **caixa de ferramentas** para seu formulário. Ao soltar o <xref:System.Windows.Forms.TextBox> controle no formulário, clique no glifo de marca inteligente e selecione a opção **definir texto como TextBox1** . Para obter detalhes, [consulte Passo a passos: Executar tarefas comuns usando marcas inteligentes em controles](performing-common-tasks-using-smart-tags-on-wf-controls.md)de Windows Forms.

2. Arraste um <xref:System.Windows.Forms.Label> controle da **caixa de ferramentas** para seu formulário.

3. Altere o valor da propriedade <xref:System.Windows.Forms.Label> do controle <xref:System.Windows.Forms.Control.AutoSize%2A> para `true`. Observe que as bordas do controle são ajustadas para se ajustar ao texto de exibição.

4. Mova o <xref:System.Windows.Forms.Label> controle para a esquerda <xref:System.Windows.Forms.TextBox> do controle, para que ele seja alinhado com <xref:System.Windows.Forms.TextBox> a borda inferior do controle. Observe a guia de alinhamento que aparece ao longo das bordas inferiores dos dois controles.

5. Mova o <xref:System.Windows.Forms.Label> controle ligeiramente para cima, até <xref:System.Windows.Forms.Label> que o texto <xref:System.Windows.Forms.TextBox> e o texto sejam alinhados. Observe a guia de alinhamento com um estilo diferente que aparece, indicando quando os campos de texto de ambos os controles estão alinhados.

## <a name="using-snaplines-with-keyboard-navigation"></a>Usando guias de alinhamento com navegação do teclado
 As guias de alinhamento ajudam a alinhar os controles ao organizá-los usando as teclas de direção do teclado.

### <a name="to-use-snaplines-with-keyboard-navigation"></a>Para usar guias de alinhamento com navegação do teclado

1. Arraste um <xref:System.Windows.Forms.Button> controle da **caixa de ferramentas** para seu formulário. Coloque-o no canto superior esquerdo do formulário.

2. Pressione CTRL + SETA PARA BAIXO. Observe que o controle se move para baixo no formulário até a primeira posição de alinhamento horizontal disponível.

3. Pressione CTRL + SETA PARA BAIXO até que o controle atinja a parte inferior do formulário. Observe as posições que ele ocupa conforme se move para baixo no formulário.

4. Pressione CTRL + SETA PARA DIREITA. Observe que o controle percorre o formulário até a primeira posição de alinhamento vertical disponível.

5. Pressione CTRL + SETA PARA CIMA até que o controle atinja a lateral do formulário. Observe as posições que ele ocupa conforme se move no formulário.

6. Mova o controle no formulário com uma combinação de teclas de direção. Observe as posições ocupadas pelo controle e as guias de alinhamento que o acompanham.

7. Pressione Shift + qualquer tecla de direção para redimensionar o <xref:System.Windows.Forms.Button> controle por incrementos de um pixel.

8. Pressione Ctrl + Shift + qualquer tecla de direção para redimensionar o <xref:System.Windows.Forms.Button> controle em incrementos de SnapLine.

## <a name="snaplines-and-layout-panels"></a>Guias de alinhamento e painéis de layout
 As guias de alinhamento são desabilitadas em painéis de layout.

### <a name="to-selectively-disable-snaplines"></a>Para desabilitar seletivamente as guias de alinhamento

1. Arraste um <xref:System.Windows.Forms.TableLayoutPanel> controle da **caixa de ferramentas** para seu formulário.

2. Clique duas vezes no <xref:System.Windows.Forms.Button> ícone de controle na **caixa de ferramentas**. Observe que um novo controle de botão aparece na <xref:System.Windows.Forms.TableLayoutPanel> primeira célula do controle.

3. Clique <xref:System.Windows.Forms.Button> duas vezes no ícone de controle na **caixa de ferramentas** duas vezes mais. Isso deixa uma célula vazia no <xref:System.Windows.Forms.TableLayoutPanel> controle.

4. Arraste um <xref:System.Windows.Forms.Button> controle da **caixa de ferramentas** para a célula <xref:System.Windows.Forms.TableLayoutPanel> vazia do controle. Observe que não aparece nenhuma guia de alinhamento.

5. Arraste o <xref:System.Windows.Forms.Button> controle para fora <xref:System.Windows.Forms.TableLayoutPanel> do controle e mova-o para <xref:System.Windows.Forms.TableLayoutPanel> o controle. Observe que as guias de alinhamento aparecem novamente.

## <a name="disabling-snaplines"></a>Desabilitando guias de alinhamento
 As guias de alinhamento são habilitadas por padrão. Você pode desabilitar as guias de alinhamento seletivamente ou desabilitá-las no ambiente de design.

### <a name="to-selectively-disable-snaplines"></a>Para desabilitar seletivamente as guias de alinhamento

- Pressione a tecla ALT enquanto move um controle no formulário.

     Observe que não aparece nenhuma guia de alinhamento e o controle não se ajusta a nenhuma posição de alinhamento possível.

### <a name="to-disable-snaplines-in-the-design-environment"></a>Para desabilitar as guias de alinhamento no ambiente de design

1. No menu **Ferramentas**, abra a caixa de diálogo **Opções**. Abra a caixa de diálogo do Designer de Formulários do Windows. Para obter detalhes, consulte [General, Windows Forms Designer, Options Dialog Box](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/5aazxs78(v=vs.100)) (Designer de Formulários do Windows, caixa de diálogo Opções).

2. Selecione o nó **Geral**. Na seção **Modo de Layout**, altere a seleção de **SnapLines** para **SnapToGrid**.

3. Clique em OK para aplicar a configuração.

4. Selecione um controle no formulário e mova-o em torno dos outros controles. Observe que as guias de alinhamento não aparecem.

## <a name="next-steps"></a>Próximas etapas
 As guias de alinhamento oferecem uma forma intuitiva de alinhar controles no formulário. Sugestões para exploração adicional incluem:

- Tente aninhar um <xref:System.Windows.Forms.GroupBox> controle dentro de <xref:System.Windows.Forms.GroupBox> outro controle. Coloque um <xref:System.Windows.Forms.Button> controle dentro do controle <xref:System.Windows.Forms.GroupBox> filho e outro dentro do controle pai <xref:System.Windows.Forms.GroupBox> . Mova os <xref:System.Windows.Forms.Button> controles para ver como os limites entre contêineres de snaplines.

- Crie uma coluna de <xref:System.Windows.Forms.TextBox> controles e uma coluna de <xref:System.Windows.Forms.Label> controles correspondente. Defina o valor da <xref:System.Windows.Forms.Label> <xref:System.Windows.Forms.Control.AutoSize%2A> propriedade Controls como `true`. Use snaplines para mover os <xref:System.Windows.Forms.Label> controles para que seu texto exibido seja alinhado com o texto <xref:System.Windows.Forms.TextBox> nos controles.

 Para obter informações sobre o design da interface do usuário do Windows, consulte a experiência do usuário do livro *Microsoft Windows, diretrizes oficiais para desenvolvedores e designers de interface do usuário* Redmond, WA: Microsoft Press, 1999. (USBN: 0-7356-0566-1).

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Design.Behavior.SnapLine>
- [Passo a passo: Organizando controles em Windows Forms usando um FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Passo a passo: Organizando controles em Windows Forms usando um TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Passo a passo: Dispor Windows Forms controles com preenchimento, margens e a propriedade AutoSize](windows-forms-controls-padding-autosize.md)
- [Organizando Controles nos Windows Forms](arranging-controls-on-windows-forms.md)
