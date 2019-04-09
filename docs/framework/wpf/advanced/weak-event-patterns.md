---
title: Padrões de evento fraco
ms.date: 03/30/2017
helpviewer_keywords:
- weak event pattern implementation [WPF]
- event handlers [WPF], weak event pattern
- IWeakEventListener interface [WPF]
ms.assetid: e7c62920-4812-4811-94d8-050a65c856f6
ms.openlocfilehash: 49795235d489ebc70cec11332e6be4a9452bc21d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59139250"
---
# <a name="weak-event-patterns"></a><span data-ttu-id="616f9-102">Padrões de evento fraco</span><span class="sxs-lookup"><span data-stu-id="616f9-102">Weak Event Patterns</span></span>
<span data-ttu-id="616f9-103">Em aplicativos, é possível que manipuladores que estão anexados a origens de eventos não sejam destruídos em coordenação com o objeto de ouvinte que anexou o manipulador à origem.</span><span class="sxs-lookup"><span data-stu-id="616f9-103">In applications, it is possible that handlers that are attached to event sources will not be destroyed in coordination with the listener object that attached the handler to the source.</span></span> <span data-ttu-id="616f9-104">Essa situação pode levar a vazamentos de memória.</span><span class="sxs-lookup"><span data-stu-id="616f9-104">This situation can lead to memory leaks.</span></span> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="616f9-105">apresenta um padrão de design que pode ser usado para resolver esse problema, fornecendo uma classe de gerenciamento dedicada para determinados eventos e implementando uma interface em ouvintes para o evento.</span><span class="sxs-lookup"><span data-stu-id="616f9-105">introduces a design pattern that can be used to address this issue, by providing a dedicated manager class for particular events and implementing an interface on listeners for that event.</span></span> <span data-ttu-id="616f9-106">Esse padrão de design é conhecido como o *padrão de evento fraco*.</span><span class="sxs-lookup"><span data-stu-id="616f9-106">This design pattern is known as the *weak event pattern*.</span></span>  
  
