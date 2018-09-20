---
title: Operadores de igualdade
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], Equals method
- class library design guidelines [.NET Framework], equality operator
- equality operator (==) [.NET Framework]
- Equals method
- == operator (equality) [.NET Framework]
ms.assetid: bc496a91-fefb-4ce0-ab4c-61f09964119a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 27550a8fd8292029cad9c2e699374a190b1a532e
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46287016"
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
  
 *Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também

- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)  
- [Diretrizes de uso](../../../docs/standard/design-guidelines/usage-guidelines.md)
