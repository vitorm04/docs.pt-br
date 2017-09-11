---
title: "Como realizar e cancelar a assinatura de eventos (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- event handlers [C#], creating
- Code Editor, event handlers
- events [C#], creating using the IDE
ms.assetid: 6319f39f-282c-4173-8a62-6c4657cf51cd
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: d444a2efe03ec127ff88236deadab719d0d64259
ms.contentlocale: pt-br
ms.lasthandoff: 09/08/2017

---
# <a name="how-to-subscribe-to-and-unsubscribe-from-events-c-programming-guide"></a><span data-ttu-id="a8280-102">Como realizar e cancelar a assinatura de eventos (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="a8280-102">How to: Subscribe to and Unsubscribe from Events (C# Programming Guide)</span></span>
<span data-ttu-id="a8280-103">Você assina um evento publicado por outra classe quando quer escrever um código personalizado que é chamado quando esse evento é gerado.</span><span class="sxs-lookup"><span data-stu-id="a8280-103">You subscribe to an event that is published by another class when you want to write custom code that is called when that event is raised.</span></span> <span data-ttu-id="a8280-104">Por exemplo, você pode assinar o evento `click` de um botão para fazer com que seu aplicativo faça algo útil quando o usuário clicar no botão.</span><span class="sxs-lookup"><span data-stu-id="a8280-104">For example, you might subscribe to a button's `click` event in order to make your application do something useful when the user clicks the button.</span></span>  
  
### <a name="to-subscribe-to-events-by-using-the-visual-studio-ide"></a><span data-ttu-id="a8280-105">Para assinar eventos usando o IDE do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a8280-105">To subscribe to events by using the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="a8280-106">Se você não vir a janela **Propriedades**, no modo de exibição de **Design**, clique com o botão direito do mouse no formulário ou controle para o qual deseja criar um manipulador de eventos e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="a8280-106">If you cannot see the **Properties** window, in **Design** view, right-click the form or control for which you want to create an event handler, and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="a8280-107">Na parte superior da janela **Propriedades**, clique no ícone **Eventos**.</span><span class="sxs-lookup"><span data-stu-id="a8280-107">On top of the **Properties** window, click the **Events** icon.</span></span>  
  
3.  <span data-ttu-id="a8280-108">Clique duas vezes no evento que deseja criar, por exemplo, o evento `Load`.</span><span class="sxs-lookup"><span data-stu-id="a8280-108">Double-click the event that you want to create, for example the `Load` event.</span></span>  
  
     [!INCLUDE[csprcs](~/includes/csprcs-md.md)]<span data-ttu-id="a8280-109"> cria um método de manipulador de eventos vazio e o adiciona ao seu código.</span><span class="sxs-lookup"><span data-stu-id="a8280-109"> creates an empty event handler method and adds it to your code.</span></span> <span data-ttu-id="a8280-110">Como alternativa, você pode adicionar o código manualmente no modo de exibição **Código**.</span><span class="sxs-lookup"><span data-stu-id="a8280-110">Alternatively you can add the code manually in **Code** view.</span></span> <span data-ttu-id="a8280-111">Por exemplo, as linhas de código a seguir declaram um método de manipulador de eventos que será chamado quando a classe `Form` gerar o evento `Load`.</span><span class="sxs-lookup"><span data-stu-id="a8280-111">For example, the following lines of code declare an event handler method that will be called when the `Form` class raises the `Load` event.</span></span>  
  
     <span data-ttu-id="a8280-112">[!code-cs[csProgGuideEvents#11](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-subscribe-to-and-unsubscribe-from-events_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="a8280-112">[!code-cs[csProgGuideEvents#11](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-subscribe-to-and-unsubscribe-from-events_1.cs)]</span></span>  
  
     <span data-ttu-id="a8280-113">A linha de código que é necessária para assinar o evento também é gerada automaticamente no método `InitializeComponent` no arquivo Form1.Designer.cs em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="a8280-113">The line of code that is required to subscribe to the event is also automatically generated in the `InitializeComponent` method in the Form1.Designer.cs file in your project.</span></span> <span data-ttu-id="a8280-114">Ele é semelhante a isto:</span><span class="sxs-lookup"><span data-stu-id="a8280-114">It resembles this:</span></span>  
  
    ```  
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
### <a name="to-subscribe-to-events-programmatically"></a><span data-ttu-id="a8280-115">Para assinar eventos de forma programática</span><span class="sxs-lookup"><span data-stu-id="a8280-115">To subscribe to events programmatically</span></span>  
  
1.  <span data-ttu-id="a8280-116">Defina um método de manipulador de eventos cuja assinatura corresponda à assinatura do delegado do evento.</span><span class="sxs-lookup"><span data-stu-id="a8280-116">Define an event handler method whose signature matches the delegate signature for the event.</span></span> <span data-ttu-id="a8280-117">Por exemplo, se o evento se basear no tipo de delegado <xref:System.EventHandler>, o código a seguir representará o stub do método:</span><span class="sxs-lookup"><span data-stu-id="a8280-117">For example, if the event is based on the <xref:System.EventHandler> delegate type, the following code represents the method stub:</span></span>  
  
    ```  
    void HandleCustomEvent(object sender, CustomEventArgs a)  
    {  
       // Do something useful here.  
    }  
    ```  
  
2.  <span data-ttu-id="a8280-118">Use o operador de atribuição de adição (`+=`) para anexar seu manipulador de eventos ao evento.</span><span class="sxs-lookup"><span data-stu-id="a8280-118">Use the addition assignment operator (`+=`) to attach your event handler to the event.</span></span> <span data-ttu-id="a8280-119">No exemplo a seguir, suponha que um objeto chamado `publisher` tem um evento chamado `RaiseCustomEvent`.</span><span class="sxs-lookup"><span data-stu-id="a8280-119">In the following example, assume that an object named `publisher` has an event named `RaiseCustomEvent`.</span></span> <span data-ttu-id="a8280-120">Observe que a classe do assinante precisa de uma referência à classe do editor para assinar seus eventos.</span><span class="sxs-lookup"><span data-stu-id="a8280-120">Note that the subscriber class needs a reference to the publisher class in order to subscribe to its events.</span></span>  
  
    ```  
    publisher.RaiseCustomEvent += HandleCustomEvent;  
    ```  
  
     <span data-ttu-id="a8280-121">Observe que a sintaxe anterior é nova no C# 2.0.</span><span class="sxs-lookup"><span data-stu-id="a8280-121">Note that the previous syntax is new in C# 2.0.</span></span> <span data-ttu-id="a8280-122">Ela é exatamente equivalente à sintaxe C# 1.0, em que o delegado de encapsulamento deve ser criado explicitamente usando a palavra-chave `new`:</span><span class="sxs-lookup"><span data-stu-id="a8280-122">It is exactly equivalent to the C# 1.0 syntax in which the encapsulating delegate must be explicitly created by using the `new` keyword:</span></span>  
  
    ```  
    publisher.RaiseCustomEvent += new CustomEventHandler(HandleCustomEvent);  
    ```  
  
     <span data-ttu-id="a8280-123">Um manipulador de eventos também pode ser adicionado usando uma expressão lambda:</span><span class="sxs-lookup"><span data-stu-id="a8280-123">An event handler can also be added by using a lambda expression:</span></span>  
  
    ```  
    public Form1()  
    {  
        InitializeComponent();  
        // Use a lambda expression to define an event handler.  
        this.Click += (s,e) => { MessageBox.Show(  
           ((MouseEventArgs)e).Location.ToString());};  
    }  
    ```  
  
     <span data-ttu-id="a8280-124">Para obter mais informações, consulte [Como usar expressões lambda fora do LINQ (C#)](../../../csharp/programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-outside-linq.md).</span><span class="sxs-lookup"><span data-stu-id="a8280-124">For more information, see [How to: Use Lambda Expressions Outside LINQ](../../../csharp/programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-outside-linq.md).</span></span>  
  
### <a name="to-subscribe-to-events-by-using-an-anonymous-method"></a><span data-ttu-id="a8280-125">Para assinar eventos usando um método anônimo</span><span class="sxs-lookup"><span data-stu-id="a8280-125">To subscribe to events by using an anonymous method</span></span>  
  
-   <span data-ttu-id="a8280-126">Se não precisar cancelar a assinatura de um evento posteriormente, você pode usar o operador de atribuição de adição (`+=`) para anexar um método anônimo ao evento.</span><span class="sxs-lookup"><span data-stu-id="a8280-126">If you will not have to unsubscribe to an event later, you can use the addition assignment operator (`+=`) to attach an anonymous method to the event.</span></span> <span data-ttu-id="a8280-127">No exemplo a seguir, suponha que um objeto chamado `publisher` tenha um evento chamado `RaiseCustomEvent` e que uma classe `CustomEventArgs` também tenha sido definida para conter algum tipo de informação de evento específico.</span><span class="sxs-lookup"><span data-stu-id="a8280-127">In the following example, assume that an object named `publisher` has an event named `RaiseCustomEvent` and that a `CustomEventArgs` class has also been defined to carry some kind of specialized event information.</span></span> <span data-ttu-id="a8280-128">Observe que a classe do assinante precisa de uma referência a `publisher` para assinar seus eventos.</span><span class="sxs-lookup"><span data-stu-id="a8280-128">Note that the subscriber class needs a reference to `publisher` in order to subscribe to its events.</span></span>  
  
    ```  
    publisher.RaiseCustomEvent += delegate(object o, CustomEventArgs e)  
    {  
      string s = o.ToString() + " " + e.ToString();  
      Console.WriteLine(s);  
    };  
    ```  
  
     <span data-ttu-id="a8280-129">É importante observar que você não pode, com facilidade, cancelar a assinatura de um evento se tiver usado uma função anônima para assiná-lo.</span><span class="sxs-lookup"><span data-stu-id="a8280-129">It is important to notice that you cannot easily unsubscribe from an event if you used an anonymous function to subscribe to it.</span></span> <span data-ttu-id="a8280-130">Para cancelar a assinatura nesse cenário, é necessário voltar ao código em que você assinou o evento, armazenar o método anônimo em uma variável do delegado e, então, adicionar o delegado ao evento.</span><span class="sxs-lookup"><span data-stu-id="a8280-130">To unsubscribe in this scenario, it is necessary to go back to the code where you subscribe to the event, store the anonymous method in a delegate variable, and then add the delegate to the event.</span></span> <span data-ttu-id="a8280-131">De modo geral, é recomendável que você não use funções anônimas para assinar eventos se precisar cancelar a assinatura do evento posteriormente no código.</span><span class="sxs-lookup"><span data-stu-id="a8280-131">In general, we recommend that you do not use anonymous functions to subscribe to events if you will have to unsubscribe from the event at some later point in your code.</span></span> <span data-ttu-id="a8280-132">Para obter mais informações sobre funções anônimas, consulte [Funções anônimas](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span><span class="sxs-lookup"><span data-stu-id="a8280-132">For more information about anonymous functions, see [Anonymous Functions](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span></span>  
  
## <a name="unsubscribing"></a><span data-ttu-id="a8280-133">Cancelando a assinatura</span><span class="sxs-lookup"><span data-stu-id="a8280-133">Unsubscribing</span></span>  
 <span data-ttu-id="a8280-134">Para impedir que o manipulador de eventos seja invocado quando o evento for gerado, cancele a assinatura do evento.</span><span class="sxs-lookup"><span data-stu-id="a8280-134">To prevent your event handler from being invoked when the event is raised, unsubscribe from the event.</span></span> <span data-ttu-id="a8280-135">Para evitar perda de recursos, cancele a assinatura de eventos antes de descartar um objeto de assinante.</span><span class="sxs-lookup"><span data-stu-id="a8280-135">In order to prevent resource leaks, you should unsubscribe from events before you dispose of a subscriber object.</span></span> <span data-ttu-id="a8280-136">Até que você cancele a assinatura de um evento, o delegado multicast subjacente ao evento no objeto de publicação terá uma referência ao delegado que encapsula o manipulador de eventos do assinante.</span><span class="sxs-lookup"><span data-stu-id="a8280-136">Until you unsubscribe from an event, the multicast delegate that underlies the event in the publishing object has a reference to the delegate that encapsulates the subscriber's event handler.</span></span> <span data-ttu-id="a8280-137">Desde que o objeto de publicação contenha essa referência, a coleta de lixo não excluirá seu objeto de assinante.</span><span class="sxs-lookup"><span data-stu-id="a8280-137">As long as the publishing object holds that reference, garbage collection will not delete your subscriber object.</span></span>  
  
#### <a name="to-unsubscribe-from-an-event"></a><span data-ttu-id="a8280-138">Para cancelar a assinatura de um evento</span><span class="sxs-lookup"><span data-stu-id="a8280-138">To unsubscribe from an event</span></span>  
  
-   <span data-ttu-id="a8280-139">Use o operador de atribuição de subtração (`-=`) para cancelar a assinatura de um evento:</span><span class="sxs-lookup"><span data-stu-id="a8280-139">Use the subtraction assignment operator (`-=`) to unsubscribe from an event:</span></span>  
  
    ```  
    publisher.RaiseCustomEvent -= HandleCustomEvent;  
    ```  
  
     <span data-ttu-id="a8280-140">Quando todos os assinantes tiverem cancelado a assinatura de um evento, a instância do evento na classe do publicador será definida como `null`.</span><span class="sxs-lookup"><span data-stu-id="a8280-140">When all subscribers have unsubscribed from an event, the event instance in the publisher class is set to `null`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8280-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a8280-141">See Also</span></span>  
 <span data-ttu-id="a8280-142">[Eventos](../../../csharp/programming-guide/events/index.md) </span><span class="sxs-lookup"><span data-stu-id="a8280-142">[Events](../../../csharp/programming-guide/events/index.md) </span></span>  
 <span data-ttu-id="a8280-143">[event](../../../csharp/language-reference/keywords/event.md) </span><span class="sxs-lookup"><span data-stu-id="a8280-143">[event](../../../csharp/language-reference/keywords/event.md) </span></span>  
 <span data-ttu-id="a8280-144">[Como publicar eventos em conformidade com as diretrizes do .NET Framework](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md) </span><span class="sxs-lookup"><span data-stu-id="a8280-144">[How to: Publish Events that Conform to .NET Framework Guidelines](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md) </span></span>  
 <span data-ttu-id="a8280-145">[Operador -= (Referência de C#)](../../language-reference/operators/subtraction-assignment-operator.md) </span><span class="sxs-lookup"><span data-stu-id="a8280-145">[-= Operator (C# Reference)](../../language-reference/operators/subtraction-assignment-operator.md) </span></span>  
 [<span data-ttu-id="a8280-146">Operador +=</span><span class="sxs-lookup"><span data-stu-id="a8280-146">+= Operator</span></span>](../../../csharp/language-reference/operators/addition-assignment-operator.md)

