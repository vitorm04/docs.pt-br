---
title: 'Passo a passo: Organizar controles nos Windows Forms usando linhas de alinhamento'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], arranging with snaplines
- snaplines [Windows Forms], arranging Windows Forms controls
- SnapLine class [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d5c9edc7-cf30-4a97-8ebe-201d569340f8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 83f0365ffb7335cb67c729c5a113e550c119191a
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987002"
---
# <a name="walkthrough-arrange-controls-on-windows-forms-using-snaplines"></a>Passo a passo: Organizar controles em Windows Forms usando Snaplines

O posicionamento exato dos controles no formulário é uma prioridade alta para muitos aplicativos. O Designer de Formulários do Windows fornece várias ferramentas de layout para fazer isso. Uma das mais importantes é o <xref:System.Windows.Forms.Design.Behavior.SnapLine> recurso.

As guias de alinhamento mostram exatamente onde alinhar os controles com outros controles. Eles também mostram as distâncias recomendadas para as margens entre os controles, conforme especificado pelas [diretrizes da interface do usuário do Windows](/windows/win32/uxguide/guidelines).

As guias de alinhamento facilitam o alinhamento dos controles para garantir uma aparência e um comportamento claros e profissionais.

## <a name="create-the-project"></a>Criar o projeto

1. No Visual Studio, crie um projeto de aplicativo baseado no Windows chamado "SnaplineExample".

2. Selecione o formulário no Designer de Formulários.

## <a name="space-and-align-controls"></a>Espaçar e alinhar controles

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

## <a name="align-to-form-and-container-margins"></a>Alinhar às margens do contêiner e do formulário

As guias de alinhamento ajudam a alinhar os controles às margens do formulário e do contêiner de uma maneira consistente.

1. Selecione um dos <xref:System.Windows.Forms.Button> controles e mova-o para a borda direita do formulário até que um snapline seja exibido. A distância do snapline da borda direita é a soma da Propriedade do <xref:System.Windows.Forms.Control.Margin%2A> controle e os valores de Propriedade do <xref:System.Windows.Forms.Control.Padding%2A> formulário.

   > [!NOTE]
   > Se a propriedade do <xref:System.Windows.Forms.Control.Padding%2A> formulário for definida como 0, 0, 0, a designer de formulários do Windows dará ao formulário um <xref:System.Windows.Forms.Control.Padding%2A> valor sombreado de 9, 9, 9, 9. Para substituir esse comportamento, atribua um valor diferente de 0,0,0,0.

2. <xref:System.Windows.Forms.Button> Altere o valor da Propriedade do <xref:System.Windows.Forms.Control.Margin%2A> controle expandindo a <xref:System.Windows.Forms.Control.Margin%2A> entrada na janela **Propriedades** e definindo a <xref:System.Windows.Forms.Padding.All%2A> Propriedade como 0. Para obter detalhes, [consulte Passo a passos: Dispor Windows Forms controles com preenchimento, margens e a propriedade](windows-forms-controls-padding-autosize.md)AutoSize.

3. Mova o <xref:System.Windows.Forms.Button> controle próximo à borda direita do formulário até que um snapline seja exibido. Essa distância agora é fornecida pelo valor da Propriedade do <xref:System.Windows.Forms.Control.Padding%2A> formulário.

4. Arraste um <xref:System.Windows.Forms.GroupBox> controle da **caixa de ferramentas** para seu formulário.

5. <xref:System.Windows.Forms.GroupBox> Altere o valor da Propriedade do <xref:System.Windows.Forms.Control.Padding%2A> controle expandindo a <xref:System.Windows.Forms.Control.Padding%2A> entrada na janela **Propriedades** e definindo a <xref:System.Windows.Forms.Padding.All%2A> Propriedade como 10.

6. Arraste um <xref:System.Windows.Forms.Button> controle da **caixa de ferramentas** para <xref:System.Windows.Forms.GroupBox> o controle.

7. Mova o <xref:System.Windows.Forms.Button> controle próximo à borda direita <xref:System.Windows.Forms.GroupBox> do controle até que um snapline seja exibido. Mova o <xref:System.Windows.Forms.Button> controle dentro do <xref:System.Windows.Forms.GroupBox> controle e observe onde as snaplines são exibidas.

## <a name="align-to-grouped-controls"></a>Alinhar a controles agrupados

Você pode usar snaplines para alinhar controles agrupados, bem como controles dentro <xref:System.Windows.Forms.GroupBox> de um controle.

1. Selecione dois dos controles no formulário. Mova um pouco a seleção e observe as guias de alinhamento que aparecem entre a seleção e os outros controles.

2. Arraste um <xref:System.Windows.Forms.GroupBox> controle da **caixa de ferramentas** para seu formulário.

3. Arraste um <xref:System.Windows.Forms.Button> controle da **caixa de ferramentas** para <xref:System.Windows.Forms.GroupBox> o controle.

4. Selecione um dos <xref:System.Windows.Forms.Button> controles e mova-o para o <xref:System.Windows.Forms.GroupBox> controle. Observe as snaplines que aparecem nas bordas do <xref:System.Windows.Forms.GroupBox> controle. Observe também as snaplines que aparecem nas bordas do <xref:System.Windows.Forms.Button> controle que estão contidas <xref:System.Windows.Forms.GroupBox> no controle. Os controles que são filhos de uma caixa de controles também dão suporte a guias de alinhamento.

## <a name="use-snaplines-to-place-a-control-by-outlining-its-size"></a>Use snaplines para posicionar um controle ao estruturar seu tamanho

1. Na **caixa de ferramentas**, clique <xref:System.Windows.Forms.Button> no ícone de controle. Não o arraste para o formulário.

2. Mova o ponteiro do mouse sobre a superfície de design do formulário. Observe que o ponteiro muda para um cruzado com <xref:System.Windows.Forms.Button> o ícone de controle anexado. Observe também as snaplines que parecem sugerir posições alinhadas para o <xref:System.Windows.Forms.Button> controle.

3. Clique e mantenha o botão do mouse pressionado.

4. Arraste o ponteiro do mouse sobre o formulário. Observe que uma estrutura de tópicos é desenhada, indicando a posição e o tamanho do controle.

5. Arraste o ponteiro até que ele se alinhe com o outro controle no formulário. Observe que aparece uma guia de alinhamento para indicar o alinhamento.

6. Solte o botão do mouse. O controle é criado com a posição e com o tamanho indicados pela estrutura de tópicos.

## <a name="use-snaplines-when-dragging-a-control-from-the-toolbox"></a>Usar snaplines ao arrastar um controle da caixa de ferramentas

1. Arraste um <xref:System.Windows.Forms.Button> controle da **caixa de ferramentas** para seu formulário, mas não solte o botão do mouse.

2. Mova o ponteiro do mouse sobre a superfície de design do formulário. Observe que o ponteiro muda para indicar a posição na qual o novo <xref:System.Windows.Forms.Button> controle será criado.

3. Arraste o ponteiro do mouse sobre o formulário. Observe as snaplines que parecem sugerir posições alinhadas para o <xref:System.Windows.Forms.Button> controle. Localize uma posição que esteja alinhada com outros controles.

4. Solte o botão do mouse. O controle é criado na posição indicada pela guia de alinhamento.

## <a name="resize-a-control-using-snaplines"></a>Redimensionar um controle usando Snaplines

1. Arraste um <xref:System.Windows.Forms.Button> controle da **caixa de ferramentas** para seu formulário.

2. Redimensione o <xref:System.Windows.Forms.Button> controle capturando uma das alças de dimensionamento de canto e arrastando. Para obter detalhes, confira [Como: Redimensionar controles em](how-to-resize-controls-on-windows-forms.md)Windows Forms.

3. Arraste a alça de dimensionamento até que <xref:System.Windows.Forms.Button> uma das bordas do controle seja alinhada com outro controle. Observe que uma guia de alinhamento aparece. Observe também que a alça de dimensionamento se encaixa na posição indicada pela guia de alinhamento.

4. Redimensione o <xref:System.Windows.Forms.Button> controle em direções diferentes e alinhe o identificador de dimensionamento a controles diferentes. Observe como as guias de alinhamento aparecem em várias orientações para indicar o alinhamento.

## <a name="align-a-label-to-a-controls-text"></a>Alinhar um rótulo ao texto de um controle

1. Arraste um <xref:System.Windows.Forms.TextBox> controle da **caixa de ferramentas** para seu formulário. Ao soltar o <xref:System.Windows.Forms.TextBox> controle no formulário, clique no glifo de marca inteligente e selecione a opção **definir texto como TextBox1** . Para obter detalhes, [consulte Passo a passos: Executar tarefas comuns usando marcas inteligentes em controles](performing-common-tasks-using-smart-tags-on-wf-controls.md)de Windows Forms.

2. Arraste um <xref:System.Windows.Forms.Label> controle da **caixa de ferramentas** para seu formulário.

3. Altere o valor da propriedade <xref:System.Windows.Forms.Label> do controle <xref:System.Windows.Forms.Control.AutoSize%2A> para `true`. Observe que as bordas do controle são ajustadas para se ajustar ao texto de exibição.

4. Mova o <xref:System.Windows.Forms.Label> controle para a esquerda <xref:System.Windows.Forms.TextBox> do controle, para que ele seja alinhado com <xref:System.Windows.Forms.TextBox> a borda inferior do controle. Observe a guia de alinhamento que aparece ao longo das bordas inferiores dos dois controles.

5. Mova o <xref:System.Windows.Forms.Label> controle ligeiramente para cima, até <xref:System.Windows.Forms.Label> que o texto <xref:System.Windows.Forms.TextBox> e o texto sejam alinhados. Observe a guia de alinhamento com um estilo diferente que aparece, indicando quando os campos de texto de ambos os controles estão alinhados.

## <a name="use-snaplines-with-keyboard-navigation"></a>Usar snaplines com navegação por teclado

1. Arraste um <xref:System.Windows.Forms.Button> controle da **caixa de ferramentas** para seu formulário. Coloque-o no canto superior esquerdo do formulário.

2. Pressione **Ctrl**+**seta para baixo**. Observe que o controle se move para baixo no formulário até a primeira posição de alinhamento horizontal disponível.

3. Pressione **Ctrl**+**seta para baixo** até que o controle atinja a parte inferior do formulário. Observe as posições que ele ocupa conforme se move para baixo no formulário.

4. Pressione **Ctrl**+**seta para a direita**. Observe que o controle percorre o formulário até a primeira posição de alinhamento vertical disponível.

5. Pressione **Ctrl**+**seta para a direita** até que o controle atinja o lado do formulário. Observe as posições que ele ocupa conforme se move no formulário.

6. Mova o controle no formulário com uma combinação de teclas de direção. Observe as posições ocupadas pelo controle e as guias de alinhamento que o acompanham.

7. Pressione+**as teclas de seta** Shift para <xref:System.Windows.Forms.Button> redimensionar o controle por incrementos de um pixel.

8. Pressione**as teclas** <xref:System.Windows.Forms.Button> **Ctrl**+**Shift**+seta para redimensionar o controle em incrementos de SnapLine.

## <a name="selectively-disable-snaplines"></a>Desabilitar seletivamente as snaplines

1. Arraste um <xref:System.Windows.Forms.TableLayoutPanel> controle da **caixa de ferramentas** para seu formulário.

2. Clique duas vezes no <xref:System.Windows.Forms.Button> ícone de controle na **caixa de ferramentas**. Observe que um novo controle de botão aparece na <xref:System.Windows.Forms.TableLayoutPanel> primeira célula do controle.

3. Clique <xref:System.Windows.Forms.Button> duas vezes no ícone de controle na **caixa de ferramentas** duas vezes mais. Isso deixa uma célula vazia no <xref:System.Windows.Forms.TableLayoutPanel> controle.

4. Arraste um <xref:System.Windows.Forms.Button> controle da **caixa de ferramentas** para a célula <xref:System.Windows.Forms.TableLayoutPanel> vazia do controle. Observe que não aparece nenhuma guia de alinhamento.

5. Arraste o <xref:System.Windows.Forms.Button> controle para fora <xref:System.Windows.Forms.TableLayoutPanel> do controle e mova-o para <xref:System.Windows.Forms.TableLayoutPanel> o controle. Observe que as guias de alinhamento aparecem novamente.

## <a name="disable-snaplines"></a>Desabilitar snaplines

Pressione a tecla **ALT** e, ao mover um controle em todo o formulário.

Nenhuma SnapLine é exibida e o controle não se ajusta a nenhuma posição de alinhamento em potencial.

### <a name="to-disable-snaplines-in-the-design-environment"></a>Para desabilitar as guias de alinhamento no ambiente de design

1. No menu **Ferramentas**, abra a caixa de diálogo **Opções**. Selecione **Designer de formulários do Windows**.

2. Selecione o nó **Geral**. Na seção **Modo de Layout**, altere a seleção de **SnapLines** para **SnapToGrid**.

3. Selecione **OK** para aplicar a configuração.

4. Selecione um controle no formulário e mova-o em torno dos outros controles. Observe que as guias de alinhamento não aparecem.

## <a name="next-steps"></a>Próximas etapas

As guias de alinhamento oferecem uma forma intuitiva de alinhar controles no formulário. Sugestões para exploração adicional incluem:

- Tente aninhar um <xref:System.Windows.Forms.GroupBox> controle dentro de <xref:System.Windows.Forms.GroupBox> outro controle. Coloque um <xref:System.Windows.Forms.Button> controle dentro do controle <xref:System.Windows.Forms.GroupBox> filho e outro dentro do controle pai <xref:System.Windows.Forms.GroupBox> . Mova os <xref:System.Windows.Forms.Button> controles para ver como os limites entre contêineres de snaplines.

- Crie uma coluna de <xref:System.Windows.Forms.TextBox> controles e uma coluna de <xref:System.Windows.Forms.Label> controles correspondente. Defina o valor da <xref:System.Windows.Forms.Label> <xref:System.Windows.Forms.Control.AutoSize%2A> propriedade Controls como `true`. Use snaplines para mover os <xref:System.Windows.Forms.Label> controles para que seu texto exibido seja alinhado com o texto <xref:System.Windows.Forms.TextBox> nos controles.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Design.Behavior.SnapLine>
- [Passo a passo: Organizando controles em Windows Forms usando um FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Passo a passo: Organizando controles em Windows Forms usando um TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Passo a passo: Dispor Windows Forms controles com preenchimento, margens e a propriedade AutoSize](windows-forms-controls-padding-autosize.md)
