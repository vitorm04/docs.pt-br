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
ms.openlocfilehash: 181d01f6e688b94876f77155bf598aba129e9fbf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949905"
---
# <a name="mouse-events-in-windows-forms"></a>Eventos do mouse no Windows Forms

Quando manipula entradas de mouse, você geralmente deseja conhecer a localização do ponteiro do mouse e o estado dos botões do mouse. Este tópico fornece detalhes sobre como obter essas informações de eventos do mouse e explica a ordem em que eventos de clique do mouse são gerados em controles dos Windows Forms. Para obter uma lista e uma descrição de todos os eventos de mouse, consulte [Como a entrada do mouse funciona nos Windows Forms](how-mouse-input-works-in-windows-forms.md).  Consulte também visão geral de manipuladores de [eventos (Windows Forms)](event-handlers-overview-windows-forms.md) e [visão geral de eventos (Windows Forms)](events-overview-windows-forms.md).

## <a name="mouse-information"></a>Informações sobre o mouse

Um <xref:System.Windows.Forms.MouseEventArgs> é enviado aos manipuladores de eventos do mouse relacionados ao clique de um botão do mouse e do controle dos movimentos do mouse. <xref:System.Windows.Forms.MouseEventArgs>fornece informações sobre o estado atual do mouse, incluindo o local do ponteiro do mouse em coordenadas do cliente, quais botões do mouse são pressionados e se a roda do mouse foi rolada. Vários eventos de mouse, como aqueles que simplesmente notificam quando o ponteiro do mouse inseriu ou deixaram os limites de um controle, enviam um <xref:System.EventArgs> para o manipulador de eventos sem informações adicionais.

Se você quiser saber o estado atual dos botões do mouse ou o local do ponteiro do mouse e desejar evitar manipular um evento do mouse, também poderá usar as <xref:System.Windows.Forms.Control.MouseButtons%2A> Propriedades e <xref:System.Windows.Forms.Control.MousePosition%2A> da <xref:System.Windows.Forms.Control> classe. <xref:System.Windows.Forms.Control.MouseButtons%2A>Retorna informações sobre quais botões do mouse estão pressionados no momento. O <xref:System.Windows.Forms.Control.MousePosition%2A> retorna as coordenadas de tela do ponteiro do mouse e é equivalente ao valor retornado por <xref:System.Windows.Forms.Cursor.Position%2A>.

## <a name="converting-between-screen-and-client-coordinates"></a>Convertendo entre coordenadas de cliente e da tela

Como algumas informações de localização do mouse estão em coordenadas de cliente e algumas estão em coordenadas de tela, talvez seja necessário converter um ponto de um sistema de coordenadas para outro. Você pode fazer isso facilmente usando os <xref:System.Windows.Forms.Control.PointToClient%2A> métodos e <xref:System.Windows.Forms.Control.PointToScreen%2A> disponíveis na <xref:System.Windows.Forms.Control> classe.

## <a name="standard-click-event-behavior"></a>Comportamento do evento de clique

Se quiser manipular eventos de clique do mouse na ordem correta, você precisará conhecer a ordem em que os eventos de clique são gerados em controles dos Windows Forms. Todos os controles dos Windows Forms geram eventos de clique na mesma ordem quando um botão do mouse é pressionado e liberado (independentemente de qual botão do mouse), exceto onde é indicado na lista a seguir de controles individuais. A lista a seguir mostra a ordem dos eventos gerados por um único clique do botão do mouse:

1. <xref:System.Windows.Forms.Control.MouseDown>circunstância.

2. <xref:System.Windows.Forms.Control.Click>circunstância.

3. <xref:System.Windows.Forms.Control.MouseClick>circunstância.

4. <xref:System.Windows.Forms.Control.MouseUp>circunstância.

A seguir, temos a ordem dos eventos gerados por um clique duplo do botão do mouse:

1. <xref:System.Windows.Forms.Control.MouseDown>circunstância.

2. <xref:System.Windows.Forms.Control.Click>circunstância.

3. <xref:System.Windows.Forms.Control.MouseClick>circunstância.

