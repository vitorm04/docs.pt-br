---
title: Eventos do mouse no Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- MouseLeave event [Windows Forms]
- events [Windows Forms], mouse
- Click event [Windows Forms], raising order
- Windows Forms controls, click events
- MouseDoubleClick event [Windows Forms]
- MouseEnter event [Windows Forms]
- MouseHover event [Windows Forms]
- MouseDown event [Windows Forms]
- MouseClick event [Windows Forms]
- MouseMove event [Windows Forms]
- mouse [Windows Forms], events
- MouseUp event
ms.assetid: 8cf0070d-793b-4876-b09e-d20d28280fab
ms.openlocfilehash: a61f4eedde611cfb7598d55465103924516e06c6
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834604"
---
# <a name="mouse-events-in-windows-forms"></a>Eventos do mouse no Windows Forms

Quando manipula entradas de mouse, você geralmente deseja conhecer a localização do ponteiro do mouse e o estado dos botões do mouse. Este tópico fornece detalhes sobre como obter essas informações de eventos do mouse e explica a ordem em que eventos de clique do mouse são gerados em controles dos Windows Forms. Para obter uma lista e uma descrição de todos os eventos de mouse, consulte [Como a entrada do mouse funciona nos Windows Forms](how-mouse-input-works-in-windows-forms.md).  Consulte também visão geral de [manipuladores de eventos (Windows Forms)](event-handlers-overview-windows-forms.md) e [visão geral de eventos (Windows Forms)](events-overview-windows-forms.md).

## <a name="mouse-information"></a>Informações sobre o mouse

Um <xref:System.Windows.Forms.MouseEventArgs> é enviado aos manipuladores de eventos do mouse relacionados ao clique de um botão do mouse e do controle dos movimentos do mouse. <xref:System.Windows.Forms.MouseEventArgs> fornece informações sobre o estado atual do mouse, incluindo o local do ponteiro do mouse nas coordenadas do cliente, quais botões do mouse são pressionados e se a roda do mouse foi rolada. Vários eventos de mouse, como aqueles que simplesmente notificam quando o ponteiro do mouse inseriu ou deixaram os limites de um controle, enviam um <xref:System.EventArgs> ao manipulador de eventos sem nenhuma informação adicional.

Se você quiser saber o estado atual dos botões do mouse ou o local do ponteiro do mouse e desejar evitar manipular um evento do mouse, também poderá usar as propriedades <xref:System.Windows.Forms.Control.MouseButtons%2A> e <xref:System.Windows.Forms.Control.MousePosition%2A> da classe <xref:System.Windows.Forms.Control>. <xref:System.Windows.Forms.Control.MouseButtons%2A> retorna informações sobre quais botões do mouse estão pressionados no momento. O <xref:System.Windows.Forms.Control.MousePosition%2A> retorna as coordenadas de tela do ponteiro do mouse e é equivalente ao valor retornado por <xref:System.Windows.Forms.Cursor.Position%2A>.

## <a name="converting-between-screen-and-client-coordinates"></a>Convertendo entre coordenadas de cliente e da tela

Como algumas informações de localização do mouse estão em coordenadas de cliente e algumas estão em coordenadas de tela, talvez seja necessário converter um ponto de um sistema de coordenadas para outro. Você pode fazer isso facilmente usando os métodos <xref:System.Windows.Forms.Control.PointToClient%2A> e <xref:System.Windows.Forms.Control.PointToScreen%2A> disponíveis na classe <xref:System.Windows.Forms.Control>.

## <a name="standard-click-event-behavior"></a>Comportamento do evento de clique

Se quiser manipular eventos de clique do mouse na ordem correta, você precisará conhecer a ordem em que os eventos de clique são gerados em controles dos Windows Forms. Todos os controles dos Windows Forms geram eventos de clique na mesma ordem quando um botão do mouse é pressionado e liberado (independentemente de qual botão do mouse), exceto onde é indicado na lista a seguir de controles individuais. A lista a seguir mostra a ordem dos eventos gerados por um único clique do botão do mouse:

1. <xref:System.Windows.Forms.Control.MouseDown> evento.

2. <xref:System.Windows.Forms.Control.Click> evento.

3. <xref:System.Windows.Forms.Control.MouseClick> evento.

4. <xref:System.Windows.Forms.Control.MouseUp> evento.

A seguir está a ordem dos eventos gerados para um clique duplo com botão do mouse:

1. <xref:System.Windows.Forms.Control.MouseDown> evento.

2. <xref:System.Windows.Forms.Control.Click> evento.

3. <xref:System.Windows.Forms.Control.MouseClick> evento.

4. <xref:System.Windows.Forms.Control.MouseUp> evento.

5. <xref:System.Windows.Forms.Control.MouseDown> evento.

6. <xref:System.Windows.Forms.Control.DoubleClick> evento. (Isso pode variar, dependendo se o controle em questão tem o conjunto de bits <xref:System.Windows.Forms.ControlStyles.StandardDoubleClick> de estilo definido como `true`. Para obter mais informações sobre como definir um bit de <xref:System.Windows.Forms.ControlStyles>, consulte o método <xref:System.Windows.Forms.Control.SetStyle%2A>.)

7. <xref:System.Windows.Forms.Control.MouseDoubleClick> evento.

8. <xref:System.Windows.Forms.Control.MouseUp> evento.

