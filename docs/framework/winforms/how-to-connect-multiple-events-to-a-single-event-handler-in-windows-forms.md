---
title: 'Como: conectar vários eventos a um único manipulador de eventos no Windows Forms'
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- events [Windows Forms], connecting multiple to single event handler
- event handlers [Windows Forms], connecting events to
- menus [Windows Forms], event-handling methods for multiple menu items
- Windows Forms controls, events
- menu items [Windows Forms], multicasting event-handling methods
ms.assetid: 5a20749a-41b5-4acc-8eb1-9e5040b0a2c4
ms.openlocfilehash: d55ccc21efb92ba1e51f4ae88be5025f2f80905b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59117956"
---
# <a name="how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms"></a>Como: conectar vários eventos a um único manipulador de eventos no Windows Forms
No projeto do seu aplicativo, talvez seja necessário usar um único manipulador de eventos para vários eventos ou fazer com que vários eventos executem o mesmo procedimento. Por exemplo, fazer um comando de menu gerar o mesmo evento que um botão no seu formulário geralmente representará uma grande economia de tempo se eles expuserem a mesma funcionalidade. Você pode fazer isso usando a exibição Eventos da janela Propriedades em C# ou usando a palavra-chave `Handles` e as caixas suspensas **Nome de Classe** e **Nome do Método** no Editor de Código do Visual Basic.  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-visual-basic"></a>Conectar vários eventos a um único manipulador de eventos no Visual Basic  
  
1.  Clique com o botão direito do mouse no formulário e escolha **Exibir Código**.  
  
2.  Na caixa suspensa **Nome de Classe**, selecione um dos controles que você deseja que o manipulador de eventos trate.  
  
3.  Na caixa suspensa **Nome de Método**, selecione um dos eventos que você deseja que o manipulador de eventos trate.  
  
4.  O Editor de Código insere o manipulador de eventos apropriado e posiciona o ponto de inserção dentro do método. No exemplo a seguir, é o <xref:System.Windows.Forms.Control.Click> evento para o <xref:System.Windows.Forms.Button> controle.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
5.  Acrescente os outros eventos que você deseja que sejam tratados à cláusula `Handles`.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click, Button2.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
6.  Adicione o código apropriado ao manipulador de eventos.  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-c"></a>Para conectar vários eventos a um único manipulador de eventos em C\#
  
1.  Selecione o controle ao qual você deseja conectar um manipulador de eventos.  
  
2.  Na janela Propriedades, clique no botão **Eventos** (![Botão Eventos](./media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")).  
  
3.  Clique no nome do evento que você deseja tratar.  
  
4.  Na seção de valor ao lado do nome do evento, clique no botão da lista suspensa para exibir uma lista de manipuladores de eventos existentes que correspondem à assinatura do método do evento que você deseja tratar.  
  
5.  Selecione o manipulador de eventos apropriado na lista.  
  
     O código será adicionado ao formulário para associar o evento ao manipulador de eventos existente.  
  
## <a name="see-also"></a>Consulte também

- [Criando manipuladores de eventos no Windows Forms](creating-event-handlers-in-windows-forms.md)
- [Visão geral de manipuladores de eventos](event-handlers-overview-windows-forms.md)