## <a name="why-implement-the-weak-event-pattern"></a><span data-ttu-id="616f9-107">Por que implementar o padrão de evento fraco?</span><span class="sxs-lookup"><span data-stu-id="616f9-107">Why Implement the Weak Event Pattern?</span></span>  
 <span data-ttu-id="616f9-108">Escutar eventos pode levar a vazamentos de memória.</span><span class="sxs-lookup"><span data-stu-id="616f9-108">Listening for events can lead to memory leaks.</span></span> <span data-ttu-id="616f9-109">A técnica comum para ouvir um evento é usar a sintaxe específica a um idioma que anexa um manipulador a um evento em uma fonte.</span><span class="sxs-lookup"><span data-stu-id="616f9-109">The typical technique for listening to an event is to use the language-specific syntax that attaches a handler to an event on a source.</span></span> <span data-ttu-id="616f9-110">Por exemplo, em C#, que a sintaxe é: `source.SomeEvent += new SomeEventHandler(MyEventHandler)`.</span><span class="sxs-lookup"><span data-stu-id="616f9-110">For example, in C#, that syntax is: `source.SomeEvent += new SomeEventHandler(MyEventHandler)`.</span></span>  
  
 <span data-ttu-id="616f9-111">Essa técnica cria uma referência forte da origem do evento para o ouvinte de eventos.</span><span class="sxs-lookup"><span data-stu-id="616f9-111">This technique creates a strong reference from the event source to the event listener.</span></span> <span data-ttu-id="616f9-112">Normalmente, anexar um manipulador de eventos para um ouvinte faz com que o ouvinte tenha um tempo de vida do objeto que é influenciado pelo tempo de vida do objeto da origem (a menos que o manipulador de eventos seja explicitamente removido).</span><span class="sxs-lookup"><span data-stu-id="616f9-112">Ordinarily, attaching an event handler for a listener causes the listener to have an object lifetime that is influenced by the object lifetime of the source (unless the event handler is explicitly removed).</span></span> <span data-ttu-id="616f9-113">Mas, em determinadas circunstâncias, você pode desejar que o tempo de vida do objeto do ouvinte seja controlado por outros fatores, como se ele pertencesse à árvore visual do aplicativo e não pelo tempo de vida de origem.</span><span class="sxs-lookup"><span data-stu-id="616f9-113">But in certain circumstances, you might want the object lifetime of the listener to be controlled by other factors, such as whether it currently belongs to the visual tree of the application, and not by the lifetime of the source.</span></span> <span data-ttu-id="616f9-114">Sempre que o tempo de vida do objeto de origem ultrapassa o tempo de vida do objeto do ouvinte, o padrão de eventos normal ocasiona um vazamento de memória: o ouvinte é mantido ativo mais que o previsto.</span><span class="sxs-lookup"><span data-stu-id="616f9-114">Whenever the source object lifetime extends beyond the object lifetime of the listener, the normal event pattern leads to a memory leak: the listener is kept alive longer than intended.</span></span>  
  
 <span data-ttu-id="616f9-115">O padrão de evento fraco é projetado para resolver esse problema de vazamento de memória.</span><span class="sxs-lookup"><span data-stu-id="616f9-115">The weak event pattern is designed to solve this memory leak problem.</span></span> <span data-ttu-id="616f9-116">O padrão de evento fraco pode ser usado sempre que um ouvinte precisa registrar um evento, mas não sabe explicitamente quando cancelar o registro.</span><span class="sxs-lookup"><span data-stu-id="616f9-116">The weak event pattern can be used whenever a listener needs to register for an event, but the listener does not explicitly know when to unregister.</span></span> <span data-ttu-id="616f9-117">O padrão de evento fraco também pode ser usado sempre que o tempo de vida do objeto de origem exceder o tempo de vida útil do objeto do ouvinte.</span><span class="sxs-lookup"><span data-stu-id="616f9-117">The weak event pattern can also be used whenever the object lifetime of the source exceeds the useful object lifetime of the listener.</span></span> <span data-ttu-id="616f9-118">(Nesse caso, o que é *útil* é determinado por você.) O padrão de evento fraco permite que o ouvinte registre e receba o evento sem afetar as características de tempo de vida do objeto do ouvinte.</span><span class="sxs-lookup"><span data-stu-id="616f9-118">(In this case, *useful* is determined by you.) The weak event pattern allows the listener to register for and receive the event without affecting the object lifetime characteristics of the listener in any way.</span></span> <span data-ttu-id="616f9-119">Na verdade, a referência implícita da origem não determina se o ouvinte está qualificado para coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="616f9-119">In effect, the implied reference from the source does not determine whether the listener is eligible for garbage collection.</span></span> <span data-ttu-id="616f9-120">A referência é uma referência fraca, por isso a nomenclatura de padrão de evento fraco e [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] relacionado.</span><span class="sxs-lookup"><span data-stu-id="616f9-120">The reference is a weak reference, thus the naming of the weak event pattern and the related [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)].</span></span> <span data-ttu-id="616f9-121">O ouvinte pode ter o lixo coletado ou destruído, e a origem pode continuar sem reter manipulador referências não colecionáveis do manipulador para um objeto agora destruído.</span><span class="sxs-lookup"><span data-stu-id="616f9-121">The listener can be garbage collected or otherwise destroyed, and the source can continue without retaining noncollectible handler references to a now destroyed object.</span></span>  
  
