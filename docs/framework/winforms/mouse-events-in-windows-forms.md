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
ms.openlocfilehash: 671e37c7d6dc40046d6d717d7785b03b6b545c7e
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59333672"
---
# <a name="mouse-events-in-windows-forms"></a>Eventos do mouse no Windows Forms
Quando manipula entradas de mouse, você geralmente deseja conhecer a localização do ponteiro do mouse e o estado dos botões do mouse. Este tópico fornece detalhes sobre como obter essas informações de eventos do mouse e explica a ordem em que eventos de clique do mouse são gerados em controles dos Windows Forms. Para obter uma lista e uma descrição de todos os eventos de mouse, consulte [Como a entrada do mouse funciona nos Windows Forms](how-mouse-input-works-in-windows-forms.md).  Consulte também [visão geral de manipuladores de eventos (Windows Forms)](event-handlers-overview-windows-forms.md) e [visão geral de eventos (Windows Forms)](events-overview-windows-forms.md).  
  
## <a name="mouse-information"></a>Informações sobre o mouse  
 Um <xref:System.Windows.Forms.MouseEventArgs> é enviado aos manipuladores de eventos do mouse relacionados a clicar em um botão do mouse e acompanhar os movimentos do mouse. <xref:System.Windows.Forms.MouseEventArgs> Fornece informações sobre o estado atual do mouse, incluindo a localização do ponteiro do mouse em coordenadas do cliente, quais botões do mouse estão pressionados e se a roda do mouse foi rolado. Muitos eventos do mouse, como aqueles que simplesmente avisam quando o ponteiro do mouse entrou ou saiu dos limites de um controle, envie um <xref:System.EventArgs> ao manipulador de eventos sem mais informações.  
  
 Se você quiser saber o estado atual dos botões do mouse ou o local do ponteiro do mouse e você quiser evitar manipular um evento de mouse, você também pode usar o <xref:System.Windows.Forms.Control.MouseButtons%2A> e <xref:System.Windows.Forms.Control.MousePosition%2A> propriedades do <xref:System.Windows.Forms.Control> classe. <xref:System.Windows.Forms.Control.MouseButtons%2A> Retorna informações sobre quais botões do mouse estão pressionados no momento. O <xref:System.Windows.Forms.Control.MousePosition%2A> retorna as coordenadas de tela do ponteiro do mouse e é equivalente ao valor retornado por <xref:System.Windows.Forms.Cursor.Position%2A>.  
  
## <a name="converting-between-screen-and-client-coordinates"></a>Convertendo entre coordenadas de cliente e da tela  
 Como algumas informações de localização do mouse estão em coordenadas de cliente e algumas estão em coordenadas de tela, talvez seja necessário converter um ponto de um sistema de coordenadas para outro. Você pode fazer isso facilmente usando o <xref:System.Windows.Forms.Control.PointToClient%2A> e <xref:System.Windows.Forms.Control.PointToScreen%2A> métodos disponíveis no <xref:System.Windows.Forms.Control> classe.  
  
## <a name="standard-click-event-behavior"></a>Comportamento do evento de clique  
 Se quiser manipular eventos de clique do mouse na ordem correta, você precisará conhecer a ordem em que os eventos de clique são gerados em controles dos Windows Forms. Todos os controles dos Windows Forms geram eventos de clique na mesma ordem quando um botão do mouse é pressionado e liberado (independentemente de qual botão do mouse), exceto onde é indicado na lista a seguir de controles individuais. A lista a seguir mostra a ordem dos eventos gerados por um único clique do botão do mouse:  
  
1. <xref:System.Windows.Forms.Control.MouseDown> .  
  
2. <xref:System.Windows.Forms.Control.Click> .  
  
3. <xref:System.Windows.Forms.Control.MouseClick> .  
  
4. <xref:System.Windows.Forms.Control.MouseUp> .  
  
 A seguir, temos a ordem dos eventos gerados por um clique duplo do botão do mouse:  
  
1. <xref:System.Windows.Forms.Control.MouseDown> .  
  
2. <xref:System.Windows.Forms.Control.Click> .  
  
3. <xref:System.Windows.Forms.Control.MouseClick> .  
  
4. <xref:System.Windows.Forms.Control.MouseUp> .  
  
5. <xref:System.Windows.Forms.Control.MouseDown> .  
  
6. <xref:System.Windows.Forms.Control.DoubleClick> . (Isso pode variar, dependendo se o controle em questão tem o <xref:System.Windows.Forms.ControlStyles.StandardDoubleClick> definido como bit de estilo `true`. Para obter mais informações sobre como definir um <xref:System.Windows.Forms.ControlStyles> bit, consulte o <xref:System.Windows.Forms.Control.SetStyle%2A> método.)  
  
7. <xref:System.Windows.Forms.Control.MouseDoubleClick> .  
  
8. <xref:System.Windows.Forms.Control.MouseUp> .  
  
 Para obter um exemplo de código que mostra a ordem do mouse, clique em eventos, consulte [como: Entrada do usuário de identificador de eventos nos Windows Forms a controles](how-to-handle-user-input-events-in-windows-forms-controls.md).  
  
