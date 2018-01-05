---
title: "Métodos de extensão"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5de945cb-88f4-49d7-b0e6-f098300cf357
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 28ce4451f9f8cc634ab76b3b4ef845103ea55e35
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="extension-methods"></a><span data-ttu-id="cd839-102">Métodos de extensão</span><span class="sxs-lookup"><span data-stu-id="cd839-102">Extension Methods</span></span>
<span data-ttu-id="cd839-103">Métodos de extensão são um recurso de linguagem que permite que os métodos estáticos ser chamado usando a sintaxe de chamada de método de instância.</span><span class="sxs-lookup"><span data-stu-id="cd839-103">Extension methods are a language feature that allows static methods to be called using instance method call syntax.</span></span> <span data-ttu-id="cd839-104">Esses métodos devem ter pelo menos um parâmetro, que representa a instância em que é o método operar.</span><span class="sxs-lookup"><span data-stu-id="cd839-104">These methods must take at least one parameter, which represents the instance the method is to operate on.</span></span>  
  
 <span data-ttu-id="cd839-105">A classe que define esses métodos de extensão é conhecida como a classe "Patrocinador", e ele deve ser declarado como estático.</span><span class="sxs-lookup"><span data-stu-id="cd839-105">The class that defines such extension methods is referred to as the "sponsor" class, and it must be declared as static.</span></span> <span data-ttu-id="cd839-106">Para usar os métodos de extensão, uma deve importar o namespace de definição de classe patrocinador.</span><span class="sxs-lookup"><span data-stu-id="cd839-106">To use extension methods, one must import the namespace defining the sponsor class.</span></span>  
  
 <span data-ttu-id="cd839-107">**X Evite** frivolously definir métodos de extensão, especialmente em tipos que você não possui.</span><span class="sxs-lookup"><span data-stu-id="cd839-107">**X AVOID** frivolously defining extension methods, especially on types you don’t own.</span></span>  
  
 <span data-ttu-id="cd839-108">Se você é proprietário de um tipo de código-fonte, considere o uso de métodos de instância regular.</span><span class="sxs-lookup"><span data-stu-id="cd839-108">If you do own source code of a type, consider using regular instance methods instead.</span></span> <span data-ttu-id="cd839-109">Se você não possui, e você deseja adicionar um método, tenha muito cuidado.</span><span class="sxs-lookup"><span data-stu-id="cd839-109">If you don’t own, and you want to add a method, be very careful.</span></span> <span data-ttu-id="cd839-110">Uso livre dos métodos de extensão tem o potencial de problemas de APIs de tipos que não foram projetados para que esses métodos.</span><span class="sxs-lookup"><span data-stu-id="cd839-110">Liberal use of extension methods has the potential of cluttering APIs of types that were not designed to have these methods.</span></span>  
  
 <span data-ttu-id="cd839-111">**✓ CONSIDERE** usando métodos de extensão em qualquer um dos seguintes cenários:</span><span class="sxs-lookup"><span data-stu-id="cd839-111">**✓ CONSIDER** using extension methods in any of the following scenarios:</span></span>  
  
-   <span data-ttu-id="cd839-112">Para fornecer auxiliar funcionalidade relevante para cada implementação de uma interface, diz funcionalidade pode ser gravada em termos de interface principal.</span><span class="sxs-lookup"><span data-stu-id="cd839-112">To provide helper functionality relevant to every implementation of an interface, if said functionality can be written in terms of the core interface.</span></span> <span data-ttu-id="cd839-113">Isso ocorre porque as implementações concretas caso contrário, não podem ser atribuídas às interfaces.</span><span class="sxs-lookup"><span data-stu-id="cd839-113">This is because concrete implementations cannot otherwise be assigned to interfaces.</span></span> <span data-ttu-id="cd839-114">Por exemplo, o `LINQ to Objects` operadores são implementados como métodos de extensão para todos os <xref:System.Collections.Generic.IEnumerable%601> tipos.</span><span class="sxs-lookup"><span data-stu-id="cd839-114">For example, the `LINQ to Objects` operators are implemented as extension methods for all <xref:System.Collections.Generic.IEnumerable%601> types.</span></span> <span data-ttu-id="cd839-115">Portanto, qualquer `IEnumerable<>` implementação é habilitado automaticamente LINQ.</span><span class="sxs-lookup"><span data-stu-id="cd839-115">Thus, any `IEnumerable<>` implementation is automatically LINQ-enabled.</span></span>  
  
