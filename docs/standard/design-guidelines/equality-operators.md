---
title: Operadores de igualdade
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- class library design guidelines [.NET Framework], Equals method
- class library design guidelines [.NET Framework], equality operator
- equality operator (==) [.NET Framework]
- Equals method
- == operator (equality) [.NET Framework]
ms.assetid: bc496a91-fefb-4ce0-ab4c-61f09964119a
caps.latest.revision: 13
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: cd740e9b7a5d38229b3564bfeca003fc4d189624
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="equality-operators"></a>Operadores de igualdade
Esta seção discute a sobrecarga de operadores de igualdade e refere-se ao `operator==` e `operator!=` como operadores de igualdade.  
  
 **X não** sobrecarregar os operadores de igualdade e não o outro.  
  
 **FAZER ✓** Certifique-se de que <xref:System.Object.Equals%2A?displayProperty=nameWithType> e os operadores de igualdade têm exatamente a mesma semântica e as características de desempenho semelhante.  
  
 Isso geralmente significa que `Object.Equals` precisa ser substituído quando os operadores de igualdade estão sobrecarregados.  
  
 **X Evite** Lançando exceções de operadores de igualdade.  
  
 Por exemplo, retornará false se um dos argumentos for nulo, em vez de gerar `NullReferenceException`.  
  
## <a name="equality-operators-on-value-types"></a>Operadores de igualdade em tipos de valor  
 **FAZER ✓** sobrecarregar os operadores de igualdade em tipos de valor, se a igualdade é significativa.  
  
 Na maioria das linguagens de programação, não há nenhuma implementação padrão de `operator==` para tipos de valor.  
  
## <a name="equality-operators-on-reference-types"></a>Operadores de igualdade em tipos de referência  
 **X Evite** sobrecarregar os operadores de igualdade em tipos de referência mutável.  
  
 Muitos idiomas tem operadores de igualdade internos para tipos de referência. Os operadores internos geralmente implementam a igualdade de referência e muitos desenvolvedores estão surpresos quando o comportamento padrão é alterado para a igualdade de valor.  
  
 Esse problema é reduzido para tipos de referência imutável porque imutabilidade torna muito mais difícil observar a diferença entre a igualdade de referência e de igualdade de valor.  
  
 **X Evite** sobrecarregar os operadores de igualdade em tipos de referência, se a implementação seria significativamente mais lenta do que o de igualdade de referência.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)  
 [Diretrizes de uso](../../../docs/standard/design-guidelines/usage-guidelines.md)