## <a name="who-should-implement-the-weak-event-pattern"></a><span data-ttu-id="616f9-122">Por que implementar o padrão de evento fraco?</span><span class="sxs-lookup"><span data-stu-id="616f9-122">Who Should Implement the Weak Event Pattern?</span></span>  
 <span data-ttu-id="616f9-123">Implementar o padrão de evento fraco é interessante principalmente para autores de controle.</span><span class="sxs-lookup"><span data-stu-id="616f9-123">Implementing the weak event pattern is interesting primarily for control authors.</span></span> <span data-ttu-id="616f9-124">Como um autor de controle, você é basicamente responsável pelo comportamento e confinamento de seu controle e o impacto em aplicativos em que ele é inserido.</span><span class="sxs-lookup"><span data-stu-id="616f9-124">As a control author, you are largely responsible for the behavior and containment of your control and the impact it has on applications in which it is inserted.</span></span> <span data-ttu-id="616f9-125">Isso inclui o comportamento de tempo de vida do objeto de controle, em particular, o tratamento do problema de vazamento de memória descrito.</span><span class="sxs-lookup"><span data-stu-id="616f9-125">This includes the control object lifetime behavior, in particular the handling of the described memory leak problem.</span></span>  
  
 <span data-ttu-id="616f9-126">Determinados cenários prestam-se inerentemente ao aplicativo do padrão de evento fraco.</span><span class="sxs-lookup"><span data-stu-id="616f9-126">Certain scenarios inherently lend themselves to the application of the weak event pattern.</span></span> <span data-ttu-id="616f9-127">Um cenário é a associação de dados.</span><span class="sxs-lookup"><span data-stu-id="616f9-127">One such scenario is data binding.</span></span> <span data-ttu-id="616f9-128">Na associação de dados, é comum que o objeto de origem seja completamente independente do objeto de ouvinte, que é um destino de uma associação.</span><span class="sxs-lookup"><span data-stu-id="616f9-128">In data binding, it is common for the source object to be completely independent of the listener object, which is a target of a binding.</span></span> <span data-ttu-id="616f9-129">Muitos aspectos da associação de dados [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] já têm o padrão de evento fraco aplicado em como os eventos são implementados.</span><span class="sxs-lookup"><span data-stu-id="616f9-129">Many aspects of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] data binding already have the weak event pattern applied in how the events are implemented.</span></span>  
  
## <a name="how-to-implement-the-weak-event-pattern"></a><span data-ttu-id="616f9-130">Como implementar o padrão de evento fraco</span><span class="sxs-lookup"><span data-stu-id="616f9-130">How to Implement the Weak Event Pattern</span></span>  
 <span data-ttu-id="616f9-131">Há três maneiras de implementar o padrão de evento fraco.</span><span class="sxs-lookup"><span data-stu-id="616f9-131">There are three ways to implement weak event pattern.</span></span> <span data-ttu-id="616f9-132">A tabela a seguir lista as três abordagens e fornece algumas diretrizes sobre quando usar cada uma.</span><span class="sxs-lookup"><span data-stu-id="616f9-132">The following table lists the three approaches and provides some guidance for when you should use each.</span></span>  
  
