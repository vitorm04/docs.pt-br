---
title: Como declarar, instanciar e usar um guia de programação do delegado C#
description: Saiba como declarar, criar uma instância e usar um delegado. Veja exemplos que abordam o C# 1,0, 2,0 e 3,0 e posterior.
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], declaring and instantiating
ms.assetid: 61c4895f-f785-48f8-8bfe-db73b411c4ae
ms.openlocfilehash: b741b3bc9c03faaa5fa2c01bd8f70d4be9b099c2
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063660"
---
# <a name="how-to-declare-instantiate-and-use-a-delegate-c-programming-guide"></a><span data-ttu-id="5bede-104">Como declarar, instanciar e usar um delegado (guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="5bede-104">How to declare, instantiate, and use a Delegate (C# Programming Guide)</span></span>
<span data-ttu-id="5bede-105">No C# 1.0 e versões posteriores, é possível declarar delegados conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="5bede-105">In C# 1.0 and later, delegates can be declared as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#13)]  
  
 [!code-csharp[csProgGuideDelegates#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#14)]  
  
 <span data-ttu-id="5bede-106">O C# 2.0 oferece uma maneira mais simples de gravar a declaração anterior, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="5bede-106">C# 2.0 provides a simpler way to write the previous declaration, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#32)]  
  
 <span data-ttu-id="5bede-107">No C# 2.0 e versões posteriores, também é possível usar um método anônimo para declarar e inicializar um [delegado](../../language-reference/builtin-types/reference-types.md), conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="5bede-107">In C# 2.0 and later, it is also possible to use an anonymous method to declare and initialize a [delegate](../../language-reference/builtin-types/reference-types.md), as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#15)]  
  
 <span data-ttu-id="5bede-108">No C# 3.0 e versões posteriores, os delegados também podem ser declarados e instanciados usando uma expressão lambda, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="5bede-108">In C# 3.0 and later, delegates can also be declared and instantiated by using a lambda expression, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#31)]  
  
 <span data-ttu-id="5bede-109">Para obter mais informações, consulte [Expressões Lambda](../../language-reference/operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="5bede-109">For more information, see [Lambda Expressions](../../language-reference/operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="5bede-110">O exemplo a seguir ilustra a declaração, instanciação e o uso de um delegado.</span><span class="sxs-lookup"><span data-stu-id="5bede-110">The following example illustrates declaring, instantiating, and using a delegate.</span></span> <span data-ttu-id="5bede-111">A classe `BookDB` encapsula um banco de dados de uma livraria que mantém um banco de dados de livros.</span><span class="sxs-lookup"><span data-stu-id="5bede-111">The `BookDB` class encapsulates a bookstore database that maintains a database of books.</span></span> <span data-ttu-id="5bede-112">Ela expõe um método, `ProcessPaperbackBooks`, que localiza todos os livros de bolso no banco de dados e chama um delegado para cada um.</span><span class="sxs-lookup"><span data-stu-id="5bede-112">It exposes a method, `ProcessPaperbackBooks`, which finds all paperback books in the database and calls a delegate for each one.</span></span> <span data-ttu-id="5bede-113">O tipo `delegate` usado tem o nome `ProcessBookDelegate`.</span><span class="sxs-lookup"><span data-stu-id="5bede-113">The `delegate` type that is used is named `ProcessBookDelegate`.</span></span> <span data-ttu-id="5bede-114">A classe `Test` usa essa classe para imprimir os títulos e o preço médio dos livros de bolso.</span><span class="sxs-lookup"><span data-stu-id="5bede-114">The `Test` class uses this class to print the titles and average price of the paperback books.</span></span>  
  
 <span data-ttu-id="5bede-115">O uso de delegados promove uma boa separação de funcionalidade entre o banco de dados da livraria e o código de cliente.</span><span class="sxs-lookup"><span data-stu-id="5bede-115">The use of delegates promotes good separation of functionality between the bookstore database and the client code.</span></span> <span data-ttu-id="5bede-116">O código de cliente não tem conhecimento de como os livros são armazenados ou como o código da livraria localiza os livros de bolso.</span><span class="sxs-lookup"><span data-stu-id="5bede-116">The client code has no knowledge of how the books are stored or how the bookstore code finds paperback books.</span></span> <span data-ttu-id="5bede-117">O código da livraria não tem conhecimento do processamento executado nos livros de bolso após a localização.</span><span class="sxs-lookup"><span data-stu-id="5bede-117">The bookstore code has no knowledge of what processing is performed on the paperback books after it finds them.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5bede-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5bede-118">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#12)]  
  
## <a name="robust-programming"></a><span data-ttu-id="5bede-119">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="5bede-119">Robust Programming</span></span>  
  
- <span data-ttu-id="5bede-120">Declarando um delegado.</span><span class="sxs-lookup"><span data-stu-id="5bede-120">Declaring a delegate.</span></span>  
  
     <span data-ttu-id="5bede-121">A instrução a seguir declara um novo tipo de delegado.</span><span class="sxs-lookup"><span data-stu-id="5bede-121">The following statement declares a new delegate type.</span></span>  
  
     [!code-csharp[csProgGuideDelegates#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#16)]  
  
     <span data-ttu-id="5bede-122">Cada tipo de delegado descreve o número e os tipos dos argumentos e o tipo do valor retornado dos métodos que pode encapsular.</span><span class="sxs-lookup"><span data-stu-id="5bede-122">Each delegate type describes the number and types of the arguments, and the type of the return value of methods that it can encapsulate.</span></span> <span data-ttu-id="5bede-123">Sempre que um novo conjunto de tipos de argumento ou tipo de valor retornado for necessário, um novo tipo de delegado deverá ser declarado.</span><span class="sxs-lookup"><span data-stu-id="5bede-123">Whenever a new set of argument types or return value type is needed, a new delegate type must be declared.</span></span>  
  
- <span data-ttu-id="5bede-124">Instanciando um delegado.</span><span class="sxs-lookup"><span data-stu-id="5bede-124">Instantiating a delegate.</span></span>  
  
     <span data-ttu-id="5bede-125">Após a declaração do tipo de delegado, um objeto delegado deve ser criado e associado a um método específico.</span><span class="sxs-lookup"><span data-stu-id="5bede-125">After a delegate type has been declared, a delegate object must be created and associated with a particular method.</span></span> <span data-ttu-id="5bede-126">No exemplo anterior, faça isso passando o método `PrintTitle` para o método `ProcessPaperbackBooks`, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="5bede-126">In the previous example, you do this by passing the `PrintTitle` method to the `ProcessPaperbackBooks` method as in the following example:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#17)]  
  
     <span data-ttu-id="5bede-127">Isso cria um novo objeto delegado associado ao método [estático](../../language-reference/keywords/static.md)`Test.PrintTitle`.</span><span class="sxs-lookup"><span data-stu-id="5bede-127">This creates a new delegate object associated with the [static](../../language-reference/keywords/static.md) method `Test.PrintTitle`.</span></span> <span data-ttu-id="5bede-128">Da mesma forma, o método não estático `AddBookToTotal` no objeto `totaller` é passado como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="5bede-128">Similarly, the non-static method `AddBookToTotal` on the object `totaller` is passed as in the following example:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#18)]  
  
     <span data-ttu-id="5bede-129">Em ambos os casos, um novo objeto delegado é passado para o método `ProcessPaperbackBooks`.</span><span class="sxs-lookup"><span data-stu-id="5bede-129">In both cases a new delegate object is passed to the `ProcessPaperbackBooks` method.</span></span>  
  
     <span data-ttu-id="5bede-130">Após a criação de um delegado, o método ao qual ele está associado nunca se altera; objetos delegados são imutáveis.</span><span class="sxs-lookup"><span data-stu-id="5bede-130">After a delegate is created, the method it is associated with never changes; delegate objects are immutable.</span></span>  
  
- <span data-ttu-id="5bede-131">Chamando um delegado.</span><span class="sxs-lookup"><span data-stu-id="5bede-131">Calling a delegate.</span></span>  
  
     <span data-ttu-id="5bede-132">Normalmente, o objeto delegado, após sua criação, é passado para outro código que chamará o delegado.</span><span class="sxs-lookup"><span data-stu-id="5bede-132">After a delegate object is created, the delegate object is typically passed to other code that will call the delegate.</span></span> <span data-ttu-id="5bede-133">Um objeto delegado é chamado usando seu nome seguido dos argumentos entre parênteses a serem passados para o delegado.</span><span class="sxs-lookup"><span data-stu-id="5bede-133">A delegate object is called by using the name of the delegate object, followed by the parenthesized arguments to be passed to the delegate.</span></span> <span data-ttu-id="5bede-134">A seguir, veja um exemplo de uma chamada de delegado:</span><span class="sxs-lookup"><span data-stu-id="5bede-134">Following is an example of a delegate call:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#19)]  
  
     <span data-ttu-id="5bede-135">Um delegado pode ser chamado de forma síncrona, como neste exemplo ou de forma assíncrona, usando os métodos `BeginInvoke` e `EndInvoke`.</span><span class="sxs-lookup"><span data-stu-id="5bede-135">A delegate can be either called synchronously, as in this example, or asynchronously by using `BeginInvoke` and `EndInvoke` methods.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bede-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5bede-136">See also</span></span>

- [<span data-ttu-id="5bede-137">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="5bede-137">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="5bede-138">Eventos</span><span class="sxs-lookup"><span data-stu-id="5bede-138">Events</span></span>](../events/index.md)
- [<span data-ttu-id="5bede-139">Representantes</span><span class="sxs-lookup"><span data-stu-id="5bede-139">Delegates</span></span>](./index.md)