-   <span data-ttu-id="cd839-116">Quando um método de instância introduz uma dependência em algum tipo, mas tal dependência interrompe as regras de gerenciamento de dependência.</span><span class="sxs-lookup"><span data-stu-id="cd839-116">When an instance method would introduce a dependency on some type, but such a dependency would break dependency management rules.</span></span> <span data-ttu-id="cd839-117">Por exemplo, uma dependência do <xref:System.String> para <xref:System.Uri?displayProperty=nameWithType> provavelmente não é desejável e isso `String.ToUri()` retornando do método de instância `System.Uri` seria o design incorreto de uma perspectiva de gerenciamento de dependência.</span><span class="sxs-lookup"><span data-stu-id="cd839-117">For example, a dependency from <xref:System.String> to <xref:System.Uri?displayProperty=nameWithType> is probably not desirable, and so `String.ToUri()` instance method returning `System.Uri` would be the wrong design from a dependency management perspective.</span></span> <span data-ttu-id="cd839-118">Um método de extensão estático `Uri.ToUri(this string str)` retornando `System.Uri` seria um muito melhor design.</span><span class="sxs-lookup"><span data-stu-id="cd839-118">A static extension method `Uri.ToUri(this string str)` returning `System.Uri` would be a much better design.</span></span>  
  
 <span data-ttu-id="cd839-119">**X Evite** definir métodos de extensão em <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cd839-119">**X AVOID** defining extension methods on <xref:System.Object?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="cd839-120">Os usuários do VB não poderá chamar esses métodos em referências de objeto usando a sintaxe de método de extensão.</span><span class="sxs-lookup"><span data-stu-id="cd839-120">VB users will not be able to call such methods on object references using the extension method syntax.</span></span> <span data-ttu-id="cd839-121">VB não oferece suporte para chamar esses métodos porque, em VB, declarar uma referência como objeto força todas as invocações de método nele para atraso associado (chamado de membro real é determinado em tempo de execução), enquanto as associações para métodos de extensão são determinadas em tempo de compilação (antecipada vinculado).</span><span class="sxs-lookup"><span data-stu-id="cd839-121">VB does not support calling such methods because, in VB, declaring a reference as Object forces all method invocations on it to be late bound (actual member called is determined at runtime), while bindings to extension methods are determined at compile-time (early bound).</span></span>  
  
 <span data-ttu-id="cd839-122">Observe que a diretriz se aplica a outros idiomas em que o mesmo comportamento de associação está presente, ou onde não há suporte para métodos de extensão.</span><span class="sxs-lookup"><span data-stu-id="cd839-122">Note that the guideline applies to other languages where the same binding behavior is present, or where extension methods are not supported.</span></span>  
  
 <span data-ttu-id="cd839-123">**X não** colocar os métodos de extensão no mesmo namespace que o tipo estendido, a menos que ele seja para a adição de métodos para interfaces de ou para o gerenciamento de dependência.</span><span class="sxs-lookup"><span data-stu-id="cd839-123">**X DO NOT** put extension methods in the same namespace as the extended type unless it is for adding methods to interfaces or for dependency management.</span></span>  
  
 <span data-ttu-id="cd839-124">**X Evite** definir dois ou mais métodos de extensão com a mesma assinatura, mesmo que eles estejam em namespaces diferentes.</span><span class="sxs-lookup"><span data-stu-id="cd839-124">**X AVOID** defining two or more extension methods with the same signature, even if they reside in different namespaces.</span></span>  
  
 <span data-ttu-id="cd839-125">**✓ CONSIDERE** definir métodos de extensão no mesmo namespace que o tipo estendido se o tipo é uma interface e se os métodos de extensão devem ser usados na maioria dos casos.</span><span class="sxs-lookup"><span data-stu-id="cd839-125">**✓ CONSIDER** defining extension methods in the same namespace as the extended type if the type is an interface and if the extension methods are meant to be used in most or all cases.</span></span>  
  
 <span data-ttu-id="cd839-126">**X não** definir métodos de extensão implementando um recurso nos namespaces normalmente associados com outros recursos.</span><span class="sxs-lookup"><span data-stu-id="cd839-126">**X DO NOT** define extension methods implementing a feature in namespaces normally associated with other features.</span></span> <span data-ttu-id="cd839-127">Em vez disso, defini-los no namespace associado com o recurso que eles pertencem.</span><span class="sxs-lookup"><span data-stu-id="cd839-127">Instead, define them in the namespace associated with the feature they belong to.</span></span>  
  
 <span data-ttu-id="cd839-128">**X Evite** genérico de nomenclatura de namespaces dedicado para métodos de extensão (por exemplo, "extensões").</span><span class="sxs-lookup"><span data-stu-id="cd839-128">**X AVOID** generic naming of namespaces dedicated to extension methods (e.g., "Extensions").</span></span> <span data-ttu-id="cd839-129">Use um nome descritivo (por exemplo, "roteamento") em vez disso.</span><span class="sxs-lookup"><span data-stu-id="cd839-129">Use a descriptive name (e.g., "Routing") instead.</span></span>  
  
 <span data-ttu-id="cd839-130">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="cd839-130">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="cd839-131">*Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="cd839-131">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd839-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cd839-132">See Also</span></span>  
 [<span data-ttu-id="cd839-133">Diretrizes de design de membro</span><span class="sxs-lookup"><span data-stu-id="cd839-133">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 [<span data-ttu-id="cd839-134">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="cd839-134">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
