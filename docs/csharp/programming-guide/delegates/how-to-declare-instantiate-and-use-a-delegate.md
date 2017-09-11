---
title: "Como declarar e usar um delegado e criar uma instância dele (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- delegates [C#], declaring and instantiating
ms.assetid: 61c4895f-f785-48f8-8bfe-db73b411c4ae
caps.latest.revision: 21
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
ms.openlocfilehash: 5a16fe4c627989f701ba523769cd87839d074849
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-declare-instantiate-and-use-a-delegate-c-programming-guide"></a><span data-ttu-id="dc100-102">Como declarar e usar um delegado e criar uma instância dele (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="dc100-102">How to: Declare, Instantiate, and Use a Delegate (C# Programming Guide)</span></span>
<span data-ttu-id="dc100-103">No C# 1.0 e versões posteriores, é possível declarar delegados conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="dc100-103">In C# 1.0 and later, delegates can be declared as shown in the following example.</span></span>  
  
 <span data-ttu-id="dc100-104">[!code-cs[csProgGuideDelegates#13](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="dc100-104">[!code-cs[csProgGuideDelegates#13](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_1.cs)]</span></span>  
  
 <span data-ttu-id="dc100-105">[!code-cs[csProgGuideDelegates#14](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="dc100-105">[!code-cs[csProgGuideDelegates#14](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_2.cs)]</span></span>  
  
 <span data-ttu-id="dc100-106">O C# 2.0 oferece uma maneira mais simples de gravar a declaração anterior, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="dc100-106">C# 2.0 provides a simpler way to write the previous declaration, as shown in the following example.</span></span>  
  
 <span data-ttu-id="dc100-107">[!code-cs[csProgGuideDelegates#32](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="dc100-107">[!code-cs[csProgGuideDelegates#32](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_3.cs)]</span></span>  
  
 <span data-ttu-id="dc100-108">No C# 2.0 e versões posteriores, também é possível usar um método anônimo para declarar e inicializar um [delegado](../../../csharp/language-reference/keywords/delegate.md), conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="dc100-108">In C# 2.0 and later, it is also possible to use an anonymous method to declare and initialize a [delegate](../../../csharp/language-reference/keywords/delegate.md), as shown in the following example.</span></span>  
  
 <span data-ttu-id="dc100-109">[!code-cs[csProgGuideDelegates#15](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="dc100-109">[!code-cs[csProgGuideDelegates#15](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_4.cs)]</span></span>  
  
 <span data-ttu-id="dc100-110">No C# 3.0 e versões posteriores, os delegados também podem ser declarados e instanciados usando uma expressão lambda, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="dc100-110">In C# 3.0 and later, delegates can also be declared and instantiated by using a lambda expression, as shown in the following example.</span></span>  
  
 <span data-ttu-id="dc100-111">[!code-cs[csProgGuideDelegates#31](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="dc100-111">[!code-cs[csProgGuideDelegates#31](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_5.cs)]</span></span>  
  
 <span data-ttu-id="dc100-112">Para obter mais informações, consulte [Expressões Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="dc100-112">For more information, see [Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="dc100-113">O exemplo a seguir ilustra a declaração, instanciação e o uso de um delegado.</span><span class="sxs-lookup"><span data-stu-id="dc100-113">The following example illustrates declaring, instantiating, and using a delegate.</span></span> <span data-ttu-id="dc100-114">A classe `BookDB` encapsula um banco de dados de uma livraria que mantém um banco de dados de livros.</span><span class="sxs-lookup"><span data-stu-id="dc100-114">The `BookDB` class encapsulates a bookstore database that maintains a database of books.</span></span> <span data-ttu-id="dc100-115">Ela expõe um método, `ProcessPaperbackBooks`, que localiza todos os livros de bolso no banco de dados e chama um delegado para cada um.</span><span class="sxs-lookup"><span data-stu-id="dc100-115">It exposes a method, `ProcessPaperbackBooks`, which finds all paperback books in the database and calls a delegate for each one.</span></span> <span data-ttu-id="dc100-116">O tipo `delegate` usado tem o nome `ProcessBookDelegate`.</span><span class="sxs-lookup"><span data-stu-id="dc100-116">The `delegate` type that is used is named `ProcessBookDelegate`.</span></span> <span data-ttu-id="dc100-117">A classe `Test` usa essa classe para imprimir os títulos e o preço médio dos livros de bolso.</span><span class="sxs-lookup"><span data-stu-id="dc100-117">The `Test` class uses this class to print the titles and average price of the paperback books.</span></span>  
  
 <span data-ttu-id="dc100-118">O uso de delegados promove uma boa separação de funcionalidade entre o banco de dados da livraria e o código de cliente.</span><span class="sxs-lookup"><span data-stu-id="dc100-118">The use of delegates promotes good separation of functionality between the bookstore database and the client code.</span></span> <span data-ttu-id="dc100-119">O código de cliente não tem conhecimento de como os livros são armazenados ou como o código da livraria localiza os livros de bolso.</span><span class="sxs-lookup"><span data-stu-id="dc100-119">The client code has no knowledge of how the books are stored or how the bookstore code finds paperback books.</span></span> <span data-ttu-id="dc100-120">O código da livraria não tem conhecimento do processamento executado nos livros de bolso após a localização.</span><span class="sxs-lookup"><span data-stu-id="dc100-120">The bookstore code has no knowledge of what processing is performed on the paperback books after it finds them.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc100-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dc100-121">Example</span></span>  
 <span data-ttu-id="dc100-122">[!code-cs[csProgGuideDelegates#12](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="dc100-122">[!code-cs[csProgGuideDelegates#12](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_6.cs)]</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="dc100-123">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="dc100-123">Robust Programming</span></span>  
  
-   <span data-ttu-id="dc100-124">Declarando um delegado.</span><span class="sxs-lookup"><span data-stu-id="dc100-124">Declaring a delegate.</span></span>  
  
     <span data-ttu-id="dc100-125">A instrução a seguir declara um novo tipo de delegado.</span><span class="sxs-lookup"><span data-stu-id="dc100-125">The following statement declares a new delegate type.</span></span>  
  
     <span data-ttu-id="dc100-126">[!code-cs[csProgGuideDelegates#16](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="dc100-126">[!code-cs[csProgGuideDelegates#16](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_7.cs)]</span></span>  
  
     <span data-ttu-id="dc100-127">Cada tipo de delegado descreve o número e os tipos dos argumentos e o tipo do valor retornado dos métodos que pode encapsular.</span><span class="sxs-lookup"><span data-stu-id="dc100-127">Each delegate type describes the number and types of the arguments, and the type of the return value of methods that it can encapsulate.</span></span> <span data-ttu-id="dc100-128">Sempre que um novo conjunto de tipos de argumento ou tipo de valor retornado for necessário, um novo tipo de delegado deverá ser declarado.</span><span class="sxs-lookup"><span data-stu-id="dc100-128">Whenever a new set of argument types or return value type is needed, a new delegate type must be declared.</span></span>  
  
-   <span data-ttu-id="dc100-129">Instanciando um delegado.</span><span class="sxs-lookup"><span data-stu-id="dc100-129">Instantiating a delegate.</span></span>  
  
     <span data-ttu-id="dc100-130">Após a declaração do tipo de delegado, um objeto delegado deve ser criado e associado a um método específico.</span><span class="sxs-lookup"><span data-stu-id="dc100-130">After a delegate type has been declared, a delegate object must be created and associated with a particular method.</span></span> <span data-ttu-id="dc100-131">No exemplo anterior, faça isso passando o método `PrintTitle` para o método `ProcessPaperbackBooks`, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="dc100-131">In the previous example, you do this by passing the `PrintTitle` method to the `ProcessPaperbackBooks` method as in the following example:</span></span>  
  
     <span data-ttu-id="dc100-132">[!code-cs[csProgGuideDelegates#17](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_8.cs)]</span><span class="sxs-lookup"><span data-stu-id="dc100-132">[!code-cs[csProgGuideDelegates#17](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_8.cs)]</span></span>  
  
     <span data-ttu-id="dc100-133">Isso cria um novo objeto delegado associado ao método [estático](../../../csharp/language-reference/keywords/static.md) `Test.PrintTitle`.</span><span class="sxs-lookup"><span data-stu-id="dc100-133">This creates a new delegate object associated with the [static](../../../csharp/language-reference/keywords/static.md) method `Test.PrintTitle`.</span></span> <span data-ttu-id="dc100-134">Da mesma forma, o método não estático `AddBookToTotal` no objeto `totaller` é passado como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="dc100-134">Similarly, the non-static method `AddBookToTotal` on the object `totaller` is passed as in the following example:</span></span>  
  
     <span data-ttu-id="dc100-135">[!code-cs[csProgGuideDelegates#18](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_9.cs)]</span><span class="sxs-lookup"><span data-stu-id="dc100-135">[!code-cs[csProgGuideDelegates#18](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_9.cs)]</span></span>  
  
     <span data-ttu-id="dc100-136">Em ambos os casos, um novo objeto delegado é passado para o método `ProcessPaperbackBooks`.</span><span class="sxs-lookup"><span data-stu-id="dc100-136">In both cases a new delegate object is passed to the `ProcessPaperbackBooks` method.</span></span>  
  
     <span data-ttu-id="dc100-137">Após a criação de um delegado, o método ao qual ele está associado nunca se altera; objetos delegados são imutáveis.</span><span class="sxs-lookup"><span data-stu-id="dc100-137">After a delegate is created, the method it is associated with never changes; delegate objects are immutable.</span></span>  
  
-   <span data-ttu-id="dc100-138">Chamando um delegado.</span><span class="sxs-lookup"><span data-stu-id="dc100-138">Calling a delegate.</span></span>  
  
     <span data-ttu-id="dc100-139">Normalmente, o objeto delegado, após sua criação, é passado para outro código que chamará o delegado.</span><span class="sxs-lookup"><span data-stu-id="dc100-139">After a delegate object is created, the delegate object is typically passed to other code that will call the delegate.</span></span> <span data-ttu-id="dc100-140">Um objeto delegado é chamado usando seu nome seguido dos argumentos entre parênteses a serem passados para o delegado.</span><span class="sxs-lookup"><span data-stu-id="dc100-140">A delegate object is called by using the name of the delegate object, followed by the parenthesized arguments to be passed to the delegate.</span></span> <span data-ttu-id="dc100-141">A seguir, veja um exemplo de uma chamada de delegado:</span><span class="sxs-lookup"><span data-stu-id="dc100-141">Following is an example of a delegate call:</span></span>  
  
     <span data-ttu-id="dc100-142">[!code-cs[csProgGuideDelegates#19](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_10.cs)]</span><span class="sxs-lookup"><span data-stu-id="dc100-142">[!code-cs[csProgGuideDelegates#19](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_10.cs)]</span></span>  
  
     <span data-ttu-id="dc100-143">Um delegado pode ser chamado de forma síncrona, como neste exemplo ou de forma assíncrona, usando os métodos `BeginInvoke` e `EndInvoke`.</span><span class="sxs-lookup"><span data-stu-id="dc100-143">A delegate can be either called synchronously, as in this example, or asynchronously by using `BeginInvoke` and `EndInvoke` methods.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc100-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dc100-144">See Also</span></span>  
 <span data-ttu-id="dc100-145">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="dc100-145">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="dc100-146">[Eventos](../../../csharp/programming-guide/events/index.md) </span><span class="sxs-lookup"><span data-stu-id="dc100-146">[Events](../../../csharp/programming-guide/events/index.md) </span></span>  
 [<span data-ttu-id="dc100-147">Delegados</span><span class="sxs-lookup"><span data-stu-id="dc100-147">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)

