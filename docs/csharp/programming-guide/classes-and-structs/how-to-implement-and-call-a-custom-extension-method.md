---
title: Como implementar e chamar um método de extensão personalizado – guia de programação C#
description: Saiba como implementar métodos de extensão para qualquer tipo .NET. O código do cliente pode usar seus métodos adicionando uma referência a uma DLL e adicionando uma diretiva using.
ms.date: 07/20/2015
helpviewer_keywords:
- extension methods [C#], implementing and calling
ms.assetid: 7dab2a56-cf8e-4a47-a444-fe610a02772a
ms.openlocfilehash: de4cc423e1823351305a23f331b082aa66add1a6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91190430"
---
# <a name="how-to-implement-and-call-a-custom-extension-method-c-programming-guide"></a><span data-ttu-id="9595b-104">Como implementar e chamar um método de extensão personalizado (guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="9595b-104">How to implement and call a custom extension method (C# Programming Guide)</span></span>

<span data-ttu-id="9595b-105">Este tópico mostra como implementar seus próprios métodos de extensão para qualquer tipo do .NET.</span><span class="sxs-lookup"><span data-stu-id="9595b-105">This topic shows how to implement your own extension methods for any .NET type.</span></span> <span data-ttu-id="9595b-106">O código de cliente pode usar seus métodos de extensão, adicionando uma referência à DLL que os contém e adicionando uma diretiva [using](../../language-reference/keywords/using-directive.md) que especifica o namespace no qual os métodos de extensão são definidos.</span><span class="sxs-lookup"><span data-stu-id="9595b-106">Client code can use your extension methods by adding a reference to the DLL that contains them, and adding a [using](../../language-reference/keywords/using-directive.md) directive that specifies the namespace in which the extension methods are defined.</span></span>  
  
## <a name="to-define-and-call-the-extension-method"></a><span data-ttu-id="9595b-107">Para definir e chamar o método de extensão</span><span class="sxs-lookup"><span data-stu-id="9595b-107">To define and call the extension method</span></span>  
  
1. <span data-ttu-id="9595b-108">Defina uma [classe](./static-classes-and-static-class-members.md) estática para conter o método de extensão.</span><span class="sxs-lookup"><span data-stu-id="9595b-108">Define a static [class](./static-classes-and-static-class-members.md) to contain the extension method.</span></span>  
  
     <span data-ttu-id="9595b-109">A classe deve estar visível para o código de cliente.</span><span class="sxs-lookup"><span data-stu-id="9595b-109">The class must be visible to client code.</span></span> <span data-ttu-id="9595b-110">Para obter mais informações sobre regras de acessibilidade, consulte [Modificadores de acesso](./access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="9595b-110">For more information about accessibility rules, see [Access Modifiers](./access-modifiers.md).</span></span>  
  
2. <span data-ttu-id="9595b-111">Implemente o método de extensão como um método estático com, pelo menos, a mesma visibilidade da classe que a contém.</span><span class="sxs-lookup"><span data-stu-id="9595b-111">Implement the extension method as a static method with at least the same visibility as the containing class.</span></span>  
  
3. <span data-ttu-id="9595b-112">O primeiro parâmetro do método especifica o tipo no qual o método opera. Ele deve ser precedido pelo modificador [this](../../language-reference/keywords/this.md).</span><span class="sxs-lookup"><span data-stu-id="9595b-112">The first parameter of the method specifies the type that the method operates on; it must be preceded with the [this](../../language-reference/keywords/this.md) modifier.</span></span>  
  
4. <span data-ttu-id="9595b-113">No código de chamada, adicione uma diretiva `using` para especificar o [namespace](../../language-reference/keywords/namespace.md) que contém a classe do método de extensão.</span><span class="sxs-lookup"><span data-stu-id="9595b-113">In the calling code, add a `using` directive to specify the [namespace](../../language-reference/keywords/namespace.md) that contains the extension method class.</span></span>  
  
5. <span data-ttu-id="9595b-114">Chame os métodos como se fossem métodos de instância no tipo.</span><span class="sxs-lookup"><span data-stu-id="9595b-114">Call the methods as if they were instance methods on the type.</span></span>  
  
     <span data-ttu-id="9595b-115">Observe que o primeiro parâmetro não é especificado pelo código de chamada porque ele representa o tipo no qual o operador está sendo aplicado e o compilador já conhece o tipo do objeto.</span><span class="sxs-lookup"><span data-stu-id="9595b-115">Note that the first parameter is not specified by calling code because it represents the type on which the operator is being applied, and the compiler already knows the type of your object.</span></span> <span data-ttu-id="9595b-116">Você só precisa fornecer argumentos para os parâmetros de 2 até o `n`.</span><span class="sxs-lookup"><span data-stu-id="9595b-116">You only have to provide arguments for parameters 2 through `n`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9595b-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9595b-117">Example</span></span>  

 <span data-ttu-id="9595b-118">O exemplo a seguir implementa um método de extensão chamado `WordCount` na classe `CustomExtensions.StringExtension`.</span><span class="sxs-lookup"><span data-stu-id="9595b-118">The following example implements an extension method named `WordCount` in the `CustomExtensions.StringExtension` class.</span></span> <span data-ttu-id="9595b-119">O método funciona na classe <xref:System.String>, que é especificada como o primeiro parâmetro do método.</span><span class="sxs-lookup"><span data-stu-id="9595b-119">The method operates on the <xref:System.String> class, which is specified as the first method parameter.</span></span> <span data-ttu-id="9595b-120">O namespace `CustomExtensions` é importado para o namespace do aplicativo e o método é chamado dentro do método `Main`.</span><span class="sxs-lookup"><span data-stu-id="9595b-120">The `CustomExtensions` namespace is imported into the application namespace, and the method is called inside the `Main` method.</span></span>  
  
 [!code-csharp[csProgGuideExtensionMethods#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#1)]  
  
## <a name="net-security"></a><span data-ttu-id="9595b-121">Segurança do .NET</span><span class="sxs-lookup"><span data-stu-id="9595b-121">.NET Security</span></span>  

 <span data-ttu-id="9595b-122">Os métodos de extensão não apresentam nenhuma vulnerabilidade de segurança específica.</span><span class="sxs-lookup"><span data-stu-id="9595b-122">Extension methods present no specific security vulnerabilities.</span></span> <span data-ttu-id="9595b-123">Eles nunca podem ser usados para representar os métodos existentes em um tipo, porque todos os conflitos de nome são resolvidos em favor da instância ou do método estático, definidos pelo próprio tipo.</span><span class="sxs-lookup"><span data-stu-id="9595b-123">They can never be used to impersonate existing methods on a type, because all name collisions are resolved in favor of the instance or static method defined by the type itself.</span></span> <span data-ttu-id="9595b-124">Os métodos de extensão não podem acessar nenhum dado particular na classe estendida.</span><span class="sxs-lookup"><span data-stu-id="9595b-124">Extension methods cannot access any private data in the extended class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9595b-125">Veja também</span><span class="sxs-lookup"><span data-stu-id="9595b-125">See also</span></span>

- [<span data-ttu-id="9595b-126">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="9595b-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9595b-127">Métodos de Extensão</span><span class="sxs-lookup"><span data-stu-id="9595b-127">Extension Methods</span></span>](./extension-methods.md)
- [<span data-ttu-id="9595b-128">LINQ (Consulta Integrada à Linguagem)</span><span class="sxs-lookup"><span data-stu-id="9595b-128">LINQ (Language-Integrated Query)</span></span>](../../linq/linq-in-csharp.md)
- [<span data-ttu-id="9595b-129">Classes static e membros de classes static</span><span class="sxs-lookup"><span data-stu-id="9595b-129">Static Classes and Static Class Members</span></span>](./static-classes-and-static-class-members.md)
- [<span data-ttu-id="9595b-130">protegidos</span><span class="sxs-lookup"><span data-stu-id="9595b-130">protected</span></span>](../../language-reference/keywords/protected.md)
- [<span data-ttu-id="9595b-131">interno</span><span class="sxs-lookup"><span data-stu-id="9595b-131">internal</span></span>](../../language-reference/keywords/internal.md)
- [<span data-ttu-id="9595b-132">public</span><span class="sxs-lookup"><span data-stu-id="9595b-132">public</span></span>](../../language-reference/keywords/public.md)
- [<span data-ttu-id="9595b-133">this</span><span class="sxs-lookup"><span data-stu-id="9595b-133">this</span></span>](../../language-reference/keywords/this.md)
- [<span data-ttu-id="9595b-134">namespace</span><span class="sxs-lookup"><span data-stu-id="9595b-134">namespace</span></span>](../../language-reference/keywords/namespace.md)