|<span data-ttu-id="616f9-133">Abordagem</span><span class="sxs-lookup"><span data-stu-id="616f9-133">Approach</span></span>|<span data-ttu-id="616f9-134">Quando implementar</span><span class="sxs-lookup"><span data-stu-id="616f9-134">When to Implement</span></span>|  
|--------------|-----------------------|  
|<span data-ttu-id="616f9-135">Usar uma classe existente de gerenciamento de evento fraco</span><span class="sxs-lookup"><span data-stu-id="616f9-135">Use an existing weak event manager class</span></span>|<span data-ttu-id="616f9-136">Se o evento que você deseja assinar tiver um correspondente <xref:System.Windows.WeakEventManager>, use o Gerenciador de evento fraco existente.</span><span class="sxs-lookup"><span data-stu-id="616f9-136">If the event you want to subscribe to has a corresponding <xref:System.Windows.WeakEventManager>, use the existing weak event manager.</span></span> <span data-ttu-id="616f9-137">Para obter uma lista de gerenciadores de evento fraco incluídos com o WPF, consulte a hierarquia de herança na <xref:System.Windows.WeakEventManager> classe.</span><span class="sxs-lookup"><span data-stu-id="616f9-137">For a list of weak event managers that are included with WPF, see the inheritance hierarchy in the <xref:System.Windows.WeakEventManager> class.</span></span> <span data-ttu-id="616f9-138">Como os gerenciadores de evento fraco incluídos são limitados, provavelmente você precisará escolher uma das outras abordagens.</span><span class="sxs-lookup"><span data-stu-id="616f9-138">Because the included weak event managers are limited, you will probably need to choose one of the other approaches.</span></span>|  
|<span data-ttu-id="616f9-139">Usar uma classe de gerenciador de evento fraco genérico</span><span class="sxs-lookup"><span data-stu-id="616f9-139">Use a generic weak event manager class</span></span>|<span data-ttu-id="616f9-140">Usar um genérico <xref:System.Windows.WeakEventManager%602> quando um existente <xref:System.Windows.WeakEventManager> está indisponível, você deseja uma maneira fácil de implementar, e você não estiver preocupado com eficiência.</span><span class="sxs-lookup"><span data-stu-id="616f9-140">Use a generic <xref:System.Windows.WeakEventManager%602> when an existing <xref:System.Windows.WeakEventManager> is not available, you want an easy way to implement, and you are not concerned about efficiency.</span></span> <span data-ttu-id="616f9-141">Genérica <xref:System.Windows.WeakEventManager%602> é menos eficiente do que um Gerenciador de evento fraco existente ou personalizado.</span><span class="sxs-lookup"><span data-stu-id="616f9-141">The generic <xref:System.Windows.WeakEventManager%602> is less efficient than an existing or custom weak event manager.</span></span> <span data-ttu-id="616f9-142">Por exemplo, a classe genérica faz mais reflexão para descobrir o evento que recebeu o nome do evento.</span><span class="sxs-lookup"><span data-stu-id="616f9-142">For example, the generic class does more reflection to discover the event given the event's name.</span></span> <span data-ttu-id="616f9-143">Além disso, o código para registrar o evento usando o genérico <xref:System.Windows.WeakEventManager%602> é mais detalhado do que usar um existente ou personalizado <xref:System.Windows.WeakEventManager>.</span><span class="sxs-lookup"><span data-stu-id="616f9-143">Also, the code to register the event by using the generic <xref:System.Windows.WeakEventManager%602> is more verbose than using an existing or custom <xref:System.Windows.WeakEventManager>.</span></span>|  
|<span data-ttu-id="616f9-144">Criar uma classe de gerenciador de evento fraco personalizado</span><span class="sxs-lookup"><span data-stu-id="616f9-144">Create a custom weak event manager class</span></span>|<span data-ttu-id="616f9-145">Criar um personalizado <xref:System.Windows.WeakEventManager> quando um existente <xref:System.Windows.WeakEventManager> não está disponível e você deseja a melhor eficiência.</span><span class="sxs-lookup"><span data-stu-id="616f9-145">Create a custom <xref:System.Windows.WeakEventManager> when an existing <xref:System.Windows.WeakEventManager> is not available and you want the best efficiency.</span></span> <span data-ttu-id="616f9-146">Usando um personalizado <xref:System.Windows.WeakEventManager> para assinar um evento será mais eficiente, mas você aumentará o custo de escrever um código no início.</span><span class="sxs-lookup"><span data-stu-id="616f9-146">Using a custom <xref:System.Windows.WeakEventManager> to subscribe to an event will be more efficient, but you do incur the cost of writing more code at the beginning.</span></span>|  
|<span data-ttu-id="616f9-147">Usar um Gerenciador de evento fraco de terceiros</span><span class="sxs-lookup"><span data-stu-id="616f9-147">Use a third-party weak event manager</span></span>|<span data-ttu-id="616f9-148">O NuGet tem [vários gerenciadores de evento fraco](https://www.nuget.org/packages?q=weak+event+manager&prerel=false) e várias estruturas WPF também suportam o padrão (por exemplo, consulte [documentação do Prism na assinatura de evento livremente acoplado](https://github.com/PrismLibrary/Prism-Documentation/blob/master/docs/wpf/Communication.md#subscribing-to-events)).</span><span class="sxs-lookup"><span data-stu-id="616f9-148">NuGet has [several weak event managers](https://www.nuget.org/packages?q=weak+event+manager&prerel=false) and many WPF frameworks also support the pattern (for instance, see [Prism's documentation on loosely coupled event subscription](https://github.com/PrismLibrary/Prism-Documentation/blob/master/docs/wpf/Communication.md#subscribing-to-events)).</span></span>|

 <span data-ttu-id="616f9-149">As seções a seguir descrevem como implementar o padrão de evento fraco.</span><span class="sxs-lookup"><span data-stu-id="616f9-149">The following sections describe how to implement the weak event pattern.</span></span>  <span data-ttu-id="616f9-150">Para fins desta discussão, o evento que deve ser assinado tem as seguintes características.</span><span class="sxs-lookup"><span data-stu-id="616f9-150">For purposes of this discussion, the event to subscribe to has the following characteristics.</span></span>  
  
-   <span data-ttu-id="616f9-151">O nome do evento é `SomeEvent`.</span><span class="sxs-lookup"><span data-stu-id="616f9-151">The event name is `SomeEvent`.</span></span>  
  
-   <span data-ttu-id="616f9-152">O evento é gerado pela classe `EventSource`.</span><span class="sxs-lookup"><span data-stu-id="616f9-152">The event is raised by the `EventSource` class.</span></span>  
  
-   <span data-ttu-id="616f9-153">O manipulador de eventos tem o tipo: `SomeEventEventHandler` (ou `EventHandler<SomeEventEventArgs>`).</span><span class="sxs-lookup"><span data-stu-id="616f9-153">The event handler has type: `SomeEventEventHandler` (or `EventHandler<SomeEventEventArgs>`).</span></span>  
  
-   <span data-ttu-id="616f9-154">O evento passa um parâmetro do tipo `SomeEventEventArgs` aos manipuladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="616f9-154">The event passes a parameter of type `SomeEventEventArgs` to the event handlers.</span></span>  
  
### <a name="using-an-existing-weak-event-manager-class"></a><span data-ttu-id="616f9-155">Usar uma classe existente de gerenciador de evento fraco</span><span class="sxs-lookup"><span data-stu-id="616f9-155">Using an Existing Weak Event Manager Class</span></span>  
  
1.  <span data-ttu-id="616f9-156">Encontre um gerenciador de evento fraco existente.</span><span class="sxs-lookup"><span data-stu-id="616f9-156">Find an existing weak event manager.</span></span>  
  
     <span data-ttu-id="616f9-157">Para obter uma lista de gerenciadores de evento fraco incluídos com o WPF, consulte a hierarquia de herança na <xref:System.Windows.WeakEventManager> classe.</span><span class="sxs-lookup"><span data-stu-id="616f9-157">For a list of weak event managers that are included with WPF, see the inheritance hierarchy in the <xref:System.Windows.WeakEventManager> class.</span></span>  
  
2.  <span data-ttu-id="616f9-158">Use o novo gerenciador de evento fraco em vez da conexão de evento normal.</span><span class="sxs-lookup"><span data-stu-id="616f9-158">Use the new weak event manager instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="616f9-159">Por exemplo, se seu código usa o padrão a seguir para assinar um evento:</span><span class="sxs-lookup"><span data-stu-id="616f9-159">For example, if your code uses the following pattern to subscribe to an event:</span></span>  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="616f9-160">Altere-o para o seguinte padrão:</span><span class="sxs-lookup"><span data-stu-id="616f9-160">Change it to the following pattern:</span></span>  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     <span data-ttu-id="616f9-161">Da mesma forma, se seu código usa o padrão a seguir para cancelar a assinatura de um evento:</span><span class="sxs-lookup"><span data-stu-id="616f9-161">Similarly, if your code uses the following pattern to unsubscribe from an event:</span></span>  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     <span data-ttu-id="616f9-162">Altere-o para o seguinte padrão:</span><span class="sxs-lookup"><span data-stu-id="616f9-162">Change it to the following pattern:</span></span>  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
### <a name="using-the-generic-weak-event-manager-class"></a><span data-ttu-id="616f9-163">Usando uma classe de gerenciador de evento fraco genérico</span><span class="sxs-lookup"><span data-stu-id="616f9-163">Using the Generic Weak Event Manager Class</span></span>  
  
1.  <span data-ttu-id="616f9-164">Usar o genérico <xref:System.Windows.WeakEventManager%602> classe em vez da conexão de evento normal.</span><span class="sxs-lookup"><span data-stu-id="616f9-164">Use the generic <xref:System.Windows.WeakEventManager%602> class instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="616f9-165">Quando você usa <xref:System.Windows.WeakEventManager%602> para registrar ouvintes de eventos, você fornece a origem do evento e <xref:System.EventArgs> tipo de como os parâmetros de tipo para a classe e a chamada <xref:System.Windows.WeakEventManager%602.AddHandler%2A> conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="616f9-165">When you use <xref:System.Windows.WeakEventManager%602> to register event listeners, you supply the event source and <xref:System.EventArgs> type as the type parameters to the class and call <xref:System.Windows.WeakEventManager%602.AddHandler%2A> as shown in the following code:</span></span>  
  
    ```  
    WeakEventManager<EventSource, SomeEventEventArgs>.AddHandler(source, "SomeEvent", source_SomeEvent);  
    ```  
  
### <a name="creating-a-custom-weak-event-manager-class"></a><span data-ttu-id="616f9-166">Criando uma classe de gerenciador de evento fraco personalizado</span><span class="sxs-lookup"><span data-stu-id="616f9-166">Creating a Custom Weak Event Manager Class</span></span>  
  
1.  <span data-ttu-id="616f9-167">Copie o seguinte modelo de classe no seu projeto.</span><span class="sxs-lookup"><span data-stu-id="616f9-167">Copy the following class template to your project.</span></span>  
  
     <span data-ttu-id="616f9-168">Essa classe herda a <xref:System.Windows.WeakEventManager> classe.</span><span class="sxs-lookup"><span data-stu-id="616f9-168">This class inherits from the <xref:System.Windows.WeakEventManager> class.</span></span>  
  
     [!code-csharp[WeakEvents#WeakEventManagerTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/WeakEvents/CSharp/WeakEventManagerTemplate.cs#weakeventmanagertemplate)]  
  
2.  <span data-ttu-id="616f9-169">Substitua o nome `SomeEventWeakEventManager` pelo seu próprio nome.</span><span class="sxs-lookup"><span data-stu-id="616f9-169">Replace the `SomeEventWeakEventManager` name with your own name.</span></span>  
  
3.  <span data-ttu-id="616f9-170">Substitua os três nomes descritos anteriormente pelos nomes correspondentes para seu evento.</span><span class="sxs-lookup"><span data-stu-id="616f9-170">Replace the three names described previously with the corresponding names for your event.</span></span> <span data-ttu-id="616f9-171">(`SomeEvent`, `EventSource` e `SomeEventEventArgs`)</span><span class="sxs-lookup"><span data-stu-id="616f9-171">(`SomeEvent`, `EventSource`, and `SomeEventEventArgs`)</span></span>  
  
4.  <span data-ttu-id="616f9-172">Defina a visibilidade (pública/interna/privada) da classe de gerenciador de evento fraco para a mesma visibilidade que o evento que ele gerencia.</span><span class="sxs-lookup"><span data-stu-id="616f9-172">Set the visibility (public / internal / private) of the weak event manager class to the same visibility as event it manages.</span></span>  
  
5.  <span data-ttu-id="616f9-173">Use o novo gerenciador de evento fraco em vez da conexão de evento normal.</span><span class="sxs-lookup"><span data-stu-id="616f9-173">Use the new weak event manager instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="616f9-174">Por exemplo, se seu código usa o padrão a seguir para assinar um evento:</span><span class="sxs-lookup"><span data-stu-id="616f9-174">For example, if your code uses the following pattern to subscribe to an event:</span></span>  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="616f9-175">Altere-o para o seguinte padrão:</span><span class="sxs-lookup"><span data-stu-id="616f9-175">Change it to the following pattern:</span></span>  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     <span data-ttu-id="616f9-176">De modo semelhante, se seu código usa o padrão a seguir para assinar um evento:</span><span class="sxs-lookup"><span data-stu-id="616f9-176">Similarly, if your code uses the following pattern to unsubscribe to an event:</span></span>  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     <span data-ttu-id="616f9-177">Altere-o para o seguinte padrão:</span><span class="sxs-lookup"><span data-stu-id="616f9-177">Change it to the following pattern:</span></span>  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="616f9-178">Consulte também</span><span class="sxs-lookup"><span data-stu-id="616f9-178">See also</span></span>

- <xref:System.Windows.WeakEventManager>
- <xref:System.Windows.IWeakEventListener>
- [<span data-ttu-id="616f9-179">Visão geral de eventos roteados</span><span class="sxs-lookup"><span data-stu-id="616f9-179">Routed Events Overview</span></span>](routed-events-overview.md)
- [<span data-ttu-id="616f9-180">Visão geral da vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="616f9-180">Data Binding Overview</span></span>](../data/data-binding-overview.md)
