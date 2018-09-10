---
title: Métodos anônimos (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous methods [C#]
- methods [C#], anonymous
- delegates [C#], anonymous methods
ms.assetid: a62441fa-f0a3-4acb-9aa6-93762a635275
ms.openlocfilehash: 26d4b7f46783b9aa41035775928a4fe322d0af44
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43506651"
---
# <a name="anonymous-methods-c-programming-guide"></a><span data-ttu-id="c7f45-102">Métodos anônimos (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="c7f45-102">Anonymous Methods (C# Programming Guide)</span></span>
<span data-ttu-id="c7f45-103">Nas versões anteriores ao C# 2.0, a única maneira de declarar um [delegado](../../../csharp/language-reference/keywords/delegate.md) era usar [métodos nomeados](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md).</span><span class="sxs-lookup"><span data-stu-id="c7f45-103">In versions of C# before 2.0, the only way to declare a [delegate](../../../csharp/language-reference/keywords/delegate.md) was to use [named methods](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md).</span></span> <span data-ttu-id="c7f45-104">O C# 2.0 apresentou os métodos anônimos e no C# 3.0 e versões posteriores, as expressões lambda substituem os métodos anônimos como a melhor maneira de gravar código embutido.</span><span class="sxs-lookup"><span data-stu-id="c7f45-104">C# 2.0 introduced anonymous methods and in C# 3.0 and later, lambda expressions supersede anonymous methods as the preferred way to write inline code.</span></span> <span data-ttu-id="c7f45-105">No entanto, as informações sobre os métodos anônimos apresentadas neste tópico também se aplicam às expressões lambda.</span><span class="sxs-lookup"><span data-stu-id="c7f45-105">However, the information about anonymous methods in this topic also applies to lambda expressions.</span></span> <span data-ttu-id="c7f45-106">Há um caso em que um método anônimo fornece uma funcionalidade não encontrada em expressões lambda.</span><span class="sxs-lookup"><span data-stu-id="c7f45-106">There is one case in which an anonymous method provides functionality not found in lambda expressions.</span></span> <span data-ttu-id="c7f45-107">Métodos anônimos habilitam a omissão da lista de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="c7f45-107">Anonymous methods enable you to omit the parameter list.</span></span> <span data-ttu-id="c7f45-108">Isso significa que um método anônimo pode ser convertido em delegados com uma variedade de assinaturas.</span><span class="sxs-lookup"><span data-stu-id="c7f45-108">This means that an anonymous method can be converted to delegates with a variety of signatures.</span></span> <span data-ttu-id="c7f45-109">Isso não é possível com expressões lambda.</span><span class="sxs-lookup"><span data-stu-id="c7f45-109">This is not possible with lambda expressions.</span></span> <span data-ttu-id="c7f45-110">Para obter mais informações específicas sobre as expressões lambda, consulte [Expressões Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="c7f45-110">For more information specifically about lambda expressions, see [Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="c7f45-111">Essencialmente, criar métodos anônimos é uma forma de passar um bloco de código como um parâmetro delegado.</span><span class="sxs-lookup"><span data-stu-id="c7f45-111">Creating anonymous methods is essentially a way to pass a code block as a delegate parameter.</span></span> <span data-ttu-id="c7f45-112">Veja dois exemplos:</span><span class="sxs-lookup"><span data-stu-id="c7f45-112">Here are two examples:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#6](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_1.cs)]  
  
 [!code-csharp[csProgGuideDelegates#5](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_2.cs)]  
  
 <span data-ttu-id="c7f45-113">Ao usar métodos anônimos, a sobrecarga de codificação será reduzida nos delegados instanciados, pois não é necessário criar um método separado.</span><span class="sxs-lookup"><span data-stu-id="c7f45-113">By using anonymous methods, you reduce the coding overhead in instantiating delegates because you do not have to create a separate method.</span></span>  
  
 <span data-ttu-id="c7f45-114">Por exemplo, especificar um bloco de código em vez de um delegado pode ser útil em uma situação em que a criação de um método parece ser uma sobrecarga desnecessária.</span><span class="sxs-lookup"><span data-stu-id="c7f45-114">For example, specifying a code block instead of a delegate can be useful in a situation when having to create a method might seem an unnecessary overhead.</span></span> <span data-ttu-id="c7f45-115">Um bom exemplo é quando um novo thread é iniciado.</span><span class="sxs-lookup"><span data-stu-id="c7f45-115">A good example would be when you start a new thread.</span></span> <span data-ttu-id="c7f45-116">Essa classe cria um thread e também contém o código executado pelo thread sem criar um método adicional para o delegado.</span><span class="sxs-lookup"><span data-stu-id="c7f45-116">This class creates a thread and also contains the code that the thread executes without creating an additional method for the delegate.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#7](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_3.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="c7f45-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="c7f45-117">Remarks</span></span>  
 <span data-ttu-id="c7f45-118">O escopo dos parâmetros de um método anônimo é o *bloco de método anônimo*.</span><span class="sxs-lookup"><span data-stu-id="c7f45-118">The scope of the parameters of an anonymous method is the *anonymous-method-block*.</span></span>  
  
 <span data-ttu-id="c7f45-119">É um erro ter uma instrução de hiperlink, como [goto](../../../csharp/language-reference/keywords/goto.md), [break](../../../csharp/language-reference/keywords/break.md) ou [continue](../../../csharp/language-reference/keywords/continue.md), dentro do bloco de método anônimo se o destino estiver fora do bloco.</span><span class="sxs-lookup"><span data-stu-id="c7f45-119">It is an error to have a jump statement, such as [goto](../../../csharp/language-reference/keywords/goto.md), [break](../../../csharp/language-reference/keywords/break.md), or [continue](../../../csharp/language-reference/keywords/continue.md), inside the anonymous method block if the target is outside the block.</span></span> <span data-ttu-id="c7f45-120">Também é um erro ter uma instrução de hiperlink, como `goto`, `break` ou `continue`, fora do bloco de método anônimo se o destino estiver dentro do bloco.</span><span class="sxs-lookup"><span data-stu-id="c7f45-120">It is also an error to have a jump statement, such as `goto`, `break`, or `continue`, outside the anonymous method block if the target is inside the block.</span></span>  
  
 <span data-ttu-id="c7f45-121">As variáveis locais e parâmetros cujo escopo contém uma declaração de método anônimo são chamados variáveis *externas* do método anônimo.</span><span class="sxs-lookup"><span data-stu-id="c7f45-121">The local variables and parameters whose scope contains an anonymous method declaration are called *outer* variables of the anonymous method.</span></span> <span data-ttu-id="c7f45-122">Por exemplo, no segmento de código a seguir, `n` é uma variável externa:</span><span class="sxs-lookup"><span data-stu-id="c7f45-122">For example, in the following code segment, `n` is an outer variable:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#8](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_4.cs)]  
  
 <span data-ttu-id="c7f45-123">Uma referência à variável externa `n` é considerada *capturada* quando o delegado é criado.</span><span class="sxs-lookup"><span data-stu-id="c7f45-123">A reference to the outer variable `n` is said to be *captured* when the delegate is created.</span></span> <span data-ttu-id="c7f45-124">Ao contrário de variáveis locais, o tempo de vida de uma variável capturada se estende até os delegados que referenciam os métodos anônimos se tornarem elegíveis para a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="c7f45-124">Unlike local variables, the lifetime of a captured variable extends until the delegates that reference the anonymous methods are eligible for garbage collection.</span></span>  
  
 <span data-ttu-id="c7f45-125">Um método anônimo não pode acessar os parâmetros [in](../../../csharp/language-reference/keywords/in.md), [ref](../../../csharp/language-reference/keywords/ref.md) e [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) de um escopo externo.</span><span class="sxs-lookup"><span data-stu-id="c7f45-125">An anonymous method cannot access the [in](../../../csharp/language-reference/keywords/in.md), [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parameters of an outer scope.</span></span>  
  
 <span data-ttu-id="c7f45-126">Nenhum código não seguro pode ser acessado dentro do *bloco de método anônimo*.</span><span class="sxs-lookup"><span data-stu-id="c7f45-126">No unsafe code can be accessed within the *anonymous-method-block*.</span></span>  
  
 <span data-ttu-id="c7f45-127">Os métodos anônimos não são permitidos no lado esquerdo do operador [is](../../../csharp/language-reference/keywords/is.md).</span><span class="sxs-lookup"><span data-stu-id="c7f45-127">Anonymous methods are not allowed on the left side of the [is](../../../csharp/language-reference/keywords/is.md) operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7f45-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c7f45-128">Example</span></span>  
 <span data-ttu-id="c7f45-129">O exemplo a seguir demonstra duas maneiras de criar uma instância para um delegado:</span><span class="sxs-lookup"><span data-stu-id="c7f45-129">The following example demonstrates two ways of instantiating a delegate:</span></span>  
  
-   <span data-ttu-id="c7f45-130">Associando o delegado a um método anônimo.</span><span class="sxs-lookup"><span data-stu-id="c7f45-130">Associating the delegate with an anonymous method.</span></span>  
  
-   <span data-ttu-id="c7f45-131">Associando o delegado a um método nomeado (`DoWork`).</span><span class="sxs-lookup"><span data-stu-id="c7f45-131">Associating the delegate with a named method (`DoWork`).</span></span>  
  
 <span data-ttu-id="c7f45-132">Em cada caso, uma mensagem será exibida quando o delegado for invocado.</span><span class="sxs-lookup"><span data-stu-id="c7f45-132">In each case, a message is displayed when the delegate is invoked.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#4](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_5.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="c7f45-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c7f45-133">See Also</span></span>

- [<span data-ttu-id="c7f45-134">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="c7f45-134">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="c7f45-135">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="c7f45-135">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="c7f45-136">Delegados</span><span class="sxs-lookup"><span data-stu-id="c7f45-136">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
- [<span data-ttu-id="c7f45-137">Expressões Lambda</span><span class="sxs-lookup"><span data-stu-id="c7f45-137">Lambda Expressions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
- [<span data-ttu-id="c7f45-138">Código não seguro e ponteiros</span><span class="sxs-lookup"><span data-stu-id="c7f45-138">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
- [<span data-ttu-id="c7f45-139">Métodos</span><span class="sxs-lookup"><span data-stu-id="c7f45-139">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)  
- [<span data-ttu-id="c7f45-140">Delegados com métodos nomeados vs. métodos anônimos</span><span class="sxs-lookup"><span data-stu-id="c7f45-140">Delegates with Named vs. Anonymous Methods</span></span>](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)
