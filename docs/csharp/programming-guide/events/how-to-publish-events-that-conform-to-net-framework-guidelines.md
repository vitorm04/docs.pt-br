---
title: Como publicar eventos que estejam em conformidade com as Diretrizes-Quadro .NET - Guia de Programação C#
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], implementation guidelines
ms.assetid: 9310ae16-8627-44a2-b08c-05e5976202b1
ms.openlocfilehash: 90c079b9f7dbf2a1d963b7eee4447145d7a10432
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167514"
---
# <a name="how-to-publish-events-that-conform-to-net-framework-guidelines-c-programming-guide"></a><span data-ttu-id="aa5e4-102">Como publicar eventos que estejam em conformidade com as Diretrizes-Quadro .NET (Guia de Programação C#)</span><span class="sxs-lookup"><span data-stu-id="aa5e4-102">How to publish events that conform to .NET Framework Guidelines (C# Programming Guide)</span></span>
<span data-ttu-id="aa5e4-103">O procedimento a seguir demonstra como adicionar eventos que seguem o padrão do .NET Framework para classes e structs.</span><span class="sxs-lookup"><span data-stu-id="aa5e4-103">The following procedure demonstrates how to add events that follow the standard .NET Framework pattern to your classes and structs.</span></span> <span data-ttu-id="aa5e4-104">Todos os eventos na biblioteca de classes do .NET Framework se baseiam no delegado <xref:System.EventHandler>, que é definido da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="aa5e4-104">All events in the .NET Framework class library are based on the <xref:System.EventHandler> delegate, which is defined as follows:</span></span>  
  
```csharp  
public delegate void EventHandler(object sender, EventArgs e);  
```  
  
> [!NOTE]
> <span data-ttu-id="aa5e4-105">O .NET Framework 2.0 apresenta uma versão genérica desse delegado, o <xref:System.EventHandler%601>.</span><span class="sxs-lookup"><span data-stu-id="aa5e4-105">The .NET Framework 2.0 introduces a generic version of this delegate, <xref:System.EventHandler%601>.</span></span> <span data-ttu-id="aa5e4-106">Os exemplos a seguir mostram como usar as duas versões.</span><span class="sxs-lookup"><span data-stu-id="aa5e4-106">The following examples show how to use both versions.</span></span>  
  
 <span data-ttu-id="aa5e4-107">Embora os eventos nas classes que você define possam ser baseados em qualquer tipo delegado válido, até mesmo nos delegados que retornam um valor, é geralmente recomendável que você baseie seus eventos no padrão do .NET Framework usando o <xref:System.EventHandler>, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="aa5e4-107">Although events in classes that you define can be based on any valid delegate type, even delegates that return a value, it is generally recommended that you base your events on the .NET Framework pattern by using <xref:System.EventHandler>, as shown in the following example.</span></span>  
  
### <a name="to-publish-events-based-on-the-eventhandler-pattern"></a><span data-ttu-id="aa5e4-108">Para publicar eventos com base no padrão EventHandler</span><span class="sxs-lookup"><span data-stu-id="aa5e4-108">To publish events based on the EventHandler pattern</span></span>  
  
1. <span data-ttu-id="aa5e4-109">(Pule esta etapa e vá para a Etapa 3a se você não tiver que enviar dados personalizados com o seu evento.) Declare a classe para seus dados personalizados em um escopo visível para suas classes de editores e assinantes.</span><span class="sxs-lookup"><span data-stu-id="aa5e4-109">(Skip this step and go to Step 3a if you do not have to send custom data with your event.) Declare the class for your custom data at a scope that is visible to both your publisher and subscriber classes.</span></span> <span data-ttu-id="aa5e4-110">Em seguida, adicione os membros necessários para manter seus dados de evento personalizados.</span><span class="sxs-lookup"><span data-stu-id="aa5e4-110">Then add the required members to hold your custom event data.</span></span> <span data-ttu-id="aa5e4-111">Neste exemplo, uma cadeia de caracteres simples é retornada.</span><span class="sxs-lookup"><span data-stu-id="aa5e4-111">In this example, a simple string is returned.</span></span>  
  
    ```csharp  
    public class CustomEventArgs : EventArgs  
    {  
        public CustomEventArgs(string s)  
        {  
            msg = s;  
        }  
        private string msg;  
        public string Message  
        {  
            get { return msg; }  
        }
    }  
    ```  
  
