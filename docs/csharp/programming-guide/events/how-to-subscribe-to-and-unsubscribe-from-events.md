---
title: Como assinar e cancelar a assinatura de eventos – C# guia de programação
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- event handlers [C#], creating
- Code Editor, event handlers
- events [C#], creating using the IDE
ms.assetid: 6319f39f-282c-4173-8a62-6c4657cf51cd
ms.openlocfilehash: e194501d7619d4bc04dec6a10d34fb2b01be2c7a
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346309"
---
# <a name="how-to-subscribe-to-and-unsubscribe-from-events-c-programming-guide"></a><span data-ttu-id="616b4-102">Como assinar e cancelar a assinatura de eventos (C# guia de programação)</span><span class="sxs-lookup"><span data-stu-id="616b4-102">How to subscribe to and unsubscribe from events (C# Programming Guide)</span></span>
<span data-ttu-id="616b4-103">Você assina um evento publicado por outra classe quando quer escrever um código personalizado que é chamado quando esse evento é gerado.</span><span class="sxs-lookup"><span data-stu-id="616b4-103">You subscribe to an event that is published by another class when you want to write custom code that is called when that event is raised.</span></span> <span data-ttu-id="616b4-104">Por exemplo, você pode assinar o evento `click` de um botão para fazer com que seu aplicativo faça algo útil quando o usuário clicar no botão.</span><span class="sxs-lookup"><span data-stu-id="616b4-104">For example, you might subscribe to a button's `click` event in order to make your application do something useful when the user clicks the button.</span></span>  
  
### <a name="to-subscribe-to-events-by-using-the-visual-studio-ide"></a><span data-ttu-id="616b4-105">Para assinar eventos usando o IDE do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="616b4-105">To subscribe to events by using the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="616b4-106">Se você não vir a janela **Propriedades**, no modo de exibição de **Design**, clique com o botão direito do mouse no formulário ou controle para o qual deseja criar um manipulador de eventos e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="616b4-106">If you cannot see the **Properties** window, in **Design** view, right-click the form or control for which you want to create an event handler, and select **Properties**.</span></span>  
  
2. <span data-ttu-id="616b4-107">Na parte superior da janela **Propriedades**, clique no ícone **Eventos**.</span><span class="sxs-lookup"><span data-stu-id="616b4-107">On top of the **Properties** window, click the **Events** icon.</span></span>  
  
3. <span data-ttu-id="616b4-108">Clique duas vezes no evento que deseja criar, por exemplo, o evento `Load`.</span><span class="sxs-lookup"><span data-stu-id="616b4-108">Double-click the event that you want to create, for example the `Load` event.</span></span>  
  
     <span data-ttu-id="616b4-109">O Visual C# cria um método de manipulador de eventos vazio e adiciona-o ao código.</span><span class="sxs-lookup"><span data-stu-id="616b4-109">Visual C# creates an empty event handler method and adds it to your code.</span></span> <span data-ttu-id="616b4-110">Como alternativa, você pode adicionar o código manualmente no modo de exibição **Código**.</span><span class="sxs-lookup"><span data-stu-id="616b4-110">Alternatively you can add the code manually in **Code** view.</span></span> <span data-ttu-id="616b4-111">Por exemplo, as linhas de código a seguir declaram um método de manipulador de eventos que será chamado quando a classe `Form` gerar o evento `Load`.</span><span class="sxs-lookup"><span data-stu-id="616b4-111">For example, the following lines of code declare an event handler method that will be called when the `Form` class raises the `Load` event.</span></span>  
  
     [!code-csharp[csProgGuideEvents#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#11)]  
  
     <span data-ttu-id="616b4-112">A linha de código que é necessária para assinar o evento também é gerada automaticamente no método `InitializeComponent` no arquivo Form1.Designer.cs em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="616b4-112">The line of code that is required to subscribe to the event is also automatically generated in the `InitializeComponent` method in the Form1.Designer.cs file in your project.</span></span> <span data-ttu-id="616b4-113">Ele é semelhante a isto:</span><span class="sxs-lookup"><span data-stu-id="616b4-113">It resembles this:</span></span>  
  
    ```csharp
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
### <a name="to-subscribe-to-events-programmatically"></a><span data-ttu-id="616b4-114">Para assinar eventos de forma programática</span><span class="sxs-lookup"><span data-stu-id="616b4-114">To subscribe to events programmatically</span></span>  
  
1. <span data-ttu-id="616b4-115">Defina um método de manipulador de eventos cuja assinatura corresponda à assinatura do delegado do evento.</span><span class="sxs-lookup"><span data-stu-id="616b4-115">Define an event handler method whose signature matches the delegate signature for the event.</span></span> <span data-ttu-id="616b4-116">Por exemplo, se o evento se basear no tipo de delegado <xref:System.EventHandler>, o código a seguir representará o stub do método:</span><span class="sxs-lookup"><span data-stu-id="616b4-116">For example, if the event is based on the <xref:System.EventHandler> delegate type, the following code represents the method stub:</span></span>  
  
    ```csharp
    void HandleCustomEvent(object sender, CustomEventArgs a)  
    {  
       // Do something useful here.  
    }  
    ```  
  
2. <span data-ttu-id="616b4-117">Use o operador de atribuição de adição (`+=`) para anexar um manipulador de eventos ao evento.</span><span class="sxs-lookup"><span data-stu-id="616b4-117">Use the addition assignment operator (`+=`) to attach an event handler to the event.</span></span> <span data-ttu-id="616b4-118">No exemplo a seguir, suponha que um objeto chamado `publisher` tem um evento chamado `RaiseCustomEvent`.</span><span class="sxs-lookup"><span data-stu-id="616b4-118">In the following example, assume that an object named `publisher` has an event named `RaiseCustomEvent`.</span></span> <span data-ttu-id="616b4-119">Observe que a classe do assinante precisa de uma referência à classe do editor para assinar seus eventos.</span><span class="sxs-lookup"><span data-stu-id="616b4-119">Note that the subscriber class needs a reference to the publisher class in order to subscribe to its events.</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += HandleCustomEvent;  
    ```  
  
     <span data-ttu-id="616b4-120">Observe que a sintaxe anterior é nova no C# 2.0.</span><span class="sxs-lookup"><span data-stu-id="616b4-120">Note that the previous syntax is new in C# 2.0.</span></span> <span data-ttu-id="616b4-121">Ela é exatamente equivalente à sintaxe C# 1.0, em que o delegado de encapsulamento deve ser criado explicitamente usando a palavra-chave `new`:</span><span class="sxs-lookup"><span data-stu-id="616b4-121">It is exactly equivalent to the C# 1.0 syntax in which the encapsulating delegate must be explicitly created by using the `new` keyword:</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += new CustomEventHandler(HandleCustomEvent);  
    ```  
  
     <span data-ttu-id="616b4-122">Você também pode usar uma [expressão lambda](../statements-expressions-operators/lambda-expressions.md) para especificar um manipulador de eventos:</span><span class="sxs-lookup"><span data-stu-id="616b4-122">You also can use a [lambda expression](../statements-expressions-operators/lambda-expressions.md) to specify an event handler:</span></span>
  
    ```csharp
    public Form1()  
    {  
        InitializeComponent();  
        this.Click += (s,e) =>
            {
                MessageBox.Show(((MouseEventArgs)e).Location.ToString());
            };
    }  
    ```  
  
### <a name="to-subscribe-to-events-by-using-an-anonymous-method"></a><span data-ttu-id="616b4-123">Para assinar eventos usando um método anônimo</span><span class="sxs-lookup"><span data-stu-id="616b4-123">To subscribe to events by using an anonymous method</span></span>  
  
- <span data-ttu-id="616b4-124">Se não precisar cancelar a assinatura de um evento posteriormente, você pode usar o operador de atribuição de adição (`+=`) para anexar um método anônimo ao evento.</span><span class="sxs-lookup"><span data-stu-id="616b4-124">If you will not have to unsubscribe to an event later, you can use the addition assignment operator (`+=`) to attach an anonymous method to the event.</span></span> <span data-ttu-id="616b4-125">No exemplo a seguir, suponha que um objeto chamado `publisher` tenha um evento chamado `RaiseCustomEvent` e que uma classe `CustomEventArgs` também tenha sido definida para conter algum tipo de informação de evento específico.</span><span class="sxs-lookup"><span data-stu-id="616b4-125">In the following example, assume that an object named `publisher` has an event named `RaiseCustomEvent` and that a `CustomEventArgs` class has also been defined to carry some kind of specialized event information.</span></span> <span data-ttu-id="616b4-126">Observe que a classe do assinante precisa de uma referência a `publisher` para assinar seus eventos.</span><span class="sxs-lookup"><span data-stu-id="616b4-126">Note that the subscriber class needs a reference to `publisher` in order to subscribe to its events.</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += delegate(object o, CustomEventArgs e)  
    {  
      string s = o.ToString() + " " + e.ToString();  
      Console.WriteLine(s);  
    };  
    ```  
  
     <span data-ttu-id="616b4-127">É importante observar que você não pode, com facilidade, cancelar a assinatura de um evento se tiver usado uma função anônima para assiná-lo.</span><span class="sxs-lookup"><span data-stu-id="616b4-127">It is important to notice that you cannot easily unsubscribe from an event if you used an anonymous function to subscribe to it.</span></span> <span data-ttu-id="616b4-128">Para cancelar a assinatura nesse cenário, é necessário voltar ao código em que você assinou o evento, armazenar o método anônimo em uma variável do delegado e, então, adicionar o delegado ao evento.</span><span class="sxs-lookup"><span data-stu-id="616b4-128">To unsubscribe in this scenario, it is necessary to go back to the code where you subscribe to the event, store the anonymous method in a delegate variable, and then add the delegate to the event.</span></span> <span data-ttu-id="616b4-129">De modo geral, é recomendável que você não use funções anônimas para assinar eventos se precisar cancelar a assinatura do evento posteriormente no código.</span><span class="sxs-lookup"><span data-stu-id="616b4-129">In general, we recommend that you do not use anonymous functions to subscribe to events if you will have to unsubscribe from the event at some later point in your code.</span></span> <span data-ttu-id="616b4-130">Para obter mais informações sobre funções anônimas, consulte [Funções anônimas](../statements-expressions-operators/anonymous-functions.md).</span><span class="sxs-lookup"><span data-stu-id="616b4-130">For more information about anonymous functions, see [Anonymous Functions](../statements-expressions-operators/anonymous-functions.md).</span></span>  
  
## <a name="unsubscribing"></a><span data-ttu-id="616b4-131">Cancelando a assinatura</span><span class="sxs-lookup"><span data-stu-id="616b4-131">Unsubscribing</span></span>  
 <span data-ttu-id="616b4-132">Para impedir que o manipulador de eventos seja invocado quando o evento for gerado, cancele a assinatura do evento.</span><span class="sxs-lookup"><span data-stu-id="616b4-132">To prevent your event handler from being invoked when the event is raised, unsubscribe from the event.</span></span> <span data-ttu-id="616b4-133">Para evitar perda de recursos, cancele a assinatura de eventos antes de descartar um objeto de assinante.</span><span class="sxs-lookup"><span data-stu-id="616b4-133">In order to prevent resource leaks, you should unsubscribe from events before you dispose of a subscriber object.</span></span> <span data-ttu-id="616b4-134">Até que você cancele a assinatura de um evento, o delegado multicast subjacente ao evento no objeto de publicação terá uma referência ao delegado que encapsula o manipulador de eventos do assinante.</span><span class="sxs-lookup"><span data-stu-id="616b4-134">Until you unsubscribe from an event, the multicast delegate that underlies the event in the publishing object has a reference to the delegate that encapsulates the subscriber's event handler.</span></span> <span data-ttu-id="616b4-135">Desde que o objeto de publicação contenha essa referência, a coleta de lixo não excluirá seu objeto de assinante.</span><span class="sxs-lookup"><span data-stu-id="616b4-135">As long as the publishing object holds that reference, garbage collection will not delete your subscriber object.</span></span>  
  
#### <a name="to-unsubscribe-from-an-event"></a><span data-ttu-id="616b4-136">Para cancelar a assinatura de um evento</span><span class="sxs-lookup"><span data-stu-id="616b4-136">To unsubscribe from an event</span></span>  
  
- <span data-ttu-id="616b4-137">Use o operador de atribuição de subtração (`-=`) para cancelar a assinatura de um evento:</span><span class="sxs-lookup"><span data-stu-id="616b4-137">Use the subtraction assignment operator (`-=`) to unsubscribe from an event:</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent -= HandleCustomEvent;  
    ```  
  
     <span data-ttu-id="616b4-138">Quando todos os assinantes tiverem cancelado a assinatura de um evento, a instância do evento na classe do publicador será definida como `null`.</span><span class="sxs-lookup"><span data-stu-id="616b4-138">When all subscribers have unsubscribed from an event, the event instance in the publisher class is set to `null`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="616b4-139">Veja também</span><span class="sxs-lookup"><span data-stu-id="616b4-139">See also</span></span>

- [<span data-ttu-id="616b4-140">Eventos</span><span class="sxs-lookup"><span data-stu-id="616b4-140">Events</span></span>](./index.md)
- [<span data-ttu-id="616b4-141">event</span><span class="sxs-lookup"><span data-stu-id="616b4-141">event</span></span>](../../language-reference/keywords/event.md)
- [<span data-ttu-id="616b4-142">Como publicar eventos que estão em conformidade com as diretrizes de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="616b4-142">How to publish events that conform to .NET Framework Guidelines</span></span>](./how-to-publish-events-that-conform-to-net-framework-guidelines.md)
- [<span data-ttu-id="616b4-143">Operadores - e -=</span><span class="sxs-lookup"><span data-stu-id="616b4-143">- and -= operators</span></span>](../../language-reference/operators/subtraction-operator.md)
- [<span data-ttu-id="616b4-144">Operadores + e +=</span><span class="sxs-lookup"><span data-stu-id="616b4-144">+ and += operators</span></span>](../../language-reference/operators/addition-operator.md)
