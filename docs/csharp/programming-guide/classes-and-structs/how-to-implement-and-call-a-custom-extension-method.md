---
title: Como implementar e chamar um método de extensão personalizado – C# guia de programação
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- extension methods [C#], implementing and calling
ms.assetid: 7dab2a56-cf8e-4a47-a444-fe610a02772a
ms.openlocfilehash: f3d96c033380698ade37c49ecbfeed14f05d3e11
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73970889"
---
# <a name="how-to-implement-and-call-a-custom-extension-method-c-programming-guide"></a><span data-ttu-id="569ee-102">Como implementar e chamar um método de extensão personalizado (C# guia de programação)</span><span class="sxs-lookup"><span data-stu-id="569ee-102">How to implement and call a custom extension method (C# Programming Guide)</span></span>
<span data-ttu-id="569ee-103">Este tópico mostra como implementar seus próprios métodos de extensão para qualquer tipo do .NET.</span><span class="sxs-lookup"><span data-stu-id="569ee-103">This topic shows how to implement your own extension methods for any .NET type.</span></span> <span data-ttu-id="569ee-104">O código de cliente pode usar seus métodos de extensão, adicionando uma referência à DLL que os contém e adicionando uma diretiva [using](../../language-reference/keywords/using-directive.md) que especifica o namespace no qual os métodos de extensão são definidos.</span><span class="sxs-lookup"><span data-stu-id="569ee-104">Client code can use your extension methods by adding a reference to the DLL that contains them, and adding a [using](../../language-reference/keywords/using-directive.md) directive that specifies the namespace in which the extension methods are defined.</span></span>  
  
## <a name="to-define-and-call-the-extension-method"></a><span data-ttu-id="569ee-105">Para definir e chamar o método de extensão</span><span class="sxs-lookup"><span data-stu-id="569ee-105">To define and call the extension method</span></span>  
  
1. <span data-ttu-id="569ee-106">Defina uma [classe](./static-classes-and-static-class-members.md) estática para conter o método de extensão.</span><span class="sxs-lookup"><span data-stu-id="569ee-106">Define a static [class](./static-classes-and-static-class-members.md) to contain the extension method.</span></span>  
  
     <span data-ttu-id="569ee-107">A classe deve estar visível para o código de cliente.</span><span class="sxs-lookup"><span data-stu-id="569ee-107">The class must be visible to client code.</span></span> <span data-ttu-id="569ee-108">Para obter mais informações sobre regras de acessibilidade, consulte [Modificadores de acesso](./access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="569ee-108">For more information about accessibility rules, see [Access Modifiers](./access-modifiers.md).</span></span>  
  
2. <span data-ttu-id="569ee-109">Implemente o método de extensão como um método estático com, pelo menos, a mesma visibilidade da classe que a contém.</span><span class="sxs-lookup"><span data-stu-id="569ee-109">Implement the extension method as a static method with at least the same visibility as the containing class.</span></span>  
  
3. <span data-ttu-id="569ee-110">O primeiro parâmetro do método especifica o tipo no qual o método opera. Ele deve ser precedido pelo modificador [this](../../language-reference/keywords/this.md).</span><span class="sxs-lookup"><span data-stu-id="569ee-110">The first parameter of the method specifies the type that the method operates on; it must be preceded with the [this](../../language-reference/keywords/this.md) modifier.</span></span>  
  
4. <span data-ttu-id="569ee-111">No código de chamada, adicione uma diretiva `using` para especificar o [namespace](../../language-reference/keywords/namespace.md) que contém a classe do método de extensão.</span><span class="sxs-lookup"><span data-stu-id="569ee-111">In the calling code, add a `using` directive to specify the [namespace](../../language-reference/keywords/namespace.md) that contains the extension method class.</span></span>  
  
5. <span data-ttu-id="569ee-112">Chame os métodos como se fossem métodos de instância no tipo.</span><span class="sxs-lookup"><span data-stu-id="569ee-112">Call the methods as if they were instance methods on the type.</span></span>  
  
     <span data-ttu-id="569ee-113">Observe que o primeiro parâmetro não é especificado pelo código de chamada porque ele representa o tipo no qual o operador está sendo aplicado e o compilador já conhece o tipo do objeto.</span><span class="sxs-lookup"><span data-stu-id="569ee-113">Note that the first parameter is not specified by calling code because it represents the type on which the operator is being applied, and the compiler already knows the type of your object.</span></span> <span data-ttu-id="569ee-114">Você só precisa fornecer argumentos para os parâmetros de 2 até o `n`.</span><span class="sxs-lookup"><span data-stu-id="569ee-114">You only have to provide arguments for parameters 2 through `n`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="569ee-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="569ee-115">Example</span></span>  
 <span data-ttu-id="569ee-116">O exemplo a seguir implementa um método de extensão chamado `WordCount` na classe `CustomExtensions.StringExtension`.</span><span class="sxs-lookup"><span data-stu-id="569ee-116">The following example implements an extension method named `WordCount` in the `CustomExtensions.StringExtension` class.</span></span> <span data-ttu-id="569ee-117">O método funciona na classe <xref:System.String>, que é especificada como o primeiro parâmetro do método.</span><span class="sxs-lookup"><span data-stu-id="569ee-117">The method operates on the <xref:System.String> class, which is specified as the first method parameter.</span></span> <span data-ttu-id="569ee-118">O namespace `CustomExtensions` é importado para o namespace do aplicativo e o método é chamado dentro do método `Main`.</span><span class="sxs-lookup"><span data-stu-id="569ee-118">The `CustomExtensions` namespace is imported into the application namespace, and the method is called inside the `Main` method.</span></span>  
  
 [!code-csharp[csProgGuideExtensionMethods#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#1)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="569ee-119">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="569ee-119">.NET Framework Security</span></span>  
 <span data-ttu-id="569ee-120">Os métodos de extensão não apresentam nenhuma vulnerabilidade de segurança específica.</span><span class="sxs-lookup"><span data-stu-id="569ee-120">Extension methods present no specific security vulnerabilities.</span></span> <span data-ttu-id="569ee-121">Eles nunca podem ser usados para representar os métodos existentes em um tipo, porque todos os conflitos de nome são resolvidos em favor da instância ou do método estático, definidos pelo próprio tipo.</span><span class="sxs-lookup"><span data-stu-id="569ee-121">They can never be used to impersonate existing methods on a type, because all name collisions are resolved in favor of the instance or static method defined by the type itself.</span></span> <span data-ttu-id="569ee-122">Os métodos de extensão não podem acessar nenhum dado particular na classe estendida.</span><span class="sxs-lookup"><span data-stu-id="569ee-122">Extension methods cannot access any private data in the extended class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="569ee-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="569ee-123">See also</span></span>

- [<span data-ttu-id="569ee-124">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="569ee-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="569ee-125">Métodos de Extensão</span><span class="sxs-lookup"><span data-stu-id="569ee-125">Extension Methods</span></span>](./extension-methods.md)
- [<span data-ttu-id="569ee-126">LINQ (Consulta Integrada à Linguagem)</span><span class="sxs-lookup"><span data-stu-id="569ee-126">LINQ (Language-Integrated Query)</span></span>](../../linq/linq-in-csharp.md)
- [<span data-ttu-id="569ee-127">Classes static e membros de classes static</span><span class="sxs-lookup"><span data-stu-id="569ee-127">Static Classes and Static Class Members</span></span>](./static-classes-and-static-class-members.md)
- [<span data-ttu-id="569ee-128">protected</span><span class="sxs-lookup"><span data-stu-id="569ee-128">protected</span></span>](../../language-reference/keywords/protected.md)
- [<span data-ttu-id="569ee-129">internal</span><span class="sxs-lookup"><span data-stu-id="569ee-129">internal</span></span>](../../language-reference/keywords/internal.md)
- [<span data-ttu-id="569ee-130">public</span><span class="sxs-lookup"><span data-stu-id="569ee-130">public</span></span>](../../language-reference/keywords/public.md)
- [<span data-ttu-id="569ee-131">this</span><span class="sxs-lookup"><span data-stu-id="569ee-131">this</span></span>](../../language-reference/keywords/this.md)
- [<span data-ttu-id="569ee-132">namespace</span><span class="sxs-lookup"><span data-stu-id="569ee-132">namespace</span></span>](../../language-reference/keywords/namespace.md)
