---
title: Design de Struct
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
ms.openlocfilehash: b6d06bc8a1e8535f1452af0726138abaebfd4951
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743605"
---
# <a name="struct-design"></a><span data-ttu-id="c9e95-102">Design de Struct</span><span class="sxs-lookup"><span data-stu-id="c9e95-102">Struct Design</span></span>
<span data-ttu-id="c9e95-103">O tipo de valor de uso geral é geralmente referido como struct, sua C# palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="c9e95-103">The general-purpose value type is most often referred to as a struct, its C# keyword.</span></span> <span data-ttu-id="c9e95-104">Esta seção fornece diretrizes para o design geral de struct.</span><span class="sxs-lookup"><span data-stu-id="c9e95-104">This section provides guidelines for general struct design.</span></span>

 <span data-ttu-id="c9e95-105">❌ não fornecem um construtor sem parâmetros para um struct.</span><span class="sxs-lookup"><span data-stu-id="c9e95-105">❌ DO NOT provide a parameterless constructor for a struct.</span></span>

 <span data-ttu-id="c9e95-106">Seguir essa diretriz permite que matrizes de structs sejam criadas sem a necessidade de executar o Construtor em cada item da matriz.</span><span class="sxs-lookup"><span data-stu-id="c9e95-106">Following this guideline allows arrays of structs to be created without having to run the constructor on each item of the array.</span></span> <span data-ttu-id="c9e95-107">Observe que C# o não permite que structs tenham construtores sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="c9e95-107">Notice that C# does not allow structs to have parameterless constructors.</span></span>

 <span data-ttu-id="c9e95-108">❌ não definir tipos de valor mutável.</span><span class="sxs-lookup"><span data-stu-id="c9e95-108">❌ DO NOT define mutable value types.</span></span>

 <span data-ttu-id="c9e95-109">Os tipos de valores mutáveis têm vários problemas.</span><span class="sxs-lookup"><span data-stu-id="c9e95-109">Mutable value types have several problems.</span></span> <span data-ttu-id="c9e95-110">Por exemplo, quando um getter de propriedade retorna um tipo de valor, o chamador recebe uma cópia.</span><span class="sxs-lookup"><span data-stu-id="c9e95-110">For example, when a property getter returns a value type, the caller receives a copy.</span></span> <span data-ttu-id="c9e95-111">Como a cópia é criada implicitamente, os desenvolvedores podem não estar cientes de que estão modificando a cópia e não o valor original.</span><span class="sxs-lookup"><span data-stu-id="c9e95-111">Because the copy is created implicitly, developers might not be aware that they are mutating the copy, and not the original value.</span></span> <span data-ttu-id="c9e95-112">Além disso, algumas linguagens (linguagens dinâmicas, em particular) têm problemas ao usar tipos de valor mutável porque até mesmo variáveis locais, quando desreferenciadas, fazem com que uma cópia seja feita.</span><span class="sxs-lookup"><span data-stu-id="c9e95-112">Also, some languages (dynamic languages, in particular) have problems using mutable value types because even local variables, when dereferenced, cause a copy to be made.</span></span>

 <span data-ttu-id="c9e95-113">✔️ garantir que um estado em que todos os dados da instância esteja definido como zero, falso ou nulo (conforme apropriado) seja válido.</span><span class="sxs-lookup"><span data-stu-id="c9e95-113">✔️ DO ensure that a state where all instance data is set to zero, false, or null (as appropriate) is valid.</span></span>

 <span data-ttu-id="c9e95-114">Isso impede a criação acidental de instâncias inválidas quando uma matriz de structs é criada.</span><span class="sxs-lookup"><span data-stu-id="c9e95-114">This prevents accidental creation of invalid instances when an array of the structs is created.</span></span>

 <span data-ttu-id="c9e95-115">✔️ implementar <xref:System.IEquatable%601> em tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="c9e95-115">✔️ DO implement <xref:System.IEquatable%601> on value types.</span></span>

 <span data-ttu-id="c9e95-116">O método <xref:System.Object.Equals%2A?displayProperty=nameWithType> em tipos de valor causa boxing, e sua implementação padrão não é muito eficiente, pois ela usa reflexão.</span><span class="sxs-lookup"><span data-stu-id="c9e95-116">The <xref:System.Object.Equals%2A?displayProperty=nameWithType> method on value types causes boxing, and its default implementation is not very efficient, because it uses reflection.</span></span> <span data-ttu-id="c9e95-117"><xref:System.IEquatable%601.Equals%2A> pode ter um desempenho muito melhor e pode ser implementado para que não cause boxing.</span><span class="sxs-lookup"><span data-stu-id="c9e95-117"><xref:System.IEquatable%601.Equals%2A> can have much better performance and can be implemented so that it will not cause boxing.</span></span>

 <span data-ttu-id="c9e95-118">❌ não estender explicitamente <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="c9e95-118">❌ DO NOT explicitly extend <xref:System.ValueType>.</span></span> <span data-ttu-id="c9e95-119">Na verdade, a maioria dos idiomas impede isso.</span><span class="sxs-lookup"><span data-stu-id="c9e95-119">In fact, most languages prevent this.</span></span>

 <span data-ttu-id="c9e95-120">Em geral, as estruturas podem ser muito úteis, mas devem ser usadas somente para valores pequenos, únicos e imutáveis que não serão emoldurados com frequência.</span><span class="sxs-lookup"><span data-stu-id="c9e95-120">In general, structs can be very useful but should only be used for small, single, immutable values that will not be boxed frequently.</span></span>

 <span data-ttu-id="c9e95-121">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="c9e95-121">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="c9e95-122">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="c9e95-122">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="c9e95-123">Veja também</span><span class="sxs-lookup"><span data-stu-id="c9e95-123">See also</span></span>

- [<span data-ttu-id="c9e95-124">Diretrizes de Design de tipo</span><span class="sxs-lookup"><span data-stu-id="c9e95-124">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)
- [<span data-ttu-id="c9e95-125">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="c9e95-125">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="c9e95-126">Escolhendo entre a classe e Struct</span><span class="sxs-lookup"><span data-stu-id="c9e95-126">Choosing Between Class and Struct</span></span>](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)
