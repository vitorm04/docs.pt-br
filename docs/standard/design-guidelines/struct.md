---
title: Estrutura de Design
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- deallocating structures
- allocating structures
- value types, structures
- structure design
- type design guidelines, structures
- structures [.NET Framework], design guidelines
ms.assetid: 1f48b2d8-608c-4be6-9ba4-d8f203ed9f9f
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2f4a6debc25a51e3a0a83e70fc8c8f8fc55c62f5
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="struct-design"></a><span data-ttu-id="4b302-102">Estrutura de Design</span><span class="sxs-lookup"><span data-stu-id="4b302-102">Struct Design</span></span>
<span data-ttu-id="4b302-103">O tipo de valor de uso geral é mais conhecido como uma estrutura, sua palavra-chave c#.</span><span class="sxs-lookup"><span data-stu-id="4b302-103">The general-purpose value type is most often referred to as a struct, its C# keyword.</span></span> <span data-ttu-id="4b302-104">Esta seção fornece diretrizes para o design da estrutura geral.</span><span class="sxs-lookup"><span data-stu-id="4b302-104">This section provides guidelines for general struct design.</span></span>  
  
 <span data-ttu-id="4b302-105">**X não** fornecer um construtor padrão para um struct.</span><span class="sxs-lookup"><span data-stu-id="4b302-105">**X DO NOT** provide a default constructor for a struct.</span></span>  
  
 <span data-ttu-id="4b302-106">Seguir essa diretriz permite matrizes de estruturas a ser criado sem a necessidade de executar o construtor em cada item da matriz.</span><span class="sxs-lookup"><span data-stu-id="4b302-106">Following this guideline allows arrays of structs to be created without having to run the constructor on each item of the array.</span></span> <span data-ttu-id="4b302-107">Observe que c# não permite estruturas ter construtores padrão.</span><span class="sxs-lookup"><span data-stu-id="4b302-107">Notice that C# does not allow structs to have default constructors.</span></span>  
  
 <span data-ttu-id="4b302-108">**X não** definir tipos de valor mutável.</span><span class="sxs-lookup"><span data-stu-id="4b302-108">**X DO NOT** define mutable value types.</span></span>  
  
 <span data-ttu-id="4b302-109">Tipos de valor mutável tem vários problemas.</span><span class="sxs-lookup"><span data-stu-id="4b302-109">Mutable value types have several problems.</span></span> <span data-ttu-id="4b302-110">Por exemplo, quando uma propriedade getter retorna um tipo de valor, o chamador recebe uma cópia.</span><span class="sxs-lookup"><span data-stu-id="4b302-110">For example, when a property getter returns a value type, the caller receives a copy.</span></span> <span data-ttu-id="4b302-111">Como a cópia é criada implicitamente, os desenvolvedores podem não estar cientes de que eles são mutação a cópia e não o valor original.</span><span class="sxs-lookup"><span data-stu-id="4b302-111">Because the copy is created implicitly, developers might not be aware that they are mutating the copy, and not the original value.</span></span> <span data-ttu-id="4b302-112">Além disso, alguns idiomas (linguagens dinâmicas, em particular) tem problemas para usar tipos de valor mutável porque mesmo variáveis locais, quando cancelada, fazer com que uma cópia a serem feitas.</span><span class="sxs-lookup"><span data-stu-id="4b302-112">Also, some languages (dynamic languages, in particular) have problems using mutable value types because even local variables, when dereferenced, cause a copy to be made.</span></span>  
  
 <span data-ttu-id="4b302-113">**FAZER ✓** Certifique-se de que um estado em que todos os dados da instância é definido como zero, false ou null (conforme apropriado) é válido.</span><span class="sxs-lookup"><span data-stu-id="4b302-113">**✓ DO** ensure that a state where all instance data is set to zero, false, or null (as appropriate) is valid.</span></span>  
  
 <span data-ttu-id="4b302-114">Isso impede que acidental criação de instâncias inválidas quando uma matriz de estruturas de é criada.</span><span class="sxs-lookup"><span data-stu-id="4b302-114">This prevents accidental creation of invalid instances when an array of the structs is created.</span></span>  
  
 <span data-ttu-id="4b302-115">**FAZER ✓** implementar <xref:System.IEquatable%601> em tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="4b302-115">**✓ DO** implement <xref:System.IEquatable%601> on value types.</span></span>  
  
 <span data-ttu-id="4b302-116">O <xref:System.Object.Equals%2A?displayProperty=nameWithType> método em tipos de valor faz com que a conversão boxing e sua implementação padrão não é muito eficiente, pois ela usa reflexão.</span><span class="sxs-lookup"><span data-stu-id="4b302-116">The <xref:System.Object.Equals%2A?displayProperty=nameWithType> method on value types causes boxing, and its default implementation is not very efficient, because it uses reflection.</span></span> <span data-ttu-id="4b302-117"><xref:System.IEquatable%601.Equals%2A>pode ter um desempenho muito melhor e pode ser implementado para que ele não fará com que a conversão boxing.</span><span class="sxs-lookup"><span data-stu-id="4b302-117"><xref:System.IEquatable%601.Equals%2A> can have much better performance and can be implemented so that it will not cause boxing.</span></span>  
  
 <span data-ttu-id="4b302-118">**X não** estender explicitamente <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="4b302-118">**X DO NOT** explicitly extend <xref:System.ValueType>.</span></span> <span data-ttu-id="4b302-119">Na verdade, a maioria das linguagens evitar isso.</span><span class="sxs-lookup"><span data-stu-id="4b302-119">In fact, most languages prevent this.</span></span>  
  
 <span data-ttu-id="4b302-120">Em geral, structs pode ser muito útil, mas só deve ser usadas para valores pequenos, único, imutáveis que não serão demarcados com frequência.</span><span class="sxs-lookup"><span data-stu-id="4b302-120">In general, structs can be very useful but should only be used for small, single, immutable values that will not be boxed frequently.</span></span>  
  
 <span data-ttu-id="4b302-121">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="4b302-121">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="4b302-122">*Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="4b302-122">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b302-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4b302-123">See Also</span></span>  
 [<span data-ttu-id="4b302-124">Diretrizes de Design de tipo</span><span class="sxs-lookup"><span data-stu-id="4b302-124">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 [<span data-ttu-id="4b302-125">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="4b302-125">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="4b302-126">Escolhendo entre a classe e Struct</span><span class="sxs-lookup"><span data-stu-id="4b302-126">Choosing Between Class and Struct</span></span>](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)
