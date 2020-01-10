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
ms.openlocfilehash: 31a5ce18f4526b5e3b8411365dff812601de87ad
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709433"
---
# <a name="equality-operators"></a>Operadores de igualdade
Esta seção discute como sobrecarregar operadores de igualdade e refere-se a `operator==` e `operator!=` como operadores de igualdade.  
  
 **X DO NOT** sobrecarregar os operadores de igualdade e não o outro.  
  
 **✓ DO** Certifique-se de que <xref:System.Object.Equals%2A?displayProperty=nameWithType> e os operadores de igualdade têm exatamente a mesma semântica e as características de desempenho semelhante.  
  
 Isso geralmente significa que `Object.Equals` precisa ser substituído quando os operadores de igualdade estão sobrecarregados.  
  
 **X AVOID** Lançando exceções de operadores de igualdade.  
  
 Por exemplo, retorne FALSE se um dos argumentos for nulo em vez de lançar `NullReferenceException`.  
  
## <a name="equality-operators-on-value-types"></a>Operadores de igualdade em tipos de valor  
 **✓ DO** sobrecarregar os operadores de igualdade em tipos de valor, se a igualdade é significativa.  
  
 Na maioria das linguagens de programação, não há implementação padrão de `operator==` para tipos de valor.  
  
## <a name="equality-operators-on-reference-types"></a>Operadores de igualdade em tipos de referência  
 **X AVOID** sobrecarregar os operadores de igualdade em tipos de referência mutável.  
  
 Muitas linguagens têm operadores de igualdade internos para tipos de referência. Os operadores internos geralmente implementam a igualdade de referência e muitos desenvolvedores ficam surpresos quando o comportamento padrão é alterado para a igualdade do valor.  
  
 Esse problema é mitigado para tipos de referência imutáveis porque a imutabilidade torna muito mais difícil observar a diferença entre igualdade de referência e igualdade de valor.  
  
 **X AVOID** sobrecarregar os operadores de igualdade em tipos de referência, se a implementação seria significativamente mais lenta do que o de igualdade de referência.  
  
 *Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Veja também

- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
- [Diretrizes de uso](../../../docs/standard/design-guidelines/usage-guidelines.md)