Para ver um exemplo de código que mostra a ordem dos eventos de clique do mouse, consulte [Como manipular eventos de entrada do usuário em controles dos Windows Forms](how-to-handle-user-input-events-in-windows-forms-controls.md).

### <a name="individual-controls"></a>Controles individuais

Os controles a seguir não estão em conformidade com o comportamento padrão dos eventos de clique do mouse:

- <xref:System.Windows.Forms.Button>
- <xref:System.Windows.Forms.CheckBox>
- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.RadioButton>

  > [!NOTE]
  > Para o controle de <xref:System.Windows.Forms.ComboBox>, o comportamento de evento detalhado posteriormente ocorrerá se o usuário clicar no campo de edição, no botão ou em um item dentro da lista.

  - Clique com o botão esquerdo: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>

  - Clique com botão direito do mouse: não são gerados eventos de clique

  - Clique duas vezes com o botão esquerdo: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>

  - Clique duas vezes com botão direito: não são gerados eventos de clique

- controles <xref:System.Windows.Forms.TextBox>, <xref:System.Windows.Forms.RichTextBox>, <xref:System.Windows.Forms.ListBox>, <xref:System.Windows.Forms.MaskedTextBox>e <xref:System.Windows.Forms.CheckedListBox>

  > [!NOTE]
  > O comportamento do evento detalhado a seguir ocorre quando o usuário clica em qualquer lugar desses controles.

  - Clique com o botão esquerdo: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>

  - Clique com botão direito do mouse: não são gerados eventos de clique

  - Clique duas vezes com o botão esquerdo: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>, <xref:System.Windows.Forms.Control.DoubleClick><xref:System.Windows.Forms.Control.MouseDoubleClick>

  - Clique duas vezes com botão direito: não são gerados eventos de clique

- Controle <xref:System.Windows.Forms.ListView>

  > [!NOTE]
  > O comportamento de evento detalhado posteriormente ocorre somente quando o usuário clica nos itens no controle de <xref:System.Windows.Forms.ListView>. Nenhum evento é gerado para cliques em qualquer outro lugar no controle. Além dos eventos descritos posteriormente, há os eventos de <xref:System.Windows.Forms.ListView.BeforeLabelEdit> e <xref:System.Windows.Forms.ListView.AfterLabelEdit>, que podem ser de seu interesse se você quiser usar a validação com o controle de <xref:System.Windows.Forms.ListView>.

  - Clique com o botão esquerdo: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>

  - Clique com o botão direito do mouse em: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>

  - Clique duas vezes com o botão esquerdo: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick>

  - Clique duas vezes com o botão direito do mouse: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick>

- Controle <xref:System.Windows.Forms.TreeView>

  > [!NOTE]
  > O comportamento de evento detalhado posteriormente ocorre apenas quando o usuário clica nos itens em si ou à direita dos itens no controle de <xref:System.Windows.Forms.TreeView>. Nenhum evento é gerado para cliques em qualquer outro lugar no controle. Além daqueles descritos posteriormente, há os eventos <xref:System.Windows.Forms.TreeView.BeforeCheck>, <xref:System.Windows.Forms.TreeView.BeforeSelect>, <xref:System.Windows.Forms.TreeView.BeforeLabelEdit>, <xref:System.Windows.Forms.TreeView.AfterSelect>, <xref:System.Windows.Forms.TreeView.AfterCheck>e <xref:System.Windows.Forms.TreeView.AfterLabelEdit>, que podem ser de seu interesse se você quiser usar a validação com o controle <xref:System.Windows.Forms.TreeView>.

  - Clique com o botão esquerdo: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>

  - Clique com o botão direito do mouse em: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>

  - Clique duas vezes com o botão esquerdo: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick>

  - Clique duas vezes com o botão direito do mouse: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick>

### <a name="painting-behavior-of-toggle-controls"></a>Comportamento de pintura de controles de alternância

Os controles de alternância, como os controles derivados da classe <xref:System.Windows.Forms.ButtonBase>, têm o seguinte comportamento de pintura distinto em combinação com eventos de clique do mouse:

1. O usuário pressiona o botão do mouse.

2. O controle pinta no estado pressionado.

3. O evento <xref:System.Windows.Forms.Control.MouseDown> é gerado.

4. O usuário libera o botão do mouse.

5. O controle pinta no estado elevado.

6. O evento <xref:System.Windows.Forms.Control.Click> é gerado.

7. O evento <xref:System.Windows.Forms.Control.MouseClick> é gerado.

8. O evento <xref:System.Windows.Forms.Control.MouseUp> é gerado.

    > [!NOTE]
    > Se o usuário mover o ponteiro para fora do controle de alternância enquanto o botão do mouse estiver inoperante (como mover o mouse para fora do controle de <xref:System.Windows.Forms.Button> enquanto ele é pressionado), o controle de alternância será pintado no estado gerado e somente o evento de <xref:System.Windows.Forms.Control.MouseUp> ocorrerá. Os eventos de <xref:System.Windows.Forms.Control.Click> ou <xref:System.Windows.Forms.Control.MouseClick> não ocorrerão nessa situação.

## <a name="see-also"></a>Consulte também

- [Entrada do mouse em um aplicativo dos Windows Forms](mouse-input-in-a-windows-forms-application.md)