2. <span data-ttu-id="aa5e4-112">(Pule esta etapa se estiver <xref:System.EventHandler%601> usando a versão genérica de .) Declare um delegado em sua aula de publicação.</span><span class="sxs-lookup"><span data-stu-id="aa5e4-112">(Skip this step if you are using the generic version of <xref:System.EventHandler%601> .) Declare a delegate in your publishing class.</span></span> <span data-ttu-id="aa5e4-113">Dê a ela um nome que termina com *EventHandler*.</span><span class="sxs-lookup"><span data-stu-id="aa5e4-113">Give it a name that ends with *EventHandler*.</span></span> <span data-ttu-id="aa5e4-114">O segundo parâmetro especifica o tipo personalizado de EventArgs.</span><span class="sxs-lookup"><span data-stu-id="aa5e4-114">The second parameter specifies your custom EventArgs type.</span></span>  
  
    ```csharp  
    public delegate void CustomEventHandler(object sender, CustomEventArgs a);  
    ```  
  
3. <span data-ttu-id="aa5e4-115">Declare o evento em sua classe de publicação, usando uma das etapas a seguir.</span><span class="sxs-lookup"><span data-stu-id="aa5e4-115">Declare the event in your publishing class by using one of the following steps.</span></span>  
  
    1. <span data-ttu-id="aa5e4-116">Se você não tiver uma classe EventArgs personalizada, o tipo de evento será o delegado EventHandler não genérico.</span><span class="sxs-lookup"><span data-stu-id="aa5e4-116">If you have no custom EventArgs class, your Event type will be the non-generic EventHandler delegate.</span></span> <span data-ttu-id="aa5e4-117">Você não precisa declarar o delegado porque ele já está declarado no namespace <xref:System> que está incluído quando você cria seu projeto do C#.</span><span class="sxs-lookup"><span data-stu-id="aa5e4-117">You do not have to declare the delegate because it is already declared in the <xref:System> namespace that is included when you create your C# project.</span></span> <span data-ttu-id="aa5e4-118">Adicione o seguinte código à sua classe publicadora.</span><span class="sxs-lookup"><span data-stu-id="aa5e4-118">Add the following code to your publisher class.</span></span>  
  
        ```csharp  
        public event EventHandler RaiseCustomEvent;  
        ```  
  
    2. <span data-ttu-id="aa5e4-119">Se você estiver usando a versão não genérica de <xref:System.EventHandler> e você tem uma classe personalizada derivada de <xref:System.EventArgs>, declare o evento dentro de sua classe de publicação e use o delegado da etapa 2 como o tipo.</span><span class="sxs-lookup"><span data-stu-id="aa5e4-119">If you are using the non-generic version of <xref:System.EventHandler> and you have a custom class derived from <xref:System.EventArgs>, declare your event inside your publishing class and use your delegate from step 2 as the type.</span></span>  
  
        ```csharp  
        public event CustomEventHandler RaiseCustomEvent;  
        ```  
  
    3. <span data-ttu-id="aa5e4-120">Se você estiver usando a versão genérica, não é necessário um delegado personalizado.</span><span class="sxs-lookup"><span data-stu-id="aa5e4-120">If you are using the generic version, you do not need a custom delegate.</span></span> <span data-ttu-id="aa5e4-121">Em vez disso, na sua classe de publicação, especifique o tipo de evento como `EventHandler<CustomEventArgs>`, substituindo o nome da sua própria classe entre os colchetes angulares.</span><span class="sxs-lookup"><span data-stu-id="aa5e4-121">Instead, in your publishing class, you specify your event type as `EventHandler<CustomEventArgs>`, substituting the name of your own class between the angle brackets.</span></span>  
  
        ```csharp  
        public event EventHandler<CustomEventArgs> RaiseCustomEvent;  
        ```  
  
## <a name="example"></a><span data-ttu-id="aa5e4-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="aa5e4-122">Example</span></span>  
 <span data-ttu-id="aa5e4-123">O exemplo a seguir demonstra as etapas anteriores, usando uma classe EventArgs personalizada e o <xref:System.EventHandler%601> como o tipo de evento.</span><span class="sxs-lookup"><span data-stu-id="aa5e4-123">The following example demonstrates the previous steps by using a custom EventArgs class and <xref:System.EventHandler%601> as the event type.</span></span>  
  
 [!code-csharp[csProgGuideEvents#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#2)]  
  
## <a name="see-also"></a><span data-ttu-id="aa5e4-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="aa5e4-124">See also</span></span>

- <xref:System.Delegate>
- [<span data-ttu-id="aa5e4-125">C# Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="aa5e4-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="aa5e4-126">Eventos</span><span class="sxs-lookup"><span data-stu-id="aa5e4-126">Events</span></span>](./index.md)
- [<span data-ttu-id="aa5e4-127">Delega</span><span class="sxs-lookup"><span data-stu-id="aa5e4-127">Delegates</span></span>](../delegates/index.md)