4. <xref:System.Windows.Forms.Control.MouseUp>circunstância.

5. <xref:System.Windows.Forms.Control.MouseDown>circunstância.

6. <xref:System.Windows.Forms.Control.DoubleClick>circunstância. (Isso pode variar, dependendo se o controle em questão tem o <xref:System.Windows.Forms.ControlStyles.StandardDoubleClick> bit de estilo definido como. `true` Para obter mais informações sobre como definir um <xref:System.Windows.Forms.ControlStyles> bit, consulte o <xref:System.Windows.Forms.Control.SetStyle%2A> método.)

7. <xref:System.Windows.Forms.Control.MouseDoubleClick>circunstância.

8. <xref:System.Windows.Forms.Control.MouseUp>circunstância.

Para obter um exemplo de código que demonstra a ordem dos eventos de clique do [mouse, consulte Como: Manipular eventos de entrada do usuário em](how-to-handle-user-input-events-in-windows-forms-controls.md)controles Windows Forms.

### <a name="individual-controls"></a>Controles individuais

Os controles a seguir não estão em conformidade com o comportamento padrão dos eventos de clique do mouse:

- <xref:System.Windows.Forms.Button>controles, <xref:System.Windows.Forms.CheckBox>, e<xref:System.Windows.Forms.RadioButton> <xref:System.Windows.Forms.ComboBox>

  > [!NOTE]
  > Para o <xref:System.Windows.Forms.ComboBox> controle, o comportamento de evento detalhado posteriormente ocorrerá se o usuário clicar no campo de edição, no botão ou em um item dentro da lista.

  - Clique com o <xref:System.Windows.Forms.Control.Click>botão esquerdo:,<xref:System.Windows.Forms.Control.MouseClick>

  - Clique com o botão direito do mouse: Nenhum evento de clique gerado

  - Clique duas vezes com o <xref:System.Windows.Forms.Control.Click>botão <xref:System.Windows.Forms.Control.MouseClick>esquerdo:,; <xref:System.Windows.Forms.Control.Click>,<xref:System.Windows.Forms.Control.MouseClick>

  - Clique duas vezes com o botão direito: Nenhum evento de clique gerado

- <xref:System.Windows.Forms.TextBox>controles, <xref:System.Windows.Forms.RichTextBox>,, e<xref:System.Windows.Forms.CheckedListBox> <xref:System.Windows.Forms.ListBox> <xref:System.Windows.Forms.MaskedTextBox>

  > [!NOTE]
  > O comportamento do evento detalhado a seguir ocorre quando o usuário clica em qualquer lugar desses controles.

  - Clique com o <xref:System.Windows.Forms.Control.Click>botão esquerdo:,<xref:System.Windows.Forms.Control.MouseClick>

  - Clique com o botão direito do mouse: Nenhum evento de clique gerado

  - Clique duas vezes com o <xref:System.Windows.Forms.Control.Click>botão <xref:System.Windows.Forms.Control.MouseClick>esquerdo <xref:System.Windows.Forms.Control.DoubleClick>:,,,<xref:System.Windows.Forms.Control.MouseDoubleClick>

  - Clique duas vezes com o botão direito: Nenhum evento de clique gerado

- Controle <xref:System.Windows.Forms.ListView>

  > [!NOTE]
  > O comportamento de evento detalhado posteriormente ocorre somente quando o usuário clica nos itens no <xref:System.Windows.Forms.ListView> controle. Nenhum evento é gerado para cliques em qualquer outro lugar no controle. Além dos eventos descritos posteriormente, há os <xref:System.Windows.Forms.ListView.BeforeLabelEdit> eventos e <xref:System.Windows.Forms.ListView.AfterLabelEdit> , que podem ser de seu interesse se você quiser usar a validação com o <xref:System.Windows.Forms.ListView> controle.

  - Clique com o <xref:System.Windows.Forms.Control.Click>botão esquerdo:,<xref:System.Windows.Forms.Control.MouseClick>

  - Clique com o <xref:System.Windows.Forms.Control.Click>botão direito do mouse em:<xref:System.Windows.Forms.Control.MouseClick>

  - Clique duas vezes com o <xref:System.Windows.Forms.Control.Click>botão <xref:System.Windows.Forms.Control.MouseClick>esquerdo:,; <xref:System.Windows.Forms.Control.DoubleClick>,<xref:System.Windows.Forms.Control.MouseDoubleClick>

  - Clique duas vezes com o <xref:System.Windows.Forms.Control.Click>botão <xref:System.Windows.Forms.Control.MouseClick>direito do mouse:,; <xref:System.Windows.Forms.Control.DoubleClick>,<xref:System.Windows.Forms.Control.MouseDoubleClick>

