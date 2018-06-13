---
title: Como localizar o elemento de origem em um manipulador de eventos
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- source element in event handlers [WPF]
- event handlers [WPF], finding source element in
ms.assetid: 85f71c5a-b714-4c65-9711-7d905c2bbe98
ms.openlocfilehash: c3ae893cd7fd7780854d6eb6ffd682feadb5c5a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543993"
---
# <a name="how-to-find-the-source-element-in-an-event-handler"></a><span data-ttu-id="62dc5-102">Como localizar o elemento de origem em um manipulador de eventos</span><span class="sxs-lookup"><span data-stu-id="62dc5-102">How to: Find the Source Element in an Event Handler</span></span>
<span data-ttu-id="62dc5-103">Este exemplo mostra como localizar o elemento de origem em um manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="62dc5-103">This example shows how to find the source element in an event handler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62dc5-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="62dc5-104">Example</span></span>  
 <span data-ttu-id="62dc5-105">A exemplo a seguir mostra um <xref:System.Windows.Controls.Primitives.ButtonBase.Click> manipulador de eventos que é declarado em um arquivo code-behind.</span><span class="sxs-lookup"><span data-stu-id="62dc5-105">The following example shows a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler that is declared in a code-behind file.</span></span> <span data-ttu-id="62dc5-106">Quando um usuário clica no botão que o manipulador está associado, o manipulador altera um valor de propriedade.</span><span class="sxs-lookup"><span data-stu-id="62dc5-106">When a user clicks the button that the handler is attached to, the handler changes a property value.</span></span> <span data-ttu-id="62dc5-107">O código do manipulador usa o <xref:System.Windows.RoutedEventArgs.Source%2A> propriedade dos dados do evento roteado relatado nos argumentos de evento para alterar o <xref:System.Windows.FrameworkElement.Width%2A> valor da propriedade a <xref:System.Windows.RoutedEventArgs.Source%2A> elemento.</span><span class="sxs-lookup"><span data-stu-id="62dc5-107">The handler code uses the <xref:System.Windows.RoutedEventArgs.Source%2A> property of the routed event data that is reported in the event arguments to change the <xref:System.Windows.FrameworkElement.Width%2A> property value on the <xref:System.Windows.RoutedEventArgs.Source%2A> element.</span></span>  
  
 [!code-xaml[RoutedEventSource#XAMLHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventSource/CSharp/default.xaml#xamlhandler)]  
  
 [!code-csharp[RoutedEventSource#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventSource/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventSource#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventSource/VisualBasic/default.xaml.vb#handler)]  
  
## <a name="see-also"></a><span data-ttu-id="62dc5-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="62dc5-108">See Also</span></span>  
 <xref:System.Windows.RoutedEventArgs>  
 [<span data-ttu-id="62dc5-109">Visão geral de eventos roteados</span><span class="sxs-lookup"><span data-stu-id="62dc5-109">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [<span data-ttu-id="62dc5-110">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="62dc5-110">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/events-how-to-topics.md)
