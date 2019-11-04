---
title: 'Instruções passo a passo: organizando controles nos Windows Forms usando linhas de alinhamento'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], arranging with snaplines
- snaplines [Windows Forms], arranging Windows Forms controls
- SnapLine class [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d5c9edc7-cf30-4a97-8ebe-201d569340f8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 04bef7162662f4fbefdaa151de13468d88530914
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460647"
---
# <a name="walkthrough-arrange-controls-on-windows-forms-using-snaplines"></a>Walkthrough: organizar controles em Windows Forms usando Snaplines

O posicionamento exato dos controles no formulário é uma prioridade alta para muitos aplicativos. O Designer de Formulários do Windows fornece várias ferramentas de layout para fazer isso. Uma das mais importantes é o recurso <xref:System.Windows.Forms.Design.Behavior.SnapLine>.

As guias de alinhamento mostram exatamente onde alinhar os controles com outros controles. Eles também mostram as distâncias recomendadas para as margens entre os controles, conforme especificado pelas [diretrizes da interface do usuário do Windows](/windows/win32/uxguide/guidelines).

As guias de alinhamento facilitam o alinhamento dos controles para garantir uma aparência e um comportamento claros e profissionais.

## <a name="create-the-project"></a>Criar o projeto

1. No Visual Studio, crie um projeto de aplicativo baseado no Windows chamado "SnaplineExample".

2. Selecione o formulário no Designer de Formulários.

## <a name="space-and-align-controls"></a>Espaçar e alinhar controles

As guias de alinhamento oferecem uma maneira intuitiva e precisa de alinhar os controles no formulário. Elas aparecem quando você está movendo um controle ou controles selecionados para perto de uma posição que se alinha a outro controle ou conjunto de controles. Sua seleção será "ajustada" para a posição sugerida ao ser movida passando pelos outros controles.

### <a name="to-arrange-controls-using-snaplines"></a>Para organizar os controles usando guias de alinhamento

1. Arraste um controle de <xref:System.Windows.Forms.Button> da **caixa de ferramentas** para seu formulário.

2. Mova o controle de <xref:System.Windows.Forms.Button> para o canto inferior direito do formulário. Observe que as snaplines que aparecem como o controle de <xref:System.Windows.Forms.Button> se aproximam das bordas inferior e direita do formulário. Essas guias de alinhamento exibem a distância recomendada entre as bordas do controle e o formulário.

3. Mova o controle de <xref:System.Windows.Forms.Button> em torno das bordas do formulário e observe onde as snaplines são exibidas. Quando tiver terminado, mova o controle de <xref:System.Windows.Forms.Button> próximo ao centro do formulário.

4. Arraste outro controle de <xref:System.Windows.Forms.Button> da **caixa de ferramentas** para seu formulário.

5. Mova o segundo controle <xref:System.Windows.Forms.Button> até que ele seja quase nível com o primeiro. Observe a guia de alinhamento que aparece na linha de base de texto de ambos os botões e observe que o controle que você está movendo se ajusta para uma posição nivelada exatamente com o outro controle.

6. Mova o segundo controle de <xref:System.Windows.Forms.Button> até que ele seja posicionado diretamente acima do primeiro. Observe as guias de alinhamento que aparecem ao longo das bordas esquerda e direita de ambos os botões e observe que o controle que você está movendo se ajusta para uma posição alinhada exatamente com o outro controle.

7. Selecione um dos controles de <xref:System.Windows.Forms.Button> e mova-o para o outro, até que esteja quase tocando. Observe a guia de alinhamento que aparece entre eles. Essa é a distância recomendada entre as bordas dos controles. Observe também que o controle que você está movendo se encaixa nessa posição.

8. Arraste dois controles de <xref:System.Windows.Forms.Panel> da **caixa de ferramentas** para seu formulário.

9. Mova um dos controles de <xref:System.Windows.Forms.Panel> até que ele seja quase nível com o primeiro. Observe as guias de alinhamento que aparecem ao longo das bordas superior e inferior de ambos os controles e observe que o controle que você está movendo se ajusta para uma posição alinhada exatamente com o outro controle.

## <a name="align-to-form-and-container-margins"></a>Alinhar às margens do contêiner e do formulário

As guias de alinhamento ajudam a alinhar os controles às margens do formulário e do contêiner de uma maneira consistente.

1. Selecione um dos controles de <xref:System.Windows.Forms.Button> e mova-o para a borda direita do formulário até que um snapline seja exibido. A distância do snapline da borda direita é a soma da propriedade <xref:System.Windows.Forms.Control.Margin%2A> do controle e os valores da propriedade <xref:System.Windows.Forms.Control.Padding%2A> do formulário.

   > [!NOTE]
   > Se a propriedade de <xref:System.Windows.Forms.Control.Padding%2A> do formulário for definida como 0, 0, 0, 0, a Designer de Formulários do Windows dará ao formulário um valor de <xref:System.Windows.Forms.Control.Padding%2A> sombreado de 9, 9, 9, 9. Para substituir esse comportamento, atribua um valor diferente de 0,0,0,0.

2. Altere o valor da propriedade <xref:System.Windows.Forms.Control.Margin%2A> do controle de <xref:System.Windows.Forms.Button> expandindo a entrada <xref:System.Windows.Forms.Control.Margin%2A> na janela **Propriedades** e definindo a propriedade <xref:System.Windows.Forms.Padding.All%2A> como 0. Para obter detalhes, consulte [Instruções passo a passo: projetando controles dos Windows Forms com preenchimento, margens e a propriedade AutoSize](windows-forms-controls-padding-autosize.md).

3. Mova o controle de <xref:System.Windows.Forms.Button> próximo à borda direita do formulário até que um snapline seja exibido. Essa distância agora é fornecida pelo valor da propriedade <xref:System.Windows.Forms.Control.Padding%2A> do formulário.

4. Arraste um controle de <xref:System.Windows.Forms.GroupBox> da **caixa de ferramentas** para seu formulário.

5. Altere o valor da propriedade <xref:System.Windows.Forms.Control.Padding%2A> do controle de <xref:System.Windows.Forms.GroupBox> expandindo a entrada <xref:System.Windows.Forms.Control.Padding%2A> na janela **Propriedades** e definindo a propriedade <xref:System.Windows.Forms.Padding.All%2A> como 10.

6. Arraste um controle de <xref:System.Windows.Forms.Button> da **caixa de ferramentas** para o controle de <xref:System.Windows.Forms.GroupBox>.

7. Mova o controle de <xref:System.Windows.Forms.Button> próximo à borda direita do controle <xref:System.Windows.Forms.GroupBox> até que um snapline seja exibido. Mova o controle de <xref:System.Windows.Forms.Button> dentro do controle de <xref:System.Windows.Forms.GroupBox> e observe onde as snaplines são exibidas.

## <a name="align-to-grouped-controls"></a>Alinhar a controles agrupados

Você pode usar snaplines para alinhar controles agrupados, bem como controles dentro de um controle de <xref:System.Windows.Forms.GroupBox>.

1. Selecione dois dos controles no formulário. Mova um pouco a seleção e observe as guias de alinhamento que aparecem entre a seleção e os outros controles.

2. Arraste um controle de <xref:System.Windows.Forms.GroupBox> da **caixa de ferramentas** para seu formulário.

3. Arraste um controle de <xref:System.Windows.Forms.Button> da **caixa de ferramentas** para o controle de <xref:System.Windows.Forms.GroupBox>.

4. Selecione um dos controles de <xref:System.Windows.Forms.Button> e mova-o para o controle de <xref:System.Windows.Forms.GroupBox>. Observe as snaplines que aparecem nas bordas do controle de <xref:System.Windows.Forms.GroupBox>. Observe também as snaplines que aparecem nas bordas do controle de <xref:System.Windows.Forms.Button> que está contido pelo controle de <xref:System.Windows.Forms.GroupBox>. Os controles que são filhos de uma caixa de controles também dão suporte a guias de alinhamento.

## <a name="use-snaplines-to-place-a-control-by-outlining-its-size"></a>Use snaplines para posicionar um controle ao estruturar seu tamanho

1. Na **caixa de ferramentas**, clique no ícone controle de <xref:System.Windows.Forms.Button>. Não o arraste para o formulário.

2. Mova o ponteiro do mouse sobre a superfície de design do formulário. Observe que o ponteiro muda para um cruz com o ícone de controle de <xref:System.Windows.Forms.Button> anexado. Observe também as snaplines que parecem sugerir posições alinhadas para o controle de <xref:System.Windows.Forms.Button>.

3. Clique e mantenha o botão do mouse pressionado.

4. Arraste o ponteiro do mouse sobre o formulário. Observe que uma estrutura de tópicos é desenhada, indicando a posição e o tamanho do controle.

5. Arraste o ponteiro até que ele se alinhe com o outro controle no formulário. Observe que aparece uma guia de alinhamento para indicar o alinhamento.

6. Solte o botão do mouse. O controle é criado com a posição e com o tamanho indicados pela estrutura de tópicos.

## <a name="use-snaplines-when-dragging-a-control-from-the-toolbox"></a>Usar snaplines ao arrastar um controle da caixa de ferramentas

1. Arraste um controle de <xref:System.Windows.Forms.Button> da **caixa de ferramentas** para seu formulário, mas não solte o botão do mouse.

2. Mova o ponteiro do mouse sobre a superfície de design do formulário. Observe que o ponteiro muda para indicar a posição na qual o novo controle de <xref:System.Windows.Forms.Button> será criado.

3. Arraste o ponteiro do mouse sobre o formulário. Observe as snaplines que parecem sugerir posições alinhadas para o controle de <xref:System.Windows.Forms.Button>. Localize uma posição que esteja alinhada com outros controles.

4. Solte o botão do mouse. O controle é criado na posição indicada pela guia de alinhamento.

## <a name="resize-a-control-using-snaplines"></a>Redimensionar um controle usando Snaplines

1. Arraste um controle de <xref:System.Windows.Forms.Button> da **caixa de ferramentas** para seu formulário.

2. Redimensione o controle de <xref:System.Windows.Forms.Button> capturando uma das alças de dimensionamento de canto e arrastando. Para obter detalhes, consulte [Instruções: redimensionar controles nos Windows Forms](how-to-resize-controls-on-windows-forms.md).

3. Arraste a alça de dimensionamento até que uma das bordas do controle de <xref:System.Windows.Forms.Button> esteja alinhada com outro controle. Observe que uma guia de alinhamento aparece. Observe também que a alça de dimensionamento se encaixa na posição indicada pela guia de alinhamento.

4. Redimensione o controle de <xref:System.Windows.Forms.Button> em direções diferentes e alinhe o identificador de dimensionamento a controles diferentes. Observe como as guias de alinhamento aparecem em várias orientações para indicar o alinhamento.

## <a name="align-a-label-to-a-controls-text"></a>Alinhar um rótulo ao texto de um controle

1. Arraste um controle de <xref:System.Windows.Forms.TextBox> da **caixa de ferramentas** para seu formulário. Ao soltar o controle <xref:System.Windows.Forms.TextBox> no formulário, clique no glifo de marca inteligente e selecione a opção **definir texto como TextBox1** . Para obter detalhes, consulte [Instruções passo a passo: realizando tarefas comuns usando smart tags em controles dos Windows Forms](performing-common-tasks-using-smart-tags-on-wf-controls.md).

2. Arraste um controle de <xref:System.Windows.Forms.Label> da **caixa de ferramentas** para seu formulário.

3. Altere o valor da propriedade <xref:System.Windows.Forms.Label> do controle <xref:System.Windows.Forms.Control.AutoSize%2A> para `true`. Observe que as bordas do controle são ajustadas para se ajustar ao texto de exibição.

4. Mova o controle de <xref:System.Windows.Forms.Label> à esquerda do controle de <xref:System.Windows.Forms.TextBox>, para que ele seja alinhado com a borda inferior do controle de <xref:System.Windows.Forms.TextBox>. Observe a guia de alinhamento que aparece ao longo das bordas inferiores dos dois controles.

5. Mova o controle de <xref:System.Windows.Forms.Label> ligeiramente para cima, até que o texto <xref:System.Windows.Forms.Label> e o texto <xref:System.Windows.Forms.TextBox> sejam alinhados. Observe a guia de alinhamento com um estilo diferente que aparece, indicando quando os campos de texto de ambos os controles estão alinhados.

## <a name="use-snaplines-with-keyboard-navigation"></a>Usar snaplines com navegação por teclado

1. Arraste um controle de <xref:System.Windows.Forms.Button> da **caixa de ferramentas** para seu formulário. Coloque-o no canto superior esquerdo do formulário.

2. Pressione **Ctrl**+**seta para baixo**. Observe que o controle se move para baixo no formulário até a primeira posição de alinhamento horizontal disponível.

3. Pressione **Ctrl**+**seta para baixo** até que o controle atinja a parte inferior do formulário. Observe as posições que ele ocupa conforme se move para baixo no formulário.

4. Pressione **Ctrl**+**seta para a direita**. Observe que o controle percorre o formulário até a primeira posição de alinhamento vertical disponível.

5. Pressione **Ctrl**+**seta para a direita** até que o controle atinja o lado do formulário. Observe as posições que ele ocupa conforme se move no formulário.

6. Mova o controle no formulário com uma combinação de teclas de direção. Observe as posições ocupadas pelo controle e as guias de alinhamento que o acompanham.

7. Pressione **Shift**+**teclas de seta** para redimensionar o controle de <xref:System.Windows.Forms.Button> por incrementos de um pixel.

8. Pressione **Ctrl**+**Shift**+**teclas de seta** para redimensionar o controle de <xref:System.Windows.Forms.Button> em incrementos de SnapLine.

## <a name="selectively-disable-snaplines"></a>Desabilitar seletivamente as snaplines

1. Arraste um controle de <xref:System.Windows.Forms.TableLayoutPanel> da **caixa de ferramentas** para seu formulário.

2. Clique duas vezes no ícone de controle de <xref:System.Windows.Forms.Button> na **caixa de ferramentas**. Observe que um novo controle de botão aparece na primeira célula do controle de <xref:System.Windows.Forms.TableLayoutPanel>.

3. Clique duas vezes no ícone de controle de <xref:System.Windows.Forms.Button> na **caixa de ferramentas** duas vezes mais. Isso deixa uma célula vazia no controle de <xref:System.Windows.Forms.TableLayoutPanel>.

4. Arraste um controle de <xref:System.Windows.Forms.Button> da **caixa de ferramentas** para a célula vazia do controle de <xref:System.Windows.Forms.TableLayoutPanel>. Observe que não aparece nenhuma guia de alinhamento.

5. Arraste o controle de <xref:System.Windows.Forms.Button> para fora do controle de <xref:System.Windows.Forms.TableLayoutPanel> e mova-o para o controle de <xref:System.Windows.Forms.TableLayoutPanel>. Observe que as guias de alinhamento aparecem novamente.

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

- Tente aninhar um controle de <xref:System.Windows.Forms.GroupBox> dentro de outro controle de <xref:System.Windows.Forms.GroupBox>. Coloque um controle de <xref:System.Windows.Forms.Button> dentro do controle de <xref:System.Windows.Forms.GroupBox> filho e outro dentro do controle de <xref:System.Windows.Forms.GroupBox> pai. Mova os controles de <xref:System.Windows.Forms.Button> para ver como os limites entre contêineres de snaplines.

- Crie uma coluna de controles de <xref:System.Windows.Forms.TextBox> e uma coluna correspondente de controles de <xref:System.Windows.Forms.Label>. Defina o valor da propriedade <xref:System.Windows.Forms.Control.AutoSize%2A> dos controles de <xref:System.Windows.Forms.Label> como `true`. Use snaplines para mover os controles de <xref:System.Windows.Forms.Label> para que o texto exibido seja alinhado com o texto nos controles de <xref:System.Windows.Forms.TextBox>.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Design.Behavior.SnapLine>
- [Passo a passo: organizando controles nos Windows Forms utilizando um FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Passo a passo: organizando controles nos Windows Forms usando um TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Passo a passo: definindo o layout de controles dos Windows Forms com preenchimento, margens e a propriedade AutoSize](windows-forms-controls-padding-autosize.md)