- Controle <xref:System.Windows.Forms.TreeView>

  > [!NOTE]
  > O comportamento de evento detalhado posteriormente ocorre somente quando o usuário clica nos itens em si ou à direita dos itens no <xref:System.Windows.Forms.TreeView> controle. Nenhum evento é gerado para cliques em qualquer outro lugar no controle. Além daqueles descritos posteriormente <xref:System.Windows.Forms.TreeView.BeforeCheck>, há os eventos <xref:System.Windows.Forms.TreeView.BeforeLabelEdit>, <xref:System.Windows.Forms.TreeView.AfterCheck> <xref:System.Windows.Forms.TreeView.AfterSelect> <xref:System.Windows.Forms.TreeView.BeforeSelect>,,, e <xref:System.Windows.Forms.TreeView.AfterLabelEdit> , que podem ser de seu interesse se você quiser usar a validação com o <xref:System.Windows.Forms.TreeView> controle .

  - Clique com o <xref:System.Windows.Forms.Control.Click>botão esquerdo:,<xref:System.Windows.Forms.Control.MouseClick>

  - Clique com o <xref:System.Windows.Forms.Control.Click>botão direito do mouse em:<xref:System.Windows.Forms.Control.MouseClick>

  - Clique duas vezes com o <xref:System.Windows.Forms.Control.Click>botão <xref:System.Windows.Forms.Control.MouseClick>esquerdo:,; <xref:System.Windows.Forms.Control.DoubleClick>,<xref:System.Windows.Forms.Control.MouseDoubleClick>

  - Clique duas vezes com o <xref:System.Windows.Forms.Control.Click>botão <xref:System.Windows.Forms.Control.MouseClick>direito do mouse:,; <xref:System.Windows.Forms.Control.DoubleClick>,<xref:System.Windows.Forms.Control.MouseDoubleClick>

### <a name="painting-behavior-of-toggle-controls"></a>Comportamento de pintura dos controles de alternância

Os controles de alternância, como os controles derivados da <xref:System.Windows.Forms.ButtonBase> classe, têm o seguinte comportamento de pintura distinto em combinação com eventos de clique do mouse:

1. O usuário pressiona o botão do mouse.

2. O controle pinta no estado pressionado.

3. O <xref:System.Windows.Forms.Control.MouseDown> evento é gerado.

4. O usuário libera o botão do mouse.

5. O controle pinta no estado elevado.

6. O <xref:System.Windows.Forms.Control.Click> evento é gerado.

7. O <xref:System.Windows.Forms.Control.MouseClick> evento é gerado.

8. O <xref:System.Windows.Forms.Control.MouseUp> evento é gerado.

    > [!NOTE]
    > Se o usuário mover o ponteiro para fora do controle de alternância enquanto o botão do mouse estiver inoperante (como mover o mouse para <xref:System.Windows.Forms.Button> fora do controle enquanto ele é pressionado), o controle de alternância será pintado no estado gerado e <xref:System.Windows.Forms.Control.MouseUp> apenas o evento ocorrerá. Os <xref:System.Windows.Forms.Control.Click> eventos <xref:System.Windows.Forms.Control.MouseClick> ou não ocorrerão nessa situação.

## <a name="see-also"></a>Consulte também

- [Entrada do mouse em um Aplicativo do Windows Forms](mouse-input-in-a-windows-forms-application.md)
