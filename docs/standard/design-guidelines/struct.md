---
title: Design de struct
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- deallocating structures
- allocating structures
- value types, structures
- structure design
- type design guidelines, structures
- structures [.NET Framework], design guidelines
ms.assetid: 1f48b2d8-608c-4be6-9ba4-d8f203ed9f9f
author: KrzysztofCwalina
ms.openlocfilehash: 240492590fab4579b9d984d5dce759f6d9f8cbab
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53153105"
---
# <a name="struct-design"></a><span data-ttu-id="6a641-102">Design de struct</span><span class="sxs-lookup"><span data-stu-id="6a641-102">Struct Design</span></span>
<span data-ttu-id="6a641-103">O tipo de valor de uso geral é mais conhecido como um struct, sua palavra-chave c#.</span><span class="sxs-lookup"><span data-stu-id="6a641-103">The general-purpose value type is most often referred to as a struct, its C# keyword.</span></span> <span data-ttu-id="6a641-104">Esta seção fornece diretrizes para design de struct geral.</span><span class="sxs-lookup"><span data-stu-id="6a641-104">This section provides guidelines for general struct design.</span></span>  
  
 <span data-ttu-id="6a641-105">**X DO NOT** fornecer um construtor padrão para um struct.</span><span class="sxs-lookup"><span data-stu-id="6a641-105">**X DO NOT** provide a default constructor for a struct.</span></span>  
  
 <span data-ttu-id="6a641-106">Seguir essa diretriz permite matrizes de structs são criados sem necessidade de executar o construtor em cada item da matriz.</span><span class="sxs-lookup"><span data-stu-id="6a641-106">Following this guideline allows arrays of structs to be created without having to run the constructor on each item of the array.</span></span> <span data-ttu-id="6a641-107">Observe que c# não permite estruturas ter construtores padrão.</span><span class="sxs-lookup"><span data-stu-id="6a641-107">Notice that C# does not allow structs to have default constructors.</span></span>  
  
 <span data-ttu-id="6a641-108">**X DO NOT** definir tipos de valor mutável.</span><span class="sxs-lookup"><span data-stu-id="6a641-108">**X DO NOT** define mutable value types.</span></span>  
  
 <span data-ttu-id="6a641-109">Tipos de valor mutável tem vários problemas.</span><span class="sxs-lookup"><span data-stu-id="6a641-109">Mutable value types have several problems.</span></span> <span data-ttu-id="6a641-110">Por exemplo, quando um getter de propriedade retorna um tipo de valor, o chamador recebe uma cópia.</span><span class="sxs-lookup"><span data-stu-id="6a641-110">For example, when a property getter returns a value type, the caller receives a copy.</span></span> <span data-ttu-id="6a641-111">Como a cópia é criada implicitamente, os desenvolvedores podem não estar cientes de que eles são mutação a cópia e não o valor original.</span><span class="sxs-lookup"><span data-stu-id="6a641-111">Because the copy is created implicitly, developers might not be aware that they are mutating the copy, and not the original value.</span></span> <span data-ttu-id="6a641-112">Além disso, alguns idiomas (linguagens dinâmicas, em particular) tem problemas ao usar tipos de valor mutável porque mesmo variáveis locais, quando desreferenciado, fazer com que uma cópia a ser feita.</span><span class="sxs-lookup"><span data-stu-id="6a641-112">Also, some languages (dynamic languages, in particular) have problems using mutable value types because even local variables, when dereferenced, cause a copy to be made.</span></span>  
  
 <span data-ttu-id="6a641-113">**✓ DO** Certifique-se de que um estado em que todos os dados da instância é definido como zero, false ou null (conforme apropriado) é válido.</span><span class="sxs-lookup"><span data-stu-id="6a641-113">**✓ DO** ensure that a state where all instance data is set to zero, false, or null (as appropriate) is valid.</span></span>  
  
 <span data-ttu-id="6a641-114">Isso impede a criação acidental de instâncias inválidas quando uma matriz de estruturas de é criada.</span><span class="sxs-lookup"><span data-stu-id="6a641-114">This prevents accidental creation of invalid instances when an array of the structs is created.</span></span>  
  
 <span data-ttu-id="6a641-115">**✓ DO** implementar <xref:System.IEquatable%601> em tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="6a641-115">**✓ DO** implement <xref:System.IEquatable%601> on value types.</span></span>  
  
 <span data-ttu-id="6a641-116">O <xref:System.Object.Equals%2A?displayProperty=nameWithType> método em tipos de valor faz com que a conversão boxing e sua implementação padrão não é muito eficiente, porque ele usa a reflexão.</span><span class="sxs-lookup"><span data-stu-id="6a641-116">The <xref:System.Object.Equals%2A?displayProperty=nameWithType> method on value types causes boxing, and its default implementation is not very efficient, because it uses reflection.</span></span> <span data-ttu-id="6a641-117"><xref:System.IEquatable%601.Equals%2A> pode ter um desempenho muito melhor e pode ser implementado para que ele não fará com que a conversão boxing.</span><span class="sxs-lookup"><span data-stu-id="6a641-117"><xref:System.IEquatable%601.Equals%2A> can have much better performance and can be implemented so that it will not cause boxing.</span></span>  
  
 <span data-ttu-id="6a641-118">**X DO NOT** estender explicitamente <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="6a641-118">**X DO NOT** explicitly extend <xref:System.ValueType>.</span></span> <span data-ttu-id="6a641-119">Na verdade, a maioria das linguagens de evitar isso.</span><span class="sxs-lookup"><span data-stu-id="6a641-119">In fact, most languages prevent this.</span></span>  
  
 <span data-ttu-id="6a641-120">Em geral, structs pode ser muito útil, mas só deve ser usados para valores pequenos, único e imutáveis que não serão ser boxed com frequência.</span><span class="sxs-lookup"><span data-stu-id="6a641-120">In general, structs can be very useful but should only be used for small, single, immutable values that will not be boxed frequently.</span></span>  
  
 <span data-ttu-id="6a641-121">*Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="6a641-121">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="6a641-122">*Reimpresso com permissão da Pearson Education, Inc. de [as diretrizes de Design do Framework: As convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008 pela Addison-Wesley Professional, como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="6a641-122">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a641-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6a641-123">See also</span></span>

- [<span data-ttu-id="6a641-124">Diretrizes de Design de tipo</span><span class="sxs-lookup"><span data-stu-id="6a641-124">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
- [<span data-ttu-id="6a641-125">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="6a641-125">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="6a641-126">Escolhendo entre a classe e Struct</span><span class="sxs-lookup"><span data-stu-id="6a641-126">Choosing Between Class and Struct</span></span>](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)
