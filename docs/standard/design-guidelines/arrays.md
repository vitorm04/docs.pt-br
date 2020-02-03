---
title: Matrizes
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], arrays
- arrays [.NET Framework], usage guidelines
- empty arrays
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
ms.openlocfilehash: d4a1f379a88231654c710b1df7b505316377c915
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741797"
---
# <a name="arrays"></a><span data-ttu-id="82374-102">Matrizes</span><span class="sxs-lookup"><span data-stu-id="82374-102">Arrays</span></span>
<span data-ttu-id="82374-103">✔️ preferir usar coleções em matrizes em APIs públicas.</span><span class="sxs-lookup"><span data-stu-id="82374-103">✔️ DO prefer using collections over arrays in public APIs.</span></span> <span data-ttu-id="82374-104">A seção [coleções](../../../docs/standard/design-guidelines/guidelines-for-collections.md) fornece detalhes sobre como escolher entre coleções e matrizes.</span><span class="sxs-lookup"><span data-stu-id="82374-104">The [Collections](../../../docs/standard/design-guidelines/guidelines-for-collections.md) section provides details about how to choose between collections and arrays.</span></span>

 <span data-ttu-id="82374-105">❌ não use campos de matriz somente leitura.</span><span class="sxs-lookup"><span data-stu-id="82374-105">❌ DO NOT use read-only array fields.</span></span> <span data-ttu-id="82374-106">O próprio campo é somente leitura e não pode ser alterado, mas os elementos na matriz podem ser alterados.</span><span class="sxs-lookup"><span data-stu-id="82374-106">The field itself is read-only and can't be changed, but elements in the array can be changed.</span></span>

 <span data-ttu-id="82374-107">✔️ Considere o uso de matrizes denteadas em vez de matrizes multidimensionais.</span><span class="sxs-lookup"><span data-stu-id="82374-107">✔️ CONSIDER using jagged arrays instead of multidimensional arrays.</span></span>

 <span data-ttu-id="82374-108">Uma matriz denteada é uma matriz com elementos que também são matrizes.</span><span class="sxs-lookup"><span data-stu-id="82374-108">A jagged array is an array with elements that are also arrays.</span></span> <span data-ttu-id="82374-109">As matrizes que compõem os elementos podem ser de tamanhos diferentes, levando a menos espaço desperdiçado para alguns conjuntos de dados (por exemplo, matriz esparsa) em comparação com matrizes multidimensionais.</span><span class="sxs-lookup"><span data-stu-id="82374-109">The arrays that make up the elements can be of different sizes, leading to less wasted space for some sets of data (e.g., sparse matrix) compared to multidimensional arrays.</span></span> <span data-ttu-id="82374-110">Além disso, o CLR otimiza as operações de índice em matrizes denteadas, para que possam apresentar um melhor desempenho de tempo de execução em alguns cenários.</span><span class="sxs-lookup"><span data-stu-id="82374-110">Furthermore, the CLR optimizes index operations on jagged arrays, so they might exhibit better runtime performance in some scenarios.</span></span>

 <span data-ttu-id="82374-111">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="82374-111">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="82374-112">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="82374-112">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="82374-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="82374-113">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="82374-114">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="82374-114">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="82374-115">Diretrizes de uso</span><span class="sxs-lookup"><span data-stu-id="82374-115">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)
