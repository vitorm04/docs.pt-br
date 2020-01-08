---
title: Como declarar, instanciar e usar um guia de C# programação de delegação
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], declaring and instantiating
ms.assetid: 61c4895f-f785-48f8-8bfe-db73b411c4ae
ms.openlocfilehash: 02c3087d27e5018b77079a2dd6f260a0e7232d3a
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346379"
---
# <a name="how-to-declare-instantiate-and-use-a-delegate-c-programming-guide"></a><span data-ttu-id="24c23-102">Como declarar, instanciar e usar um delegado (C# guia de programação)</span><span class="sxs-lookup"><span data-stu-id="24c23-102">How to declare, instantiate, and use a Delegate (C# Programming Guide)</span></span>
<span data-ttu-id="24c23-103">No C# 1.0 e versões posteriores, é possível declarar delegados conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="24c23-103">In C# 1.0 and later, delegates can be declared as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#13)]  
  
 [!code-csharp[csProgGuideDelegates#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#14)]  
  
 <span data-ttu-id="24c23-104">O C# 2.0 oferece uma maneira mais simples de gravar a declaração anterior, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="24c23-104">C# 2.0 provides a simpler way to write the previous declaration, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#32)]  
  
 <span data-ttu-id="24c23-105">No C# 2.0 e versões posteriores, também é possível usar um método anônimo para declarar e inicializar um [delegado](../../language-reference/builtin-types/reference-types.md), conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="24c23-105">In C# 2.0 and later, it is also possible to use an anonymous method to declare and initialize a [delegate](../../language-reference/builtin-types/reference-types.md), as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#15)]  
  
 <span data-ttu-id="24c23-106">No C# 3.0 e versões posteriores, os delegados também podem ser declarados e instanciados usando uma expressão lambda, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="24c23-106">In C# 3.0 and later, delegates can also be declared and instantiated by using a lambda expression, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#31)]  
  
 <span data-ttu-id="24c23-107">Para obter mais informações, consulte [Expressões Lambda](../statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="24c23-107">For more information, see [Lambda Expressions](../statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="24c23-108">O exemplo a seguir ilustra a declaração, instanciação e o uso de um delegado.</span><span class="sxs-lookup"><span data-stu-id="24c23-108">The following example illustrates declaring, instantiating, and using a delegate.</span></span> <span data-ttu-id="24c23-109">A classe `BookDB` encapsula um banco de dados de uma livraria que mantém um banco de dados de livros.</span><span class="sxs-lookup"><span data-stu-id="24c23-109">The `BookDB` class encapsulates a bookstore database that maintains a database of books.</span></span> <span data-ttu-id="24c23-110">Ela expõe um método, `ProcessPaperbackBooks`, que localiza todos os livros de bolso no banco de dados e chama um delegado para cada um.</span><span class="sxs-lookup"><span data-stu-id="24c23-110">It exposes a method, `ProcessPaperbackBooks`, which finds all paperback books in the database and calls a delegate for each one.</span></span> <span data-ttu-id="24c23-111">O tipo `delegate` usado tem o nome `ProcessBookDelegate`.</span><span class="sxs-lookup"><span data-stu-id="24c23-111">The `delegate` type that is used is named `ProcessBookDelegate`.</span></span> <span data-ttu-id="24c23-112">A classe `Test` usa essa classe para imprimir os títulos e o preço médio dos livros de bolso.</span><span class="sxs-lookup"><span data-stu-id="24c23-112">The `Test` class uses this class to print the titles and average price of the paperback books.</span></span>  
  
 <span data-ttu-id="24c23-113">O uso de delegados promove uma boa separação de funcionalidade entre o banco de dados da livraria e o código de cliente.</span><span class="sxs-lookup"><span data-stu-id="24c23-113">The use of delegates promotes good separation of functionality between the bookstore database and the client code.</span></span> <span data-ttu-id="24c23-114">O código de cliente não tem conhecimento de como os livros são armazenados ou como o código da livraria localiza os livros de bolso.</span><span class="sxs-lookup"><span data-stu-id="24c23-114">The client code has no knowledge of how the books are stored or how the bookstore code finds paperback books.</span></span> <span data-ttu-id="24c23-115">O código da livraria não tem conhecimento do processamento executado nos livros de bolso após a localização.</span><span class="sxs-lookup"><span data-stu-id="24c23-115">The bookstore code has no knowledge of what processing is performed on the paperback books after it finds them.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24c23-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="24c23-116">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#12)]  
  
## <a name="robust-programming"></a><span data-ttu-id="24c23-117">Programação Robusta</span><span class="sxs-lookup"><span data-stu-id="24c23-117">Robust Programming</span></span>  
  
- <span data-ttu-id="24c23-118">Declarando um delegado.</span><span class="sxs-lookup"><span data-stu-id="24c23-118">Declaring a delegate.</span></span>  
  
     <span data-ttu-id="24c23-119">A instrução a seguir declara um novo tipo de delegado.</span><span class="sxs-lookup"><span data-stu-id="24c23-119">The following statement declares a new delegate type.</span></span>  
  
     [!code-csharp[csProgGuideDelegates#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#16)]  
  
     <span data-ttu-id="24c23-120">Cada tipo de delegado descreve o número e os tipos dos argumentos e o tipo do valor retornado dos métodos que pode encapsular.</span><span class="sxs-lookup"><span data-stu-id="24c23-120">Each delegate type describes the number and types of the arguments, and the type of the return value of methods that it can encapsulate.</span></span> <span data-ttu-id="24c23-121">Sempre que um novo conjunto de tipos de argumento ou tipo de valor retornado for necessário, um novo tipo de delegado deverá ser declarado.</span><span class="sxs-lookup"><span data-stu-id="24c23-121">Whenever a new set of argument types or return value type is needed, a new delegate type must be declared.</span></span>  
  
- <span data-ttu-id="24c23-122">Instanciando um delegado.</span><span class="sxs-lookup"><span data-stu-id="24c23-122">Instantiating a delegate.</span></span>  
  
     <span data-ttu-id="24c23-123">Após a declaração do tipo de delegado, um objeto delegado deve ser criado e associado a um método específico.</span><span class="sxs-lookup"><span data-stu-id="24c23-123">After a delegate type has been declared, a delegate object must be created and associated with a particular method.</span></span> <span data-ttu-id="24c23-124">No exemplo anterior, faça isso passando o método `PrintTitle` para o método `ProcessPaperbackBooks`, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="24c23-124">In the previous example, you do this by passing the `PrintTitle` method to the `ProcessPaperbackBooks` method as in the following example:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#17)]  
  
     <span data-ttu-id="24c23-125">Isso cria um novo objeto delegado associado ao método [estático](../../language-reference/keywords/static.md)`Test.PrintTitle`.</span><span class="sxs-lookup"><span data-stu-id="24c23-125">This creates a new delegate object associated with the [static](../../language-reference/keywords/static.md) method `Test.PrintTitle`.</span></span> <span data-ttu-id="24c23-126">Da mesma forma, o método não estático `AddBookToTotal` no objeto `totaller` é passado como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="24c23-126">Similarly, the non-static method `AddBookToTotal` on the object `totaller` is passed as in the following example:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#18)]  
  
     <span data-ttu-id="24c23-127">Em ambos os casos, um novo objeto delegado é passado para o método `ProcessPaperbackBooks`.</span><span class="sxs-lookup"><span data-stu-id="24c23-127">In both cases a new delegate object is passed to the `ProcessPaperbackBooks` method.</span></span>  
  
     <span data-ttu-id="24c23-128">Após a criação de um delegado, o método ao qual ele está associado nunca se altera; objetos delegados são imutáveis.</span><span class="sxs-lookup"><span data-stu-id="24c23-128">After a delegate is created, the method it is associated with never changes; delegate objects are immutable.</span></span>  
  
- <span data-ttu-id="24c23-129">Chamando um delegado.</span><span class="sxs-lookup"><span data-stu-id="24c23-129">Calling a delegate.</span></span>  
  
     <span data-ttu-id="24c23-130">Normalmente, o objeto delegado, após sua criação, é passado para outro código que chamará o delegado.</span><span class="sxs-lookup"><span data-stu-id="24c23-130">After a delegate object is created, the delegate object is typically passed to other code that will call the delegate.</span></span> <span data-ttu-id="24c23-131">Um objeto delegado é chamado usando seu nome seguido dos argumentos entre parênteses a serem passados para o delegado.</span><span class="sxs-lookup"><span data-stu-id="24c23-131">A delegate object is called by using the name of the delegate object, followed by the parenthesized arguments to be passed to the delegate.</span></span> <span data-ttu-id="24c23-132">A seguir, veja um exemplo de uma chamada de delegado:</span><span class="sxs-lookup"><span data-stu-id="24c23-132">Following is an example of a delegate call:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#19)]  
  
     <span data-ttu-id="24c23-133">Um delegado pode ser chamado de forma síncrona, como neste exemplo ou de forma assíncrona, usando os métodos `BeginInvoke` e `EndInvoke`.</span><span class="sxs-lookup"><span data-stu-id="24c23-133">A delegate can be either called synchronously, as in this example, or asynchronously by using `BeginInvoke` and `EndInvoke` methods.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24c23-134">Veja também</span><span class="sxs-lookup"><span data-stu-id="24c23-134">See also</span></span>

- [<span data-ttu-id="24c23-135">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="24c23-135">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="24c23-136">Eventos</span><span class="sxs-lookup"><span data-stu-id="24c23-136">Events</span></span>](../events/index.md)
- [<span data-ttu-id="24c23-137">Delegados</span><span class="sxs-lookup"><span data-stu-id="24c23-137">Delegates</span></span>](./index.md)
