---
title: Operadores de igualdade
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], Equals method
- class library design guidelines [.NET Framework], equality operator
- equality operator (==) [.NET Framework]
- Equals method
- == operator (equality) [.NET Framework]
ms.assetid: bc496a91-fefb-4ce0-ab4c-61f09964119a
author: KrzysztofCwalina
ms.openlocfilehash: ef1a0aff1ac59434d9d9a6f0371bf236f637050e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61960324"
---
# <a name="equality-operators"></a>Operadores de igualdade
Esta seção discute a sobrecarga de operadores de igualdade e refere-se ao `operator==` e `operator!=` como operadores de igualdade.  
  
 **X DO NOT** sobrecarregar os operadores de igualdade e não o outro.  
  
 **✓ DO** Certifique-se de que <xref:System.Object.Equals%2A?displayProperty=nameWithType> e os operadores de igualdade têm exatamente a mesma semântica e as características de desempenho semelhante.  
  
 Isso significa que muitas vezes `Object.Equals` precisa ser substituído quando os operadores de igualdade são sobrecarregados.  
  
 **X AVOID** Lançando exceções de operadores de igualdade.  
  
 Por exemplo, retornar false se um dos argumentos for nulo em vez de gerar `NullReferenceException`.  
  
## <a name="equality-operators-on-value-types"></a>Operadores de igualdade em tipos de valor  
 **✓ DO** sobrecarregar os operadores de igualdade em tipos de valor, se a igualdade é significativa.  
  
 Na maioria das linguagens de programação, não há nenhuma implementação padrão de `operator==` para tipos de valor.  
  
## <a name="equality-operators-on-reference-types"></a>Operadores de igualdade em tipos de referência  
 **X AVOID** sobrecarregar os operadores de igualdade em tipos de referência mutável.  
  
 Muitos idiomas têm operadores de igualdade interna para tipos de referência. Os operadores internos geralmente implementam a igualdade de referência, e muitos desenvolvedores estão surpresos quando o comportamento padrão é alterado para a igualdade de valor.  
  
 Esse problema é reduzido para tipos de referência imutável porque imutabilidade torna muito difícil observar a diferença entre a igualdade de referência e de igualdade de valor.  
  
 **X AVOID** sobrecarregar os operadores de igualdade em tipos de referência, se a implementação seria significativamente mais lenta do que o de igualdade de referência.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpresso com permissão da Pearson Education, Inc. de [as diretrizes de Design do Framework: As convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008 pela Addison-Wesley Professional, como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também

- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
- [Diretrizes de uso](../../../docs/standard/design-guidelines/usage-guidelines.md)
