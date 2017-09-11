---
title: "Métodos anônimos (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- anonymous methods [C#]
- methods [C#], anonymous
- delegates [C#], anonymous methods
ms.assetid: a62441fa-f0a3-4acb-9aa6-93762a635275
caps.latest.revision: 31
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
ms.openlocfilehash: 92842becf26a15ab1a6f5e9621002abf71dc67bc
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="anonymous-methods-c-programming-guide"></a><span data-ttu-id="0ed7f-102">Métodos anônimos (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="0ed7f-102">Anonymous Methods (C# Programming Guide)</span></span>
<span data-ttu-id="0ed7f-103">Nas versões anteriores ao C# 2.0, a única maneira de declarar um [delegado](../../../csharp/language-reference/keywords/delegate.md) era usar [métodos nomeados](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md).</span><span class="sxs-lookup"><span data-stu-id="0ed7f-103">In versions of C# before 2.0, the only way to declare a [delegate](../../../csharp/language-reference/keywords/delegate.md) was to use [named methods](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md).</span></span> <span data-ttu-id="0ed7f-104">O C# 2.0 apresentou os métodos anônimos e no C# 3.0 e versões posteriores, as expressões lambda substituem os métodos anônimos como a melhor maneira de gravar código embutido.</span><span class="sxs-lookup"><span data-stu-id="0ed7f-104">C# 2.0 introduced anonymous methods and in C# 3.0 and later, lambda expressions supersede anonymous methods as the preferred way to write inline code.</span></span> <span data-ttu-id="0ed7f-105">No entanto, as informações sobre os métodos anônimos apresentadas neste tópico também se aplicam às expressões lambda.</span><span class="sxs-lookup"><span data-stu-id="0ed7f-105">However, the information about anonymous methods in this topic also applies to lambda expressions.</span></span> <span data-ttu-id="0ed7f-106">Há um caso em que um método anônimo fornece uma funcionalidade não encontrada em expressões lambda.</span><span class="sxs-lookup"><span data-stu-id="0ed7f-106">There is one case in which an anonymous method provides functionality not found in lambda expressions.</span></span> <span data-ttu-id="0ed7f-107">Métodos anônimos habilitam a omissão da lista de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="0ed7f-107">Anonymous methods enable you to omit the parameter list.</span></span> <span data-ttu-id="0ed7f-108">Isso significa que um método anônimo pode ser convertido em delegados com uma variedade de assinaturas.</span><span class="sxs-lookup"><span data-stu-id="0ed7f-108">This means that an anonymous method can be converted to delegates with a variety of signatures.</span></span> <span data-ttu-id="0ed7f-109">Isso não é possível com expressões lambda.</span><span class="sxs-lookup"><span data-stu-id="0ed7f-109">This is not possible with lambda expressions.</span></span> <span data-ttu-id="0ed7f-110">Para obter mais informações específicas sobre as expressões lambda, consulte [Expressões Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="0ed7f-110">For more information specifically about lambda expressions, see [Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="0ed7f-111">Essencialmente, criar métodos anônimos é uma forma de passar um bloco de código como um parâmetro delegado.</span><span class="sxs-lookup"><span data-stu-id="0ed7f-111">Creating anonymous methods is essentially a way to pass a code block as a delegate parameter.</span></span> <span data-ttu-id="0ed7f-112">Veja dois exemplos:</span><span class="sxs-lookup"><span data-stu-id="0ed7f-112">Here are two examples:</span></span>  
  
 <span data-ttu-id="0ed7f-113">[!code-cs[csProgGuideDelegates#6](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="0ed7f-113">[!code-cs[csProgGuideDelegates#6](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_1.cs)]</span></span>  
  
 <span data-ttu-id="0ed7f-114">[!code-cs[csProgGuideDelegates#5](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="0ed7f-114">[!code-cs[csProgGuideDelegates#5](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_2.cs)]</span></span>  
  
 <span data-ttu-id="0ed7f-115">Ao usar métodos anônimos, a sobrecarga de codificação será reduzida nos delegados instanciados, pois não é necessário criar um método separado.</span><span class="sxs-lookup"><span data-stu-id="0ed7f-115">By using anonymous methods, you reduce the coding overhead in instantiating delegates because you do not have to create a separate method.</span></span>  
  
 <span data-ttu-id="0ed7f-116">Por exemplo, especificar um bloco de código em vez de um delegado pode ser útil em uma situação em que a criação de um método parece ser uma sobrecarga desnecessária.</span><span class="sxs-lookup"><span data-stu-id="0ed7f-116">For example, specifying a code block instead of a delegate can be useful in a situation when having to create a method might seem an unnecessary overhead.</span></span> <span data-ttu-id="0ed7f-117">Um bom exemplo é quando um novo thread é iniciado.</span><span class="sxs-lookup"><span data-stu-id="0ed7f-117">A good example would be when you start a new thread.</span></span> <span data-ttu-id="0ed7f-118">Essa classe cria um thread e também contém o código executado pelo thread sem criar um método adicional para o delegado.</span><span class="sxs-lookup"><span data-stu-id="0ed7f-118">This class creates a thread and also contains the code that the thread executes without creating an additional method for the delegate.</span></span>  
  
 <span data-ttu-id="0ed7f-119">[!code-cs[csProgGuideDelegates#7](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="0ed7f-119">[!code-cs[csProgGuideDelegates#7](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_3.cs)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0ed7f-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="0ed7f-120">Remarks</span></span>  
 <span data-ttu-id="0ed7f-121">O escopo dos parâmetros de um método anônimo é o *bloco de método anônimo*.</span><span class="sxs-lookup"><span data-stu-id="0ed7f-121">The scope of the parameters of an anonymous method is the *anonymous-method-block*.</span></span>  
  
 <span data-ttu-id="0ed7f-122">É um erro ter uma instrução de hiperlink, como [goto](../../../csharp/language-reference/keywords/goto.md), [break](../../../csharp/language-reference/keywords/break.md) ou [continue](../../../csharp/language-reference/keywords/continue.md), dentro do bloco de método anônimo se o destino estiver fora do bloco.</span><span class="sxs-lookup"><span data-stu-id="0ed7f-122">It is an error to have a jump statement, such as [goto](../../../csharp/language-reference/keywords/goto.md), [break](../../../csharp/language-reference/keywords/break.md), or [continue](../../../csharp/language-reference/keywords/continue.md), inside the anonymous method block if the target is outside the block.</span></span> <span data-ttu-id="0ed7f-123">Também é um erro ter uma instrução de hiperlink, como `goto`, `break` ou `continue`, fora do bloco de método anônimo se o destino estiver dentro do bloco.</span><span class="sxs-lookup"><span data-stu-id="0ed7f-123">It is also an error to have a jump statement, such as `goto`, `break`, or `continue`, outside the anonymous method block if the target is inside the block.</span></span>  
  
 <span data-ttu-id="0ed7f-124">As variáveis locais e parâmetros cujo escopo contém uma declaração de método anônimo são chamados variáveis *externas* do método anônimo.</span><span class="sxs-lookup"><span data-stu-id="0ed7f-124">The local variables and parameters whose scope contains an anonymous method declaration are called *outer* variables of the anonymous method.</span></span> <span data-ttu-id="0ed7f-125">Por exemplo, no segmento de código a seguir, `n` é uma variável externa:</span><span class="sxs-lookup"><span data-stu-id="0ed7f-125">For example, in the following code segment, `n` is an outer variable:</span></span>  
  
 <span data-ttu-id="0ed7f-126">[!code-cs[csProgGuideDelegates#8](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="0ed7f-126">[!code-cs[csProgGuideDelegates#8](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_4.cs)]</span></span>  
  
 <span data-ttu-id="0ed7f-127">Uma referência à variável externa `n` é considerada *capturada* quando o delegado é criado.</span><span class="sxs-lookup"><span data-stu-id="0ed7f-127">A reference to the outer variable `n` is said to be *captured* when the delegate is created.</span></span> <span data-ttu-id="0ed7f-128">Ao contrário de variáveis locais, o tempo de vida de uma variável capturada se estende até os delegados que referenciam os métodos anônimos se tornarem elegíveis para a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="0ed7f-128">Unlike local variables, the lifetime of a captured variable extends until the delegates that reference the anonymous methods are eligible for garbage collection.</span></span>  
  
 <span data-ttu-id="0ed7f-129">Um método anônimo não pode acessar os parâmetros [ref](../../../csharp/language-reference/keywords/ref.md) ou [out](../../../csharp/language-reference/keywords/out.md) de um escopo externo.</span><span class="sxs-lookup"><span data-stu-id="0ed7f-129">An anonymous method cannot access the [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out.md) parameters of an outer scope.</span></span>  
  
 <span data-ttu-id="0ed7f-130">Nenhum código não seguro pode ser acessado dentro do *bloco de método anônimo*.</span><span class="sxs-lookup"><span data-stu-id="0ed7f-130">No unsafe code can be accessed within the *anonymous-method-block*.</span></span>  
  
 <span data-ttu-id="0ed7f-131">Os métodos anônimos não são permitidos no lado esquerdo do operador [is](../../../csharp/language-reference/keywords/is.md).</span><span class="sxs-lookup"><span data-stu-id="0ed7f-131">Anonymous methods are not allowed on the left side of the [is](../../../csharp/language-reference/keywords/is.md) operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ed7f-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ed7f-132">Example</span></span>  
 <span data-ttu-id="0ed7f-133">O exemplo a seguir demonstra duas maneiras de criar uma instância para um delegado:</span><span class="sxs-lookup"><span data-stu-id="0ed7f-133">The following example demonstrates two ways of instantiating a delegate:</span></span>  
  
-   <span data-ttu-id="0ed7f-134">Associando o delegado a um método anônimo.</span><span class="sxs-lookup"><span data-stu-id="0ed7f-134">Associating the delegate with an anonymous method.</span></span>  
  
-   <span data-ttu-id="0ed7f-135">Associando o delegado a um método nomeado (`DoWork`).</span><span class="sxs-lookup"><span data-stu-id="0ed7f-135">Associating the delegate with a named method (`DoWork`).</span></span>  
  
 <span data-ttu-id="0ed7f-136">Em cada caso, uma mensagem será exibida quando o delegado for invocado.</span><span class="sxs-lookup"><span data-stu-id="0ed7f-136">In each case, a message is displayed when the delegate is invoked.</span></span>  
  
 <span data-ttu-id="0ed7f-137">[!code-cs[csProgGuideDelegates#4](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="0ed7f-137">[!code-cs[csProgGuideDelegates#4](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_5.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ed7f-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ed7f-138">See Also</span></span>  
 <span data-ttu-id="0ed7f-139">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="0ed7f-139">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="0ed7f-140">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="0ed7f-140">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="0ed7f-141">[Delegados](../../../csharp/programming-guide/delegates/index.md) </span><span class="sxs-lookup"><span data-stu-id="0ed7f-141">[Delegates](../../../csharp/programming-guide/delegates/index.md) </span></span>  
 <span data-ttu-id="0ed7f-142">[Expressões Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="0ed7f-142">[Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) </span></span>  
 <span data-ttu-id="0ed7f-143">[Código Não Seguro e Ponteiros](../../../csharp/programming-guide/unsafe-code-pointers/index.md) </span><span class="sxs-lookup"><span data-stu-id="0ed7f-143">[Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md) </span></span>  
 <span data-ttu-id="0ed7f-144">[Métodos](../../../csharp/programming-guide/classes-and-structs/methods.md) </span><span class="sxs-lookup"><span data-stu-id="0ed7f-144">[Methods](../../../csharp/programming-guide/classes-and-structs/methods.md) </span></span>  
 [<span data-ttu-id="0ed7f-145">Delegados com métodos nomeados vs. métodos anônimos</span><span class="sxs-lookup"><span data-stu-id="0ed7f-145">Delegates with Named vs. Anonymous Methods</span></span>](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)

