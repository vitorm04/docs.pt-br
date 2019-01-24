---
title: 'Como: Localizar o elemento de origem em um manipulador de eventos'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- source element in event handlers [WPF]
- event handlers [WPF], finding source element in
ms.assetid: 85f71c5a-b714-4c65-9711-7d905c2bbe98
ms.openlocfilehash: 4cdf1434f2d341cbc1e65541fd02ab4b5cad194d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54536731"
---
# <a name="how-to-find-the-source-element-in-an-event-handler"></a><span data-ttu-id="8ff7a-102">Como: Localizar o elemento de origem em um manipulador de eventos</span><span class="sxs-lookup"><span data-stu-id="8ff7a-102">How to: Find the Source Element in an Event Handler</span></span>
<span data-ttu-id="8ff7a-103">Este exemplo mostra como localizar o elemento de origem em um manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="8ff7a-103">This example shows how to find the source element in an event handler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ff7a-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8ff7a-104">Example</span></span>  
 <span data-ttu-id="8ff7a-105">A exemplo a seguir mostra um <xref:System.Windows.Controls.Primitives.ButtonBase.Click> manipulador de eventos que é declarada em um arquivo code-behind.</span><span class="sxs-lookup"><span data-stu-id="8ff7a-105">The following example shows a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler that is declared in a code-behind file.</span></span> <span data-ttu-id="8ff7a-106">Quando um usuário clica no botão que o manipulador está anexado a, o manipulador altera um valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="8ff7a-106">When a user clicks the button that the handler is attached to, the handler changes a property value.</span></span> <span data-ttu-id="8ff7a-107">O código do manipulador usa a <xref:System.Windows.RoutedEventArgs.Source%2A> propriedade dos dados do evento roteado que são relatados nos argumentos de evento para alterar o <xref:System.Windows.FrameworkElement.Width%2A> valor da propriedade a <xref:System.Windows.RoutedEventArgs.Source%2A> elemento.</span><span class="sxs-lookup"><span data-stu-id="8ff7a-107">The handler code uses the <xref:System.Windows.RoutedEventArgs.Source%2A> property of the routed event data that is reported in the event arguments to change the <xref:System.Windows.FrameworkElement.Width%2A> property value on the <xref:System.Windows.RoutedEventArgs.Source%2A> element.</span></span>  
  
 [!code-xaml[RoutedEventSource#XAMLHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventSource/CSharp/default.xaml#xamlhandler)]  
  
 [!code-csharp[RoutedEventSource#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventSource/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventSource#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventSource/VisualBasic/default.xaml.vb#handler)]  
  
## <a name="see-also"></a><span data-ttu-id="8ff7a-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8ff7a-108">See also</span></span>
- <xref:System.Windows.RoutedEventArgs>
- [<span data-ttu-id="8ff7a-109">Visão geral de eventos roteados</span><span class="sxs-lookup"><span data-stu-id="8ff7a-109">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
- [<span data-ttu-id="8ff7a-110">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="8ff7a-110">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/events-how-to-topics.md)
