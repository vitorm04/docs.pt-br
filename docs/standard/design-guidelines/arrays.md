---
title: Matrizes
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- class library design guidelines [.NET Framework], arrays
- arrays [.NET Framework], usage guidelines
- empty arrays
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
caps.latest.revision: 18
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 54f5d68a343f473c67484e9e806551eb115bac36
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="arrays"></a><span data-ttu-id="391ca-102">Matrizes</span><span class="sxs-lookup"><span data-stu-id="391ca-102">Arrays</span></span>
<span data-ttu-id="391ca-103">**FAZER ✓** preferir usar coleções em matrizes em APIs públicas.</span><span class="sxs-lookup"><span data-stu-id="391ca-103">**✓ DO** prefer using collections over arrays in public APIs.</span></span> <span data-ttu-id="391ca-104">O [coleções](../../../docs/standard/design-guidelines/guidelines-for-collections.md) seção fornece detalhes sobre como escolher entre coleções e matrizes.</span><span class="sxs-lookup"><span data-stu-id="391ca-104">The [Collections](../../../docs/standard/design-guidelines/guidelines-for-collections.md) section provides details about how to choose between collections and arrays.</span></span>  
  
 <span data-ttu-id="391ca-105">**X não** usar campos de matriz de somente leitura.</span><span class="sxs-lookup"><span data-stu-id="391ca-105">**X DO NOT** use read-only array fields.</span></span> <span data-ttu-id="391ca-106">O próprio campo é somente leitura e não pode ser alterado, mas os elementos da matriz podem ser alterados.</span><span class="sxs-lookup"><span data-stu-id="391ca-106">The field itself is read-only and can't be changed, but elements in the array can be changed.</span></span>  
  
 <span data-ttu-id="391ca-107">**✓ CONSIDERE** usando matrizes denteadas em vez de matrizes multidimensionais.</span><span class="sxs-lookup"><span data-stu-id="391ca-107">**✓ CONSIDER** using jagged arrays instead of multidimensional arrays.</span></span>  
  
 <span data-ttu-id="391ca-108">Uma matriz denteada é uma matriz com elementos também são matrizes.</span><span class="sxs-lookup"><span data-stu-id="391ca-108">A jagged array is an array with elements that are also arrays.</span></span> <span data-ttu-id="391ca-109">As matrizes que compõem os elementos podem ser de tamanhos diferentes, resultando em menos perda de espaço para alguns conjuntos de dados (por exemplo, matriz esparsa) em comparação comparada matrizes multidimensionais.</span><span class="sxs-lookup"><span data-stu-id="391ca-109">The arrays that make up the elements can be of different sizes, leading to less wasted space for some sets of data (e.g., sparse matrix) compared to multidimensional arrays.</span></span> <span data-ttu-id="391ca-110">Além disso, o CLR otimiza as operações de índice em matrizes denteadas, para que eles podem apresentar melhor desempenho de tempo de execução em alguns cenários.</span><span class="sxs-lookup"><span data-stu-id="391ca-110">Furthermore, the CLR optimizes index operations on jagged arrays, so they might exhibit better runtime performance in some scenarios.</span></span>  
  
 <span data-ttu-id="391ca-111">*Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="391ca-111">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="391ca-112">*Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="391ca-112">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="391ca-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="391ca-113">See Also</span></span>  
 <xref:System.Array>  
 [<span data-ttu-id="391ca-114">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="391ca-114">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="391ca-115">Diretrizes de uso</span><span class="sxs-lookup"><span data-stu-id="391ca-115">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)
