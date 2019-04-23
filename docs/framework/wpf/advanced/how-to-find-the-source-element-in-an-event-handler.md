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
ms.openlocfilehash: 9a49878c9ad8313903df4506796998fd43e2e749
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59104553"
---
# <a name="how-to-find-the-source-element-in-an-event-handler"></a><span data-ttu-id="fcdf5-102">Como: Localizar o elemento de origem em um manipulador de eventos</span><span class="sxs-lookup"><span data-stu-id="fcdf5-102">How to: Find the Source Element in an Event Handler</span></span>
<span data-ttu-id="fcdf5-103">Este exemplo mostra como localizar o elemento de origem em um manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="fcdf5-103">This example shows how to find the source element in an event handler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fcdf5-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fcdf5-104">Example</span></span>  
 <span data-ttu-id="fcdf5-105">A exemplo a seguir mostra um <xref:System.Windows.Controls.Primitives.ButtonBase.Click> manipulador de eventos que é declarada em um arquivo code-behind.</span><span class="sxs-lookup"><span data-stu-id="fcdf5-105">The following example shows a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler that is declared in a code-behind file.</span></span> <span data-ttu-id="fcdf5-106">Quando um usuário clica no botão que o manipulador está anexado a, o manipulador altera um valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="fcdf5-106">When a user clicks the button that the handler is attached to, the handler changes a property value.</span></span> <span data-ttu-id="fcdf5-107">O código do manipulador usa a <xref:System.Windows.RoutedEventArgs.Source%2A> propriedade dos dados do evento roteado que são relatados nos argumentos de evento para alterar o <xref:System.Windows.FrameworkElement.Width%2A> valor da propriedade a <xref:System.Windows.RoutedEventArgs.Source%2A> elemento.</span><span class="sxs-lookup"><span data-stu-id="fcdf5-107">The handler code uses the <xref:System.Windows.RoutedEventArgs.Source%2A> property of the routed event data that is reported in the event arguments to change the <xref:System.Windows.FrameworkElement.Width%2A> property value on the <xref:System.Windows.RoutedEventArgs.Source%2A> element.</span></span>  
  
 [!code-xaml[RoutedEventSource#XAMLHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventSource/CSharp/default.xaml#xamlhandler)]  
  
 [!code-csharp[RoutedEventSource#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventSource/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventSource#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventSource/VisualBasic/default.xaml.vb#handler)]  
  
## <a name="see-also"></a><span data-ttu-id="fcdf5-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fcdf5-108">See also</span></span>

- <xref:System.Windows.RoutedEventArgs>
- [<span data-ttu-id="fcdf5-109">Visão geral de eventos roteados</span><span class="sxs-lookup"><span data-stu-id="fcdf5-109">Routed Events Overview</span></span>](routed-events-overview.md)
- [<span data-ttu-id="fcdf5-110">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="fcdf5-110">How-to Topics</span></span>](events-how-to-topics.md)
