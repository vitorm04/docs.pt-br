---
title: "Delegados (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- C# language, delegates
- delegates [C#]
ms.assetid: 97de039b-c76b-4b9c-a27d-8c1e1c8d93da
caps.latest.revision: 30
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
ms.openlocfilehash: 1d3dc2252b086f9df9e64a059a53ec8792e11b45
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="delegates-c-programming-guide"></a><span data-ttu-id="11398-102">Delegados (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="11398-102">Delegates (C# Programming Guide)</span></span>
<span data-ttu-id="11398-103">Um [delegado](../../../csharp/language-reference/keywords/delegate.md) é um tipo que representa referências aos métodos com lista de parâmetros e tipo de retorno específicos.</span><span class="sxs-lookup"><span data-stu-id="11398-103">A [delegate](../../../csharp/language-reference/keywords/delegate.md) is a type that represents references to methods with a particular parameter list and return type.</span></span> <span data-ttu-id="11398-104">Ao instanciar um delegado, você pode associar sua instância a qualquer método com assinatura e tipo de retorno compatíveis.</span><span class="sxs-lookup"><span data-stu-id="11398-104">When you instantiate a delegate, you can associate its instance with any method with a compatible signature and return type.</span></span> <span data-ttu-id="11398-105">Você pode invocar (ou chamar) o método através da instância de delegado.</span><span class="sxs-lookup"><span data-stu-id="11398-105">You can invoke (or call) the method through the delegate instance.</span></span>  
  
 <span data-ttu-id="11398-106">Delegados são usados para passar métodos como argumentos a outros métodos.</span><span class="sxs-lookup"><span data-stu-id="11398-106">Delegates are used to pass methods as arguments to other methods.</span></span> <span data-ttu-id="11398-107">Os manipuladores de eventos nada mais são do que métodos chamados por meio de delegados.</span><span class="sxs-lookup"><span data-stu-id="11398-107">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="11398-108">Ao criar um método personalizado, uma classe como um controle do Windows poderá chamá-lo quando um determinado evento ocorrer.</span><span class="sxs-lookup"><span data-stu-id="11398-108">You create a custom method, and a class such as a windows control can call your method when a certain event occurs.</span></span> <span data-ttu-id="11398-109">O seguinte exemplo mostra uma declaração de delegado:</span><span class="sxs-lookup"><span data-stu-id="11398-109">The following example shows a delegate declaration:</span></span>  
  
 <span data-ttu-id="11398-110">[!code-cs[csProgGuideDelegates n º 20](../../../csharp/programming-guide/delegates/codesnippet/CSharp/index_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="11398-110">[!code-cs[csProgGuideDelegates#20](../../../csharp/programming-guide/delegates/codesnippet/CSharp/index_1.cs)]</span></span>  
  
 <span data-ttu-id="11398-111">Qualquer método de qualquer classe ou struct acessível que corresponda ao tipo delegado pode ser atribuído ao delegado.</span><span class="sxs-lookup"><span data-stu-id="11398-111">Any method from any accessible class or struct that matches the delegate type can be assigned to the delegate.</span></span> <span data-ttu-id="11398-112">O método pode ser estático ou de instância.</span><span class="sxs-lookup"><span data-stu-id="11398-112">The method can be either static or an instance method.</span></span> <span data-ttu-id="11398-113">Isso possibilita alterar via programação chamadas de método e também conectar novo código a classes existentes.</span><span class="sxs-lookup"><span data-stu-id="11398-113">This makes it possible to programmatically change method calls, and also plug new code into existing classes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="11398-114">No contexto da sobrecarga de método, a assinatura de um método não inclui o valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="11398-114">In the context of method overloading, the signature of a method does not include the return value.</span></span> <span data-ttu-id="11398-115">No entanto, no contexto de delegados, a assinatura inclui o valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="11398-115">But in the context of delegates, the signature does include the return value.</span></span> <span data-ttu-id="11398-116">Em outras palavras, um método deve ter o mesmo tipo de retorno que o delegado.</span><span class="sxs-lookup"><span data-stu-id="11398-116">In other words, a method must have the same return type as the delegate.</span></span>  
  
 <span data-ttu-id="11398-117">Essa capacidade de se referir a um método como um parâmetro torna delegados ideais para definir métodos de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="11398-117">This ability to refer to a method as a parameter makes delegates ideal for defining callback methods.</span></span> <span data-ttu-id="11398-118">Por exemplo, uma referência a um método que compara dois objetos poderia ser passada como um argumento para um algoritmo de classificação.</span><span class="sxs-lookup"><span data-stu-id="11398-118">For example, a reference to a method that compares two objects could be passed as an argument to a sort algorithm.</span></span> <span data-ttu-id="11398-119">Como o código de comparação está em um procedimento separado, o algoritmo de classificação pode ser escrito de forma mais geral.</span><span class="sxs-lookup"><span data-stu-id="11398-119">Because the comparison code is in a separate procedure, the sort algorithm can be written in a more general way.</span></span>  
  
## <a name="delegates-overview"></a><span data-ttu-id="11398-120">Visão geral de delegados</span><span class="sxs-lookup"><span data-stu-id="11398-120">Delegates Overview</span></span>  
 <span data-ttu-id="11398-121">Os delegados possuem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="11398-121">Delegates have the following properties:</span></span>  
  
-   <span data-ttu-id="11398-122">Os delegados são como ponteiros de funções em C++, mas apresentam tipos seguros.</span><span class="sxs-lookup"><span data-stu-id="11398-122">Delegates are like C++ function pointers but are type safe.</span></span>  
  
-   <span data-ttu-id="11398-123">Os delegados permitem que métodos sejam passados como parâmetros.</span><span class="sxs-lookup"><span data-stu-id="11398-123">Delegates allow methods to be passed as parameters.</span></span>  
  
-   <span data-ttu-id="11398-124">Os delegados podem ser usados para definir métodos de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="11398-124">Delegates can be used to define callback methods.</span></span>  
  
-   <span data-ttu-id="11398-125">Os delegados podem ser encadeados juntos; por exemplo, vários métodos podem ser chamados um único evento.</span><span class="sxs-lookup"><span data-stu-id="11398-125">Delegates can be chained together; for example, multiple methods can be called on a single event.</span></span>  
  
-   <span data-ttu-id="11398-126">Os métodos não precisam corresponder ao tipo delegado exatamente.</span><span class="sxs-lookup"><span data-stu-id="11398-126">Methods do not have to match the delegate type exactly.</span></span> <span data-ttu-id="11398-127">Para obter mais informações, consulte [Usando a variação delegados](../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="11398-127">For more information, see [Using Variance in Delegates](../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span></span>  
  
-   <span data-ttu-id="11398-128">O C# versão 2.0 introduziu o conceito de [Métodos Anônimos](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) que permitem que blocos de código sejam passados como parâmetros em vez de um método definido separadamente.</span><span class="sxs-lookup"><span data-stu-id="11398-128">C# version 2.0 introduced the concept of [Anonymous Methods](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md), which allow code blocks to be passed as parameters in place of a separately defined method.</span></span> <span data-ttu-id="11398-129">O C# 3.0 introduziu expressões lambda como uma maneira mais concisa de escrever blocos de código embutidos.</span><span class="sxs-lookup"><span data-stu-id="11398-129">C# 3.0 introduced lambda expressions as a more concise way of writing inline code blocks.</span></span> <span data-ttu-id="11398-130">Os métodos anônimos e as expressões lambda (em determinados contextos) são compilados para tipos delegados.</span><span class="sxs-lookup"><span data-stu-id="11398-130">Both anonymous methods and lambda expressions (in certain contexts) are compiled to delegate types.</span></span> <span data-ttu-id="11398-131">Juntos, esses recursos são agora conhecidos como funções anônimas.</span><span class="sxs-lookup"><span data-stu-id="11398-131">Together, these features are now known as anonymous functions.</span></span> <span data-ttu-id="11398-132">Para obter mais informações sobre expressões lambda, consulte [Funções Anônimas](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span><span class="sxs-lookup"><span data-stu-id="11398-132">For more information about lambda expressions, see [Anonymous Functions](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="11398-133">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="11398-133">In This Section</span></span>  
  
-   [<span data-ttu-id="11398-134">Usando delegados</span><span class="sxs-lookup"><span data-stu-id="11398-134">Using Delegates</span></span>](../../../csharp/programming-guide/delegates/using-delegates.md)  
  
-   [<span data-ttu-id="11398-135">Quando usar delegados em vez de interfaces (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="11398-135">When to Use Delegates Instead of Interfaces (C# Programming Guide)</span></span>](http://msdn.microsoft.com/en-us/2e759bdf-7ca4-4005-8597-af92edf6d8f0)  
  
-   [<span data-ttu-id="11398-136">Delegados com métodos nomeados vs. métodos anônimos</span><span class="sxs-lookup"><span data-stu-id="11398-136">Delegates with Named vs. Anonymous Methods</span></span>](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)  
  
-   [<span data-ttu-id="11398-137">Métodos anônimos</span><span class="sxs-lookup"><span data-stu-id="11398-137">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
  
-   [<span data-ttu-id="11398-138">Usando Variação em Delegações</span><span class="sxs-lookup"><span data-stu-id="11398-138">Using Variance in Delegates</span></span>](../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)  
  
-   [<span data-ttu-id="11398-139">Como combinar delegados (delegados multicast)</span><span class="sxs-lookup"><span data-stu-id="11398-139">How to: Combine Delegates (Multicast Delegates)</span></span>](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)  
  
-   [<span data-ttu-id="11398-140">Como declarar e usar um delegado e criar uma instância dele</span><span class="sxs-lookup"><span data-stu-id="11398-140">How to: Declare, Instantiate, and Use a Delegate</span></span>](../../../csharp/programming-guide/delegates/how-to-declare-instantiate-and-use-a-delegate.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="11398-141">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="11398-141">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="featured-book-chapters"></a><span data-ttu-id="11398-142">Capítulos do Livro em Destaque</span><span class="sxs-lookup"><span data-stu-id="11398-142">Featured Book Chapters</span></span>  
 <span data-ttu-id="11398-143">[Expressões lambda, eventos e delegados](http://go.microsoft.com/fwlink/?LinkId=195395) em [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](http://go.microsoft.com/fwlink/?LinkId=195369)</span><span class="sxs-lookup"><span data-stu-id="11398-143">[Delegates, Events, and Lambda Expressions](http://go.microsoft.com/fwlink/?LinkId=195395) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](http://go.microsoft.com/fwlink/?LinkId=195369)</span></span>  
  
 <span data-ttu-id="11398-144">[Delegados e eventos](http://go.microsoft.com/fwlink/?LinkId=195418) em [Learning C# 3.0: Master the fundamentals of C# 3.0](http://go.microsoft.com/fwlink/?LinkId=195412)</span><span class="sxs-lookup"><span data-stu-id="11398-144">[Delegates and Events](http://go.microsoft.com/fwlink/?LinkId=195418) in [Learning C# 3.0: Master the fundamentals of C# 3.0](http://go.microsoft.com/fwlink/?LinkId=195412)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11398-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="11398-145">See Also</span></span>  
 <span data-ttu-id="11398-146"><xref:System.Delegate></span><span class="sxs-lookup"><span data-stu-id="11398-146"><xref:System.Delegate></span></span>   
 <span data-ttu-id="11398-147">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="11398-147">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="11398-148">Eventos</span><span class="sxs-lookup"><span data-stu-id="11398-148">Events</span></span>](../../../csharp/programming-guide/events/index.md)