### <a name="individual-controls"></a>Controles individuais  
 Os controles a seguir não estão em conformidade com o comportamento padrão dos eventos de clique do mouse:  
  
-   <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.CheckBox>, <xref:System.Windows.Forms.ComboBox>, e <xref:System.Windows.Forms.RadioButton> controles  
  
    > [!NOTE]
    >  Para o <xref:System.Windows.Forms.ComboBox> controle, o comportamento do evento detalhado a seguir ocorre se o usuário clicar no campo de edição, o botão, ou em um item dentro da lista.  
  
    -   Com o botão esquerdo: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>  
  
    -   Clique com botão direito: Nenhum evento de clique gerado  
  
    -   Clique duas vezes à esquerda: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>  
  
    -   Clique duas vezes à direita: Nenhum evento de clique gerado  
  
-   <xref:System.Windows.Forms.TextBox>, <xref:System.Windows.Forms.RichTextBox>, <xref:System.Windows.Forms.ListBox>, <xref:System.Windows.Forms.MaskedTextBox>, e <xref:System.Windows.Forms.CheckedListBox> controles  
  
    > [!NOTE]
    >  O comportamento do evento detalhado a seguir ocorre quando o usuário clica em qualquer lugar desses controles.  
  
    -   Com o botão esquerdo: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>  
  
    -   Clique com botão direito: Nenhum evento de clique gerado  
  
    -   Clique duas vezes à esquerda: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>, <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick>  
  
    -   Clique duas vezes à direita: Nenhum evento de clique gerado  
  
-   <xref:System.Windows.Forms.ListView> Controle   
  
    > [!NOTE]
    >  O comportamento do evento detalhado a seguir ocorre apenas quando o usuário clica nos itens a <xref:System.Windows.Forms.ListView> controle. Nenhum evento é gerado para cliques em qualquer outro lugar no controle. Além dos eventos descritos mais adiante, existem os <xref:System.Windows.Forms.ListView.BeforeLabelEdit> e <xref:System.Windows.Forms.ListView.AfterLabelEdit> eventos, que podem ser de seu interesse se você quiser usar a validação com o <xref:System.Windows.Forms.ListView> controle.  
  
    -   Com o botão esquerdo: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>  
  
    -   Clique com botão direito: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>  
  
    -   Clique duas vezes à esquerda: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick>  
  
    -   À direita, clique duas vezes: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick>  
  
-   <xref:System.Windows.Forms.TreeView> Controle   
  
    > [!NOTE]
    >  O comportamento do evento detalhado a seguir ocorre apenas quando o usuário clica nos próprios itens ou à direita dos itens no <xref:System.Windows.Forms.TreeView> controle. Nenhum evento é gerado para cliques em qualquer outro lugar no controle. Além dos descritos mais adiante, há o <xref:System.Windows.Forms.TreeView.BeforeCheck>, <xref:System.Windows.Forms.TreeView.BeforeSelect>, <xref:System.Windows.Forms.TreeView.BeforeLabelEdit>, <xref:System.Windows.Forms.TreeView.AfterSelect>, <xref:System.Windows.Forms.TreeView.AfterCheck>, e <xref:System.Windows.Forms.TreeView.AfterLabelEdit> eventos, que podem ser de seu interesse se você quiser usar a validação com o <xref:System.Windows.Forms.TreeView> controle .  
  
    -   Com o botão esquerdo: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>  
  
    -   Clique com botão direito: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>  
  
    -   Clique duas vezes à esquerda: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick>  
  
    -   À direita, clique duas vezes: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick>  
  
### <a name="painting-behavior-of-toggle-controls"></a>Comportamento de pintura dos controles de alternância  
 Ativar/desativar controles, como os controles que derivam de <xref:System.Windows.Forms.ButtonBase> de classe, ter o seguinte comportamento de pintura distinto em combinação com o mouse eventos de clique:  
  
1. O usuário pressiona o botão do mouse.  
  
2. O controle pinta no estado pressionado.  
  
3. O <xref:System.Windows.Forms.Control.MouseDown> é gerado.  
  
4. O usuário libera o botão do mouse.  
  
5. O controle pinta no estado elevado.  
  
6. O <xref:System.Windows.Forms.Control.Click> é gerado.  
  
7. O <xref:System.Windows.Forms.Control.MouseClick> é gerado.  
  
8. O <xref:System.Windows.Forms.Control.MouseUp> é gerado.  
  
    > [!NOTE]
    >  Se o usuário move o ponteiro para fora do controle de alternância enquanto o botão do mouse está pressionado (como mover o mouse o <xref:System.Windows.Forms.Button> controlar enquanto ele está pressionado), o controle de alternância pintará no solto estado e somente o <xref:System.Windows.Forms.Control.MouseUp> evento ocorre. O <xref:System.Windows.Forms.Control.Click> ou <xref:System.Windows.Forms.Control.MouseClick> eventos não ocorrerão nesta situação.  
  
## <a name="see-also"></a>Consulte também

- [Entrada do mouse em um aplicativo do Windows Forms](mouse-input-in-a-windows-forms-application.md)
