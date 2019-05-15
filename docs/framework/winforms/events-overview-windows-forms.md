---
title: Visão geral sobre eventos (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, event handling
- events [Windows Forms], about events
- delegates [Windows Forms], multicast
- delegates [Windows Forms], events and
- multicast event delegates
- Windows Forms controls, events
ms.assetid: 814a6a43-a312-4791-88d8-f75f9a4f8c4c
ms.openlocfilehash: 3adc2891579cafff9c8aeb3e918ae74c6f3ad8a5
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591017"
---
# <a name="events-overview-windows-forms"></a>Visão geral sobre eventos (Windows Forms)
Um evento é uma ação a qual você pode responder ou "manipular", no código. Os eventos podem ser gerados por uma ação do usuário, como o clicar do mouse ou pressionar de uma tecla, pelo código de programa ou pelo sistema.

 Os aplicativos controlados por eventos executam código em resposta a um evento. Cada formulário e controle expõe um conjunto predefinido de eventos com base nos quais você pode programar. Se um desses eventos ocorre e não há código no manipulador de evento associado, esse código é invocado.

 Os tipos de eventos gerados por um objeto variam, mas muitos tipos são comuns à maioria dos controles. Por exemplo, a maioria dos objetos lidará com um evento <xref:System.Windows.Forms.Control.Click>. Se um usuário clicar em um formulário, o código no manipulador de eventos <xref:System.Windows.Forms.Control.Click> do formulário é executado.

> [!NOTE]
>  Muitos eventos ocorrem com outros eventos. Por exemplo, enquanto o evento <xref:System.Windows.Forms.Control.DoubleClick> ocorre, os eventos <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.MouseUp> e <xref:System.Windows.Forms.Control.Click> ocorrem.

 Para obter informações sobre como gerar e consumir um evento, consulte [eventos](../../standard/events/index.md).

## <a name="delegates-and-their-role"></a>Classes delegate e suas funções
 Os delegados são classes comumente usados no .NET Framework para criar mecanismos de manipulação de eventos. As classes delegate, em termos gerais, equivalem a ponteiros de função, usados normalmente no [!INCLUDE[vcprvc](../../../includes/vcprvc-md.md)] e outras linguagens orientadas a objetos. No entanto, diferente dos ponteiros de função, as classes delegate são orientadas a objeto, fortemente tipadas e seguras. Além disso, quando um ponteiro de função contém apenas uma referência a uma função particular, uma classe delegate consiste em uma referência a um objeto, e as referências a um ou mais métodos dentro do objeto.

 Esse modelo de evento usa *delegados* para associar eventos aos métodos que são usados para lidar com eles. A classe delegate permite que outras classes se registrem para a notificação de eventos, especificando um método de manipulador. Quando o evento ocorre, a classe delegate chama o método associado. Para obter mais informações sobre como definir classes Delegate, consulte [eventos](../../standard/events/index.md).

 Essas classes podem ser associadas a um único método ou a vários métodos, o que chamamos de multicasting. Ao criar um delegado para um evento, você (ou o Windows) normalmente cria um evento multicast. Uma rara exceção pode ser um evento que resulta em um procedimento específico (como a exibição de uma caixa de diálogo) que não repetiria logicamente várias vezes por evento. Para obter informações sobre como criar um delegado multicast, consulte [como: Combinar delegados (delegados Multicast)](~/docs/csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md).

 Uma classe delegate multicast mantém uma lista de invocação dos métodos aos quais ela está associada. Essa classe é compatível com um método <xref:System.Delegate.Combine%2A> para adicionar um método à lista de invocação e um método <xref:System.Delegate.Remove%2A> para removê-lo.

 Quando um evento é registrado pelo aplicativo, o controle gera o evento invocando a classe delegate para esse evento. A classe delegate chama o método vinculado. No caso mais comum (uma classe delegate multicast) a classe chama cada método associado da lista de invocação, que fornece uma notificação de um para muitos. Essa estratégia significa que o controle não precisa manter uma lista de objetos de destino para notificação de eventos, a classe delegate lida com todo o registro e notificação.

 Essas classes também permitem que vários eventos sejam associados ao mesmo método, permitindo uma notificação muitos para um. Por exemplo, um evento de clique de botão e um evento de clique de comando de menu podem invocar a mesma classe delegate, que chama um único método para lidar com esses eventos separados da mesma maneira.

 O mecanismo de associação usado com essas classes é dinâmico: uma classe delegate pode ser associada em tempo de execução a qualquer método cuja assinatura corresponda à assinatura do manipulador de eventos. Com esse recurso, você pode configurar ou alterar o método associado de acordo com uma condição e anexar dinamicamente um manipulador de eventos a um controle.

## <a name="see-also"></a>Consulte também

- [Criando manipuladores de eventos no Windows Forms](creating-event-handlers-in-windows-forms.md)
- [Visão geral de manipuladores de eventos](event-handlers-overview-windows-forms.md)
