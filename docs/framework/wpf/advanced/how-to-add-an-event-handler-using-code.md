---
title: 'Como: Adicionar um manipulador de eventos usando código'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- event handlers [WPF], adding
- XAML [WPF], adding event handlers
ms.assetid: 269c61e0-6bd9-4291-9bed-1c5ee66da486
ms.openlocfilehash: 10f8e0899e61d5d54589c910bdcbcd92d8ee947c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129347"
---
# <a name="how-to-add-an-event-handler-using-code"></a><span data-ttu-id="baf2f-102">Como: Adicionar um manipulador de eventos usando código</span><span class="sxs-lookup"><span data-stu-id="baf2f-102">How to: Add an Event Handler Using Code</span></span>
<span data-ttu-id="baf2f-103">Esse exemplo mostra como adicionar um manipulador de eventos a um elemento usando código.</span><span class="sxs-lookup"><span data-stu-id="baf2f-103">This example shows how to add an event handler to an element by using code.</span></span>  
  
 <span data-ttu-id="baf2f-104">Se você desejar adicionar um manipulador de eventos a um elemento [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] e a página de marcação que contém o elemento já foi carregada, será necessário adicionar o manipulador usando código.</span><span class="sxs-lookup"><span data-stu-id="baf2f-104">If you want to add an event handler to a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] element, and the markup page that contains the element has already been loaded, you must add the handler using code.</span></span> <span data-ttu-id="baf2f-105">Como alternativa, se estiver compilando a árvore de elementos para um aplicativo usando inteiramente código e não declarando nenhum elemento usando [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], você poderá chamar métodos específicos para adicionar manipuladores de eventos à árvore de elementos construídos.</span><span class="sxs-lookup"><span data-stu-id="baf2f-105">Alternatively, if you are building up the element tree for an application entirely using code and not declaring any elements using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can call specific methods to add event handlers to the constructed element tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="baf2f-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="baf2f-106">Example</span></span>  
 <span data-ttu-id="baf2f-107">O exemplo a seguir adiciona um novo <xref:System.Windows.Controls.Button> a uma página existente que está inicialmente definida em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="baf2f-107">The following example adds a new <xref:System.Windows.Controls.Button> to an existing page that is initially defined in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="baf2f-108">Um arquivo code-behind implementa um método de manipulador de eventos e, em seguida, adiciona esse método como um novo manipulador de eventos sobre o <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="baf2f-108">A code-behind file implements an event handler method and then adds that method as a new event handler on the <xref:System.Windows.Controls.Button>.</span></span>  
  
 <span data-ttu-id="baf2f-109">O C# exemplo usa o `+=` operador para atribuir um manipulador a um evento.</span><span class="sxs-lookup"><span data-stu-id="baf2f-109">The C# example uses the `+=` operator to assign a handler to an event.</span></span> <span data-ttu-id="baf2f-110">Este é o mesmo operador que é usado para atribuir um manipulador no modelo de manipulação de eventos [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)].</span><span class="sxs-lookup"><span data-stu-id="baf2f-110">This is the same operator that is used to assign a handler in the [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] event handling model.</span></span> <span data-ttu-id="baf2f-111">Microsoft Visual Basic não suporta este operador como um meio de adicionar manipuladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="baf2f-111">Microsoft Visual Basic does not support this operator as a means of adding event handlers.</span></span> <span data-ttu-id="baf2f-112">Em vez disso, ele requer uma de duas técnicas:</span><span class="sxs-lookup"><span data-stu-id="baf2f-112">It instead requires one of two techniques:</span></span>  
  
-   <span data-ttu-id="baf2f-113">Use o <xref:System.Windows.UIElement.AddHandler%2A> método, junto com um `AddressOf` operador, para fazer referência a implementação do manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="baf2f-113">Use the <xref:System.Windows.UIElement.AddHandler%2A> method, together with an `AddressOf` operator, to reference the event handler implementation.</span></span>  
  
-   <span data-ttu-id="baf2f-114">Use a palavra-chave `Handles` como parte da definição do manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="baf2f-114">Use the `Handles` keyword as part of the event handler definition.</span></span> <span data-ttu-id="baf2f-115">Essa técnica não é mostrada aqui. Consulte [Manipulação de eventos do Visual Basic e WPF](visual-basic-and-wpf-event-handling.md).</span><span class="sxs-lookup"><span data-stu-id="baf2f-115">This technique is not shown here; see [Visual Basic and WPF Event Handling](visual-basic-and-wpf-event-handling.md).</span></span>  
  
 [!code-xaml[RoutedEventAddRemoveHandler#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[RoutedEventAddRemoveHandler#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventAddRemoveHandler#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/VisualBasic/default.xaml.vb#handler)]  
  
> [!NOTE]
>  <span data-ttu-id="baf2f-116">É muito mais simples adicionar um manipulador de eventos na página [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] analisada inicialmente.</span><span class="sxs-lookup"><span data-stu-id="baf2f-116">Adding an event handler in the initially parsed [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page is much simpler.</span></span> <span data-ttu-id="baf2f-117">Dentro do elemento de objetos ao qual você deseja adicionar o manipulador de eventos, adicione um atributo que corresponde ao nome do evento que você deseja manipular.</span><span class="sxs-lookup"><span data-stu-id="baf2f-117">Within the object element where you want to add the event handler, add an attribute that matches the name of the event that you want to handle.</span></span> <span data-ttu-id="baf2f-118">Em seguida, especifique o valor desse atributo como o nome do método do manipulador de eventos que você definiu no arquivo code-behind da página [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="baf2f-118">Then specify the value of that attribute as the name of the event handler method that you defined in the code-behind file of the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page.</span></span> <span data-ttu-id="baf2f-119">Para obter mais informações, consulte [Visão geral de XAML (WPF)](xaml-overview-wpf.md) ou [Visão geral de eventos roteados](routed-events-overview.md).</span><span class="sxs-lookup"><span data-stu-id="baf2f-119">For more information, see [XAML Overview (WPF)](xaml-overview-wpf.md) or [Routed Events Overview](routed-events-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baf2f-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="baf2f-120">See also</span></span>

- [<span data-ttu-id="baf2f-121">Visão geral de eventos roteados</span><span class="sxs-lookup"><span data-stu-id="baf2f-121">Routed Events Overview</span></span>](routed-events-overview.md)
- [<span data-ttu-id="baf2f-122">Tópicos explicativos </span><span class="sxs-lookup"><span data-stu-id="baf2f-122">How-to Topics</span></span>](events-how-to-topics.md)
