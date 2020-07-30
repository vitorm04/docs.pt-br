---
title: Publicar eventos que estão em conformidade com as diretrizes do .NET – guia de programação C#
description: Saiba como publicar eventos que estão em conformidade com as diretrizes do .NET. Todos os eventos na biblioteca de classes de .NET Framework são baseados no delegado EventHandler.
ms.date: 05/26/2020
helpviewer_keywords:
- events [C#], implementation guidelines
ms.assetid: 9310ae16-8627-44a2-b08c-05e5976202b1
ms.openlocfilehash: 1b802e236026911b55bafcb3f48d487c43bba174
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302107"
---
# <a name="how-to-publish-events-that-conform-to-net-guidelines-c-programming-guide"></a><span data-ttu-id="1a6ac-104">Como publicar eventos que estão em conformidade com as diretrizes do .NET (guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="1a6ac-104">How to publish events that conform to .NET Guidelines (C# Programming Guide)</span></span>

<span data-ttu-id="1a6ac-105">O procedimento a seguir demonstra como adicionar eventos que seguem o padrão .NET padrão para suas classes e estruturas.</span><span class="sxs-lookup"><span data-stu-id="1a6ac-105">The following procedure demonstrates how to add events that follow the standard .NET pattern to your classes and structs.</span></span> <span data-ttu-id="1a6ac-106">Todos os eventos na biblioteca de classes do .NET Framework se baseiam no delegado <xref:System.EventHandler>, que é definido da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="1a6ac-106">All events in the .NET Framework class library are based on the <xref:System.EventHandler> delegate, which is defined as follows:</span></span>

```csharp
public delegate void EventHandler(object sender, EventArgs e);
```

> [!NOTE]
> <span data-ttu-id="1a6ac-107">.NET Framework 2,0 apresenta uma versão genérica desse delegado, <xref:System.EventHandler%601> .</span><span class="sxs-lookup"><span data-stu-id="1a6ac-107">.NET Framework 2.0 introduces a generic version of this delegate, <xref:System.EventHandler%601>.</span></span> <span data-ttu-id="1a6ac-108">Os exemplos a seguir mostram como usar as duas versões.</span><span class="sxs-lookup"><span data-stu-id="1a6ac-108">The following examples show how to use both versions.</span></span>

<span data-ttu-id="1a6ac-109">Embora eventos em classes que você define possam ser baseados em qualquer tipo delegado válido, até mesmo delegados que retornam um valor, geralmente é recomendável que você baseie seus eventos no padrão .NET usando <xref:System.EventHandler> , conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="1a6ac-109">Although events in classes that you define can be based on any valid delegate type, even delegates that return a value, it is generally recommended that you base your events on the .NET pattern by using <xref:System.EventHandler>, as shown in the following example.</span></span>

<span data-ttu-id="1a6ac-110">O nome `EventHandler` pode levar a um pouco de confusão, pois ela não lida realmente com o evento.</span><span class="sxs-lookup"><span data-stu-id="1a6ac-110">The name `EventHandler` can lead to a bit of confusion as it doesn't actually handle the event.</span></span> <span data-ttu-id="1a6ac-111">Os <xref:System.EventHandler> genéricos, e <xref:System.EventHandler%601> são tipos delegados.</span><span class="sxs-lookup"><span data-stu-id="1a6ac-111">The <xref:System.EventHandler>, and generic <xref:System.EventHandler%601> are delegate types.</span></span> <span data-ttu-id="1a6ac-112">Um método ou uma expressão lambda cuja assinatura corresponde à definição de delegado é o *manipulador de eventos* e será invocado quando o evento for gerado.</span><span class="sxs-lookup"><span data-stu-id="1a6ac-112">A method or lambda expression whose signature matches the delegate definition is the *event handler* and will be invoked when the event is raised.</span></span>

## <a name="publish-events-based-on-the-eventhandler-pattern"></a><span data-ttu-id="1a6ac-113">Publicar eventos com base no padrão EventHandler</span><span class="sxs-lookup"><span data-stu-id="1a6ac-113">Publish events based on the EventHandler pattern</span></span>

1. <span data-ttu-id="1a6ac-114">(Pule esta etapa e vá para a etapa 3a se você não precisar enviar dados personalizados com seu evento.) Declare a classe para seus dados personalizados em um escopo que seja visível para as classes de Publicador e de assinante.</span><span class="sxs-lookup"><span data-stu-id="1a6ac-114">(Skip this step and go to Step 3a if you do not have to send custom data with your event.) Declare the class for your custom data at a scope that is visible to both your publisher and subscriber classes.</span></span> <span data-ttu-id="1a6ac-115">Em seguida, adicione os membros necessários para manter seus dados de evento personalizados.</span><span class="sxs-lookup"><span data-stu-id="1a6ac-115">Then add the required members to hold your custom event data.</span></span> <span data-ttu-id="1a6ac-116">Neste exemplo, uma cadeia de caracteres simples é retornada.</span><span class="sxs-lookup"><span data-stu-id="1a6ac-116">In this example, a simple string is returned.</span></span>

    ```csharp
    public class CustomEventArgs : EventArgs
    {
        public CustomEventArgs(string message)
        {
            Message = message;
        }

        public string Message { get; set; }
    }
    ```

2. <span data-ttu-id="1a6ac-117">(Ignore esta etapa se você estiver usando a versão genérica do <xref:System.EventHandler%601> .) Declare um delegado em sua classe de publicação.</span><span class="sxs-lookup"><span data-stu-id="1a6ac-117">(Skip this step if you are using the generic version of <xref:System.EventHandler%601>.) Declare a delegate in your publishing class.</span></span> <span data-ttu-id="1a6ac-118">Dê um nome que termine com `EventHandler` .</span><span class="sxs-lookup"><span data-stu-id="1a6ac-118">Give it a name that ends with `EventHandler`.</span></span> <span data-ttu-id="1a6ac-119">O segundo parâmetro especifica o `EventArgs` tipo personalizado.</span><span class="sxs-lookup"><span data-stu-id="1a6ac-119">The second parameter specifies your custom `EventArgs` type.</span></span>

    ```csharp
    public delegate void CustomEventHandler(object sender, CustomEventArgs args);
    ```

3. <span data-ttu-id="1a6ac-120">Declare o evento em sua classe de publicação, usando uma das etapas a seguir.</span><span class="sxs-lookup"><span data-stu-id="1a6ac-120">Declare the event in your publishing class by using one of the following steps.</span></span>

    1. <span data-ttu-id="1a6ac-121">Se você não tiver uma classe EventArgs personalizada, o tipo de evento será o delegado EventHandler não genérico.</span><span class="sxs-lookup"><span data-stu-id="1a6ac-121">If you have no custom EventArgs class, your Event type will be the non-generic EventHandler delegate.</span></span> <span data-ttu-id="1a6ac-122">Você não precisa declarar o delegado porque ele já está declarado no namespace <xref:System> que está incluído quando você cria seu projeto do C#.</span><span class="sxs-lookup"><span data-stu-id="1a6ac-122">You do not have to declare the delegate because it is already declared in the <xref:System> namespace that is included when you create your C# project.</span></span> <span data-ttu-id="1a6ac-123">Adicione o seguinte código à sua classe publicadora.</span><span class="sxs-lookup"><span data-stu-id="1a6ac-123">Add the following code to your publisher class.</span></span>

        ```csharp
        public event EventHandler RaiseCustomEvent;
        ```

    2. <span data-ttu-id="1a6ac-124">Se você estiver usando a versão não genérica de <xref:System.EventHandler> e você tem uma classe personalizada derivada de <xref:System.EventArgs>, declare o evento dentro de sua classe de publicação e use o delegado da etapa 2 como o tipo.</span><span class="sxs-lookup"><span data-stu-id="1a6ac-124">If you are using the non-generic version of <xref:System.EventHandler> and you have a custom class derived from <xref:System.EventArgs>, declare your event inside your publishing class and use your delegate from step 2 as the type.</span></span>

        ```csharp
        public event CustomEventHandler RaiseCustomEvent;
        ```

    3. <span data-ttu-id="1a6ac-125">Se você estiver usando a versão genérica, não é necessário um delegado personalizado.</span><span class="sxs-lookup"><span data-stu-id="1a6ac-125">If you are using the generic version, you do not need a custom delegate.</span></span> <span data-ttu-id="1a6ac-126">Em vez disso, na sua classe de publicação, especifique o tipo de evento como `EventHandler<CustomEventArgs>`, substituindo o nome da sua própria classe entre os colchetes angulares.</span><span class="sxs-lookup"><span data-stu-id="1a6ac-126">Instead, in your publishing class, you specify your event type as `EventHandler<CustomEventArgs>`, substituting the name of your own class between the angle brackets.</span></span>

        ```csharp
        public event EventHandler<CustomEventArgs> RaiseCustomEvent;
        ```

## <a name="example"></a><span data-ttu-id="1a6ac-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1a6ac-127">Example</span></span>

<span data-ttu-id="1a6ac-128">O exemplo a seguir demonstra as etapas anteriores, usando uma classe EventArgs personalizada e o <xref:System.EventHandler%601> como o tipo de evento.</span><span class="sxs-lookup"><span data-stu-id="1a6ac-128">The following example demonstrates the previous steps by using a custom EventArgs class and <xref:System.EventHandler%601> as the event type.</span></span>

[!code-csharp[csProgGuideEvents#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#2)]

## <a name="see-also"></a><span data-ttu-id="1a6ac-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="1a6ac-129">See also</span></span>

- <xref:System.Delegate>
- [<span data-ttu-id="1a6ac-130">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="1a6ac-130">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="1a6ac-131">Eventos</span><span class="sxs-lookup"><span data-stu-id="1a6ac-131">Events</span></span>](index.md)
- [<span data-ttu-id="1a6ac-132">Representantes</span><span class="sxs-lookup"><span data-stu-id="1a6ac-132">Delegates</span></span>](../delegates/index.md)
