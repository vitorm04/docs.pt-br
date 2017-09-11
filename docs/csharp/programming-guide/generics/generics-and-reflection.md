---
title: "Genéricos e reflexão (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- generics [C#], reflection
- reflection [C#], generic types
ms.assetid: 162fd9b4-dd5b-4abb-8c9b-e44e21e2f451
caps.latest.revision: 15
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
ms.openlocfilehash: 201806cca08be0633d41e10ecb7641a0f03c975b
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="generics-and-reflection-c-programming-guide"></a><span data-ttu-id="09e17-102">Genéricos e reflexão (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="09e17-102">Generics and Reflection (C# Programming Guide)</span></span>
<span data-ttu-id="09e17-103">Como o tempo de execução do CLR (Common Language Runtime) tem acesso às informações de tipo genérico em tempo de execução, você pode usar a reflexão para obter informações sobre tipos genéricos da mesma forma como para tipos não genéricos.</span><span class="sxs-lookup"><span data-stu-id="09e17-103">Because the Common Language Runtime (CLR) has access to generic type information at run time, you can use reflection to obtain information about generic types in the same way as for non-generic types.</span></span> <span data-ttu-id="09e17-104">Para obter mais informações, consulte [Genéricos em tempo de execução](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).</span><span class="sxs-lookup"><span data-stu-id="09e17-104">For more information, see [Generics in the Run Time](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).</span></span>  
  
 <span data-ttu-id="09e17-105">No [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)] foram adicionados diversos novos membros à classe <xref:System.Type> para habilitar as informações em tempo de execução para tipos genéricos.</span><span class="sxs-lookup"><span data-stu-id="09e17-105">In the [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)] several new members are added to the <xref:System.Type> class to enable run-time information for generic types.</span></span> <span data-ttu-id="09e17-106">Consulte a documentação dessas classes para obter mais informações sobre como usar esses métodos e propriedades.</span><span class="sxs-lookup"><span data-stu-id="09e17-106">See the documentation on these classes for more information on how to use these methods and properties.</span></span> <span data-ttu-id="09e17-107">O namespace <xref:System.Reflection.Emit> também contém novos membros que dão suporte a genéricos.</span><span class="sxs-lookup"><span data-stu-id="09e17-107">The <xref:System.Reflection.Emit> namespace also contains new members that support generics.</span></span> <span data-ttu-id="09e17-108">Consulte [Como definir um tipo genérico com a emissão de reflexão](../../../framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md).</span><span class="sxs-lookup"><span data-stu-id="09e17-108">See [How to: Define a Generic Type with Reflection Emit](../../../framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md).</span></span>  
  
 <span data-ttu-id="09e17-109">Para obter uma lista das condições invariáveis para termos usados na reflexão genérica, consulte os comentários da propriedade <xref:System.Type.IsGenericType%2A>.</span><span class="sxs-lookup"><span data-stu-id="09e17-109">For a list of the invariant conditions for terms used in generic reflection, see the <xref:System.Type.IsGenericType%2A> property remarks.</span></span>  
  
|<span data-ttu-id="09e17-110">Nome do membro System.Type</span><span class="sxs-lookup"><span data-stu-id="09e17-110">System.Type Member Name</span></span>|<span data-ttu-id="09e17-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="09e17-111">Description</span></span>|  
|-----------------------------|-----------------|  
|<xref:System.Type.IsGenericType%2A>|<span data-ttu-id="09e17-112">Retorna verdadeiro se um tipo for genérico.</span><span class="sxs-lookup"><span data-stu-id="09e17-112">Returns true if a type is generic.</span></span>|  
|<xref:System.Type.GetGenericArguments%2A>|<span data-ttu-id="09e17-113">Retorna uma matriz de objetos `Type` que representa os argumentos de tipo fornecidos para um tipo construído ou os parâmetros de tipo de uma definição de tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="09e17-113">Returns an array of `Type` objects that represent the type arguments supplied for a constructed type, or the type parameters of a generic type definition.</span></span>|  
|<xref:System.Type.GetGenericTypeDefinition%2A>|<span data-ttu-id="09e17-114">Retorna a definição de tipo genérico subjacente para o tipo construído atual.</span><span class="sxs-lookup"><span data-stu-id="09e17-114">Returns the underlying generic type definition for the current constructed type.</span></span>|  
|<xref:System.Type.GetGenericParameterConstraints%2A>|<span data-ttu-id="09e17-115">Retorna uma matriz de objetos `Type` que representam as restrições no parâmetro de tipo genérico atual.</span><span class="sxs-lookup"><span data-stu-id="09e17-115">Returns an array of `Type` objects that represent the constraints on the current generic type parameter.</span></span>|  
|<xref:System.Type.ContainsGenericParameters%2A>|<span data-ttu-id="09e17-116">Retorna verdadeiro se o tipo ou qualquer um dos seus tipos ou métodos de delimitação contêm parâmetros de tipo para os quais não foram fornecidos tipos específicos.</span><span class="sxs-lookup"><span data-stu-id="09e17-116">Returns true if the type or any of its enclosing types or methods contain type parameters for which specific types have not been supplied.</span></span>|  
|<xref:System.Type.GenericParameterAttributes%2A>|<span data-ttu-id="09e17-117">Obtém uma combinação de sinalizadores `GenericParameterAttributes` que descrevem as restrições especiais do parâmetro de tipo genérico atual.</span><span class="sxs-lookup"><span data-stu-id="09e17-117">Gets a combination of `GenericParameterAttributes` flags that describe the special constraints of the current generic type parameter.</span></span>|  
|<xref:System.Type.GenericParameterPosition%2A>|<span data-ttu-id="09e17-118">Para um objeto `Type` que representa um parâmetro de tipo, obtém a posição do parâmetro de tipo na lista de parâmetros de tipo da definição de tipo genérico ou da definição de método genérico que declarou o parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="09e17-118">For a `Type` object that represents a type parameter, gets the position of the type parameter in the type parameter list of the generic type definition or generic method definition that declared the type parameter.</span></span>|  
|<xref:System.Type.IsGenericParameter%2A>|<span data-ttu-id="09e17-119">Obtém um valor que indica se o `Type` atual representa um parâmetro de tipo de um tipo genérico ou uma definição de método.</span><span class="sxs-lookup"><span data-stu-id="09e17-119">Gets a value that indicates whether the current `Type` represents a type parameter of a generic type or method definition.</span></span>|  
|<xref:System.Type.IsGenericTypeDefinition%2A>|<span data-ttu-id="09e17-120">Obtém um valor que indica se o <xref:System.Type> atual representa uma definição de tipo genérico, da qual outros tipos genéricos podem ser construídos.</span><span class="sxs-lookup"><span data-stu-id="09e17-120">Gets a value that indicates whether the current <xref:System.Type> represents a generic type definition, from which other generic types can be constructed.</span></span> <span data-ttu-id="09e17-121">Retorna verdadeiro se o tipo representa a definição de um tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="09e17-121">Returns true if the type represents the definition of a generic type.</span></span>|  
|<xref:System.Type.DeclaringMethod%2A>|<span data-ttu-id="09e17-122">Retorna o método genérico que definiu o parâmetro de tipo genérico atual ou nulo, se o parâmetro de tipo não foi definido por um método genérico.</span><span class="sxs-lookup"><span data-stu-id="09e17-122">Returns the generic method that defined the current generic type parameter, or null if the type parameter was not defined by a generic method.</span></span>|  
|<xref:System.Type.MakeGenericType%2A>|<span data-ttu-id="09e17-123">Substitui os elementos de uma matriz de tipos pelos parâmetros de tipo da definição de tipo genérico atual e retorna um objeto <xref:System.Type> que representa o tipo construído resultante.</span><span class="sxs-lookup"><span data-stu-id="09e17-123">Substitutes the elements of an array of types for the type parameters of the current generic type definition, and returns a <xref:System.Type> object representing the resulting constructed type.</span></span>|  
  
 <span data-ttu-id="09e17-124">Além disso, foram adicionados novos membros à classe <xref:System.Reflection.MethodInfo> para habilitar as informações em tempo de execução para métodos genéricos.</span><span class="sxs-lookup"><span data-stu-id="09e17-124">In addition, new members are added to the <xref:System.Reflection.MethodInfo> class to enable run-time information for generic methods.</span></span> <span data-ttu-id="09e17-125">Consulte os comentários sobre a propriedade <xref:System.Reflection.MethodInfo.IsGenericMethod%2A> para obter uma lista das condições invariáveis para termos usados para refletir sobre os métodos genéricos.</span><span class="sxs-lookup"><span data-stu-id="09e17-125">See the <xref:System.Reflection.MethodInfo.IsGenericMethod%2A> property remarks for a list of invariant conditions for terms used to reflect on generic methods.</span></span>  
  
|<span data-ttu-id="09e17-126">Nome do membro System.Reflection.MemberInfo</span><span class="sxs-lookup"><span data-stu-id="09e17-126">System.Reflection.MemberInfo Member Name</span></span>|<span data-ttu-id="09e17-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="09e17-127">Description</span></span>|  
|----------------------------------------------|-----------------|  
|<xref:System.Reflection.MethodInfo.IsGenericMethod%2A>|<span data-ttu-id="09e17-128">Retorna verdadeiro se um método for genérico.</span><span class="sxs-lookup"><span data-stu-id="09e17-128">Returns true if a method is generic.</span></span>|  
|<xref:System.Reflection.MethodInfo.GetGenericArguments%2A>|<span data-ttu-id="09e17-129">Retorna uma matriz de objetos Type que representam os argumentos de tipo de um método genérico construído ou os parâmetros de tipo de uma definição de método genérico.</span><span class="sxs-lookup"><span data-stu-id="09e17-129">Returns an array of Type objects that represent the type arguments of a constructed generic method or the type parameters of a generic method definition.</span></span>|  
|<xref:System.Reflection.MethodInfo.GetGenericMethodDefinition%2A>|<span data-ttu-id="09e17-130">Retorna a definição de método genérico subjacente para o método construído atual.</span><span class="sxs-lookup"><span data-stu-id="09e17-130">Returns the underlying generic method definition for the current constructed method.</span></span>|  
|<xref:System.Reflection.MethodInfo.ContainsGenericParameters%2A>|<span data-ttu-id="09e17-131">Retorna verdadeiro se o método ou qualquer um dos seus tipos de delimitação contêm parâmetros de tipo para os quais não foram fornecidos tipos específicos.</span><span class="sxs-lookup"><span data-stu-id="09e17-131">Returns true if the method or any of its enclosing types contain any type parameters for which specific types have not been supplied.</span></span>|  
|<xref:System.Reflection.MethodInfo.IsGenericMethodDefinition%2A>|<span data-ttu-id="09e17-132">Retorna verdadeiro se o <xref:System.Reflection.MethodInfo> atual representar a definição de um método genérico.</span><span class="sxs-lookup"><span data-stu-id="09e17-132">Returns true if the current <xref:System.Reflection.MethodInfo> represents the definition of a generic method.</span></span>|  
|<xref:System.Reflection.MethodInfo.MakeGenericMethod%2A>|<span data-ttu-id="09e17-133">Substitui os elementos de uma matriz de tipos pelos parâmetros de tipo da definição de método genérico atual e retorna um objeto <xref:System.Reflection.MethodInfo> que representa o método construído resultante.</span><span class="sxs-lookup"><span data-stu-id="09e17-133">Substitutes the elements of an array of types for the type parameters of the current generic method definition, and returns a <xref:System.Reflection.MethodInfo> object representing the resulting constructed method.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="09e17-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="09e17-134">See Also</span></span>  
 <span data-ttu-id="09e17-135">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="09e17-135">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="09e17-136">[Genéricos](../../../csharp/programming-guide/generics/index.md) </span><span class="sxs-lookup"><span data-stu-id="09e17-136">[Generics](../../../csharp/programming-guide/generics/index.md) </span></span>  
 <span data-ttu-id="09e17-137">[Reflexão e tipos genéricos](../../../framework/reflection-and-codedom/reflection-and-generic-types.md) </span><span class="sxs-lookup"><span data-stu-id="09e17-137">[Reflection and Generic Types](../../../framework/reflection-and-codedom/reflection-and-generic-types.md) </span></span>  
 [<span data-ttu-id="09e17-138">Genéricos</span><span class="sxs-lookup"><span data-stu-id="09e17-138">Generics</span></span>](~/docs/standard/generics/index.md)

