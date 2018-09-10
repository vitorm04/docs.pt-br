---
title: Matrizes
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], arrays
- arrays [.NET Framework], usage guidelines
- empty arrays
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1ac7e28c3172f2ed68d402e1d04a1664644c7f25
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44207363"
---
# <a name="arrays"></a>Matrizes
**✓ DO** preferir usar coleções em matrizes em APIs públicas. O [coleções](../../../docs/standard/design-guidelines/guidelines-for-collections.md) seção fornece detalhes sobre como escolher entre coleções e matrizes.  
  
 **X DO NOT** usar campos de matriz de somente leitura. O campo em si é somente leitura e não pode ser alterado, mas os elementos na matriz podem ser alterados.  
  
 **✓ CONSIDER** usando matrizes denteadas em vez de matrizes multidimensionais.  
  
 Uma matriz denteada é uma matriz com elementos que também são matrizes. As matrizes que constituem os elementos podem ter tamanhos diferentes, resultando em menos espaço desperdiçado para alguns conjuntos de dados (por exemplo, matriz esparsa) em comparação comparado matrizes multidimensionais. Além disso, o CLR otimiza as operações de índice em matrizes denteadas, portanto, eles podem apresentar melhor desempenho de tempo de execução em alguns cenários.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Array>  
- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)  
- [Diretrizes de uso](../../../docs/standard/design-guidelines/usage-guidelines.md)
