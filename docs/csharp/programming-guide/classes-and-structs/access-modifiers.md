---
title: "Modificadores de acesso (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- C# Language, access modifiers
- access modifiers [C#], about
ms.assetid: 6e81ee82-224f-4a12-9baf-a0dca2656c5b
caps.latest.revision: 32
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
ms.openlocfilehash: 38b259b4d85d54467cd15cd49e5987f6198e8d99
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="access-modifiers-c-programming-guide"></a><span data-ttu-id="35ee5-102">Modificadores de acesso (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="35ee5-102">Access Modifiers (C# Programming Guide)</span></span>
<span data-ttu-id="35ee5-103">Todos os tipos e membros de tipo têm um nível de acessibilidade, que controla se podem ser usados de outro código no seu assembly ou outros assemblies.</span><span class="sxs-lookup"><span data-stu-id="35ee5-103">All types and type members have an accessibility level, which controls whether they can be used from other code in your assembly or other assemblies.</span></span> <span data-ttu-id="35ee5-104">Você pode usar os modificadores de acesso a seguir para especificar a acessibilidade de um tipo ou membro quando você o declarar:</span><span class="sxs-lookup"><span data-stu-id="35ee5-104">You can use the following access modifiers to specify the accessibility of a type or member when you declare it:</span></span>  
  
 [<span data-ttu-id="35ee5-105">public</span><span class="sxs-lookup"><span data-stu-id="35ee5-105">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
 <span data-ttu-id="35ee5-106">O tipo ou membro pode ser acessado por qualquer outro código no mesmo assembly ou em outro assembly que faz referência a ele.</span><span class="sxs-lookup"><span data-stu-id="35ee5-106">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span>  
  
 [<span data-ttu-id="35ee5-107">private</span><span class="sxs-lookup"><span data-stu-id="35ee5-107">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
 <span data-ttu-id="35ee5-108">O tipo ou membro pode ser acessado somente pelo código na mesma classe ou struct.</span><span class="sxs-lookup"><span data-stu-id="35ee5-108">The type or member can be accessed only by code in the same class or struct.</span></span>  
  
 [<span data-ttu-id="35ee5-109">protected</span><span class="sxs-lookup"><span data-stu-id="35ee5-109">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
 <span data-ttu-id="35ee5-110">O tipo ou membro pode ser acessado somente pelo código na mesma classe ou struct ou em uma classe derivada dessa classe.</span><span class="sxs-lookup"><span data-stu-id="35ee5-110">The type or member can be accessed only by code in the same class or struct, or in a class that is derived from that class.</span></span>  
  
 [<span data-ttu-id="35ee5-111">internal</span><span class="sxs-lookup"><span data-stu-id="35ee5-111">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)  
 <span data-ttu-id="35ee5-112">O tipo ou membro pode ser acessado por qualquer código no mesmo assembly, mas não de outro assembly.</span><span class="sxs-lookup"><span data-stu-id="35ee5-112">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span>  
  
 `protected internal`  
 <span data-ttu-id="35ee5-113">O tipo ou membro pode ser acessado por qualquer código no assembly no qual ele é declarado ou de uma classe derivada em outro assembly.</span><span class="sxs-lookup"><span data-stu-id="35ee5-113">The type or member can be accessed by any code in the assembly in which it is declared, or from within a derived class in another assembly.</span></span> <span data-ttu-id="35ee5-114">O acesso de outro assembly deve ocorrer dentro de uma declaração de classe que deriva da classe na qual o elemento interno protegido é declarado e deve ser executado por meio de uma instância do tipo de classe derivada.</span><span class="sxs-lookup"><span data-stu-id="35ee5-114">Access from another assembly must take place within a class declaration that derives from the class in which the protected internal element is declared, and it must take place through an instance of the derived class type.</span></span>  
  
 <span data-ttu-id="35ee5-115">Os exemplos a seguir demonstram como especificar modificadores de acesso em um tipo e membro:</span><span class="sxs-lookup"><span data-stu-id="35ee5-115">The following examples demonstrate how to specify access modifiers on a type and member:</span></span>  
  
 <span data-ttu-id="35ee5-116">[!code-cs[csProgGuideObjects#72](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/access-modifiers_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="35ee5-116">[!code-cs[csProgGuideObjects#72](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/access-modifiers_1.cs)]</span></span>  
  
 <span data-ttu-id="35ee5-117">Nem todos os modificadores de acesso podem ser usados por todos os tipos ou membros em todos os contextos e, em alguns casos, a acessibilidade de um membro de tipo é restrita pela acessibilidade do seu tipo recipiente.</span><span class="sxs-lookup"><span data-stu-id="35ee5-117">Not all access modifiers can be used by all types or members in all contexts, and in some cases the accessibility of a type member is constrained by the accessibility of its containing type.</span></span> <span data-ttu-id="35ee5-118">As seções a seguir fornecem mais detalhes sobre a acessibilidade.</span><span class="sxs-lookup"><span data-stu-id="35ee5-118">The following sections provide more details about accessibility.</span></span>  
  
## <a name="class-and-struct-accessibility"></a><span data-ttu-id="35ee5-119">Acessibilidade de classe e struct</span><span class="sxs-lookup"><span data-stu-id="35ee5-119">Class and Struct Accessibility</span></span>  
 <span data-ttu-id="35ee5-120">As classes e structs que são declarados dentro de um namespace (em outras palavras, que não estão aninhadas dentro de outras classes ou structs) podem ser públicos ou internos.</span><span class="sxs-lookup"><span data-stu-id="35ee5-120">Classes and structs that are declared directly within a namespace (in other words, that are not nested within other classes or structs) can be either public or internal.</span></span> <span data-ttu-id="35ee5-121">Interno é o padrão se nenhum modificador de acesso for especificado.</span><span class="sxs-lookup"><span data-stu-id="35ee5-121">Internal is the default if no access modifier is specified.</span></span>  
  
 <span data-ttu-id="35ee5-122">Membros de struct, incluindo classes e structs aninhados, podem ser declarados como públicos, internos ou privados.</span><span class="sxs-lookup"><span data-stu-id="35ee5-122">Struct members, including nested classes and structs, can be declared as public, internal, or private.</span></span> <span data-ttu-id="35ee5-123">Membros de classe, incluindo classes e structs aninhados, podem públicos, internos protegidos, protegidos, internos ou privados.</span><span class="sxs-lookup"><span data-stu-id="35ee5-123">Class members, including nested classes and structs, can be public, protected internal, protected, internal, or private.</span></span> <span data-ttu-id="35ee5-124">O nível de acesso para membros de classes e membros de struct, incluindo classes e structs aninhados, é privado por padrão.</span><span class="sxs-lookup"><span data-stu-id="35ee5-124">The access level for class members and struct members, including nested classes and structs, is private by default.</span></span> <span data-ttu-id="35ee5-125">Tipos aninhados privados não são acessíveis de fora do tipo recipiente.</span><span class="sxs-lookup"><span data-stu-id="35ee5-125">Private nested types are not accessible from outside the containing type.</span></span>  
  
 <span data-ttu-id="35ee5-126">Classes derivadas não podem ter acessibilidade maior do que seus tipos base.</span><span class="sxs-lookup"><span data-stu-id="35ee5-126">Derived classes cannot have greater accessibility than their base types.</span></span> <span data-ttu-id="35ee5-127">Em outras palavras, você não pode ter uma classe pública `B` que deriva de uma classe interna `A`.</span><span class="sxs-lookup"><span data-stu-id="35ee5-127">In other words, you cannot have a public class `B` that derives from an internal class `A`.</span></span> <span data-ttu-id="35ee5-128">Se isso fosse permitido, teria o efeito de tornar `A` público, pois todos os membros internos ou protegidos de `A` são acessíveis da classe derivada.</span><span class="sxs-lookup"><span data-stu-id="35ee5-128">If this were allowed, it would have the effect of making `A` public, because all protected or internal members of `A` are accessible from the derived class.</span></span>  
  
 <span data-ttu-id="35ee5-129">Você pode permitir que outros assemblies específicos acessem seus tipos internos usando o InternalsVisibleToAttribute.</span><span class="sxs-lookup"><span data-stu-id="35ee5-129">You can enable specific other assemblies to access your internal types by using the InternalsVisibleToAttribute.</span></span> <span data-ttu-id="35ee5-130">Para obter mais informações, consulte [Assemblies amigáveis](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055).</span><span class="sxs-lookup"><span data-stu-id="35ee5-130">For more information, see [Friend Assemblies](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055).</span></span>  
  
## <a name="class-and-struct-member-accessibility"></a><span data-ttu-id="35ee5-131">Acessibilidade de membro de classe e struct</span><span class="sxs-lookup"><span data-stu-id="35ee5-131">Class and Struct Member Accessibility</span></span>  
 <span data-ttu-id="35ee5-132">Membros de classe (incluindo structs e classes aninhados) podem ser declarados com qualquer um dos cinco tipos de acesso.</span><span class="sxs-lookup"><span data-stu-id="35ee5-132">Class members (including nested classes and structs) can be declared with any of the five types of access.</span></span> <span data-ttu-id="35ee5-133">Membros de struct não podem ser declarados como protegidos porque os structs não têm suporte à herança.</span><span class="sxs-lookup"><span data-stu-id="35ee5-133">Struct members cannot be declared as protected because structs do not support inheritance.</span></span>  
  
 <span data-ttu-id="35ee5-134">Normalmente, a acessibilidade de um membro não é maior que a acessibilidade do tipo que o contém.</span><span class="sxs-lookup"><span data-stu-id="35ee5-134">Normally, the accessibility of a member is not greater than the accessibility of the type that contains it.</span></span> <span data-ttu-id="35ee5-135">No entanto, um membro público de uma classe interna pode ser acessível de fora do assembly se o membro implementa os métodos de interface ou substitui os métodos virtuais que são definidos em uma classe base pública.</span><span class="sxs-lookup"><span data-stu-id="35ee5-135">However, a public member of an internal class might be accessible from outside the assembly if the member implements interface methods or overrides virtual methods that are defined in a public base class.</span></span>  
  
 <span data-ttu-id="35ee5-136">O tipo de qualquer membro que seja um campo, propriedade ou evento deve ser pelo menos tão acessível quanto o próprio membro.</span><span class="sxs-lookup"><span data-stu-id="35ee5-136">The type of any member that is a field, property, or event must be at least as accessible as the member itself.</span></span> <span data-ttu-id="35ee5-137">Da mesma forma, o tipo de retorno e os tipos de parâmetro de qualquer membro que é um método, indexador ou delegado devem ser pelo menos tão acessíveis quanto o próprio membro.</span><span class="sxs-lookup"><span data-stu-id="35ee5-137">Similarly, the return type and the parameter types of any member that is a method, indexer, or delegate must be at least as accessible as the member itself.</span></span> <span data-ttu-id="35ee5-138">Por exemplo, você não pode ter um método público `M` que retorna uma classe `C`, a menos que `C` também seja público.</span><span class="sxs-lookup"><span data-stu-id="35ee5-138">For example, you cannot have a public method `M` that returns a class `C` unless `C` is also public.</span></span> <span data-ttu-id="35ee5-139">Da mesma forma, você não pode ter uma propriedade protegida do tipo `A` se `A` for declarado como particular.</span><span class="sxs-lookup"><span data-stu-id="35ee5-139">Likewise, you cannot have a protected property of type `A` if `A` is declared as private.</span></span>  
  
 <span data-ttu-id="35ee5-140">Os operadores definidos pelo usuário sempre devem ser declarados como públicos.</span><span class="sxs-lookup"><span data-stu-id="35ee5-140">User-defined operators must always be declared as public.</span></span> <span data-ttu-id="35ee5-141">Para obter mais informações, consulte [operador (Referência de C#)](../../../csharp/language-reference/keywords/operator.md).</span><span class="sxs-lookup"><span data-stu-id="35ee5-141">For more information, see [operator (C# Reference)](../../../csharp/language-reference/keywords/operator.md).</span></span>  
  
 <span data-ttu-id="35ee5-142">Os finalizadores não podem ter modificadores de acessibilidade.</span><span class="sxs-lookup"><span data-stu-id="35ee5-142">Finalizers cannot have accessibility modifiers.</span></span>  
  
 <span data-ttu-id="35ee5-143">Para definir o nível de acesso para um membro de classe ou de struct, adicione a palavra-chave apropriada à declaração do membro, como mostrado o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="35ee5-143">To set the access level for a class or struct member, add the appropriate keyword to the member declaration, as shown in the following example.</span></span>  
  
 <span data-ttu-id="35ee5-144">[!code-cs[csProgGuideObjects#73](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/access-modifiers_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="35ee5-144">[!code-cs[csProgGuideObjects#73](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/access-modifiers_2.cs)]</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="35ee5-145">O nível de acessibilidade interno protegido significa protegido OU interno, não protegido E interno.</span><span class="sxs-lookup"><span data-stu-id="35ee5-145">The protected internal accessibility level means protected OR internal, not protected AND internal.</span></span> <span data-ttu-id="35ee5-146">Em outras palavras, um membro interno protegido pode ser acessado de qualquer classe no mesmo assembly, incluindo as classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="35ee5-146">In other words, a protected internal member can be accessed from any class in the same assembly, including derived classes.</span></span> <span data-ttu-id="35ee5-147">Para limitar a acessibilidade para apenas classes derivadas no mesmo assembly, declare a classe em si como interna e declare seus membros como protegidos.</span><span class="sxs-lookup"><span data-stu-id="35ee5-147">To limit accessibility to only derived classes in the same assembly, declare the class itself internal, and declare its members as protected.</span></span>  
  
## <a name="other-types"></a><span data-ttu-id="35ee5-148">Outros tipos</span><span class="sxs-lookup"><span data-stu-id="35ee5-148">Other Types</span></span>  
 <span data-ttu-id="35ee5-149">Interfaces declaradas diretamente dentro de um namespace podem ser declaradas como públicas ou internas e, exatamente como as classes e structs, as interfaces assumem como padrão o acesso interno.</span><span class="sxs-lookup"><span data-stu-id="35ee5-149">Interfaces declared directly within a namespace can be declared as public or internal and, just like classes and structs, interfaces default to internal access.</span></span> <span data-ttu-id="35ee5-150">Membros de interface sempre são públicos, pois a finalidade de uma interface é permitir que outros tipos acessem uma classe ou struct.</span><span class="sxs-lookup"><span data-stu-id="35ee5-150">Interface members are always public because the purpose of an interface is to enable other types to access a class or struct.</span></span> <span data-ttu-id="35ee5-151">Nenhum modificador de acesso pode ser aplicado aos membros de interface.</span><span class="sxs-lookup"><span data-stu-id="35ee5-151">No access modifiers can be applied to interface members.</span></span>  
  
 <span data-ttu-id="35ee5-152">Membros de enumeração sempre são públicos e nenhum modificador de acesso pode ser aplicado.</span><span class="sxs-lookup"><span data-stu-id="35ee5-152">Enumeration members are always public, and no access modifiers can be applied.</span></span>  
  
 <span data-ttu-id="35ee5-153">Delegados se comportam como classes e structs.</span><span class="sxs-lookup"><span data-stu-id="35ee5-153">Delegates behave like classes and structs.</span></span> <span data-ttu-id="35ee5-154">Por padrão, eles têm acesso interno quando declarados diretamente dentro de um namespace e acesso privado quando aninhados.</span><span class="sxs-lookup"><span data-stu-id="35ee5-154">By default, they have internal access when declared directly within a namespace, and private access when nested.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="35ee5-155">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="35ee5-155">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="35ee5-156">Consulte também</span><span class="sxs-lookup"><span data-stu-id="35ee5-156">See Also</span></span>  
 <span data-ttu-id="35ee5-157">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="35ee5-157">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="35ee5-158">[Classes e structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span><span class="sxs-lookup"><span data-stu-id="35ee5-158">[Classes and Structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span></span>  
 <span data-ttu-id="35ee5-159">[Interfaces](../../../csharp/programming-guide/interfaces/index.md) </span><span class="sxs-lookup"><span data-stu-id="35ee5-159">[Interfaces](../../../csharp/programming-guide/interfaces/index.md) </span></span>  
 <span data-ttu-id="35ee5-160">[private](../../../csharp/language-reference/keywords/private.md) </span><span class="sxs-lookup"><span data-stu-id="35ee5-160">[private](../../../csharp/language-reference/keywords/private.md) </span></span>  
 <span data-ttu-id="35ee5-161">[public](../../../csharp/language-reference/keywords/public.md) </span><span class="sxs-lookup"><span data-stu-id="35ee5-161">[public](../../../csharp/language-reference/keywords/public.md) </span></span>  
 <span data-ttu-id="35ee5-162">[internal](../../../csharp/language-reference/keywords/internal.md) </span><span class="sxs-lookup"><span data-stu-id="35ee5-162">[internal](../../../csharp/language-reference/keywords/internal.md) </span></span>  
 <span data-ttu-id="35ee5-163">[protected](../../../csharp/language-reference/keywords/protected.md) </span><span class="sxs-lookup"><span data-stu-id="35ee5-163">[protected](../../../csharp/language-reference/keywords/protected.md) </span></span>  
 <span data-ttu-id="35ee5-164">[class](../../../csharp/language-reference/keywords/class.md) </span><span class="sxs-lookup"><span data-stu-id="35ee5-164">[class](../../../csharp/language-reference/keywords/class.md) </span></span>  
 <span data-ttu-id="35ee5-165">[struct](../../../csharp/language-reference/keywords/struct.md) </span><span class="sxs-lookup"><span data-stu-id="35ee5-165">[struct](../../../csharp/language-reference/keywords/struct.md) </span></span>  
 [<span data-ttu-id="35ee5-166">interface</span><span class="sxs-lookup"><span data-stu-id="35ee5-166">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)

