---
title: Parâmetros de nomeação
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- parameters, names
- names [.NET Framework], parameters
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
ms.openlocfilehash: 0bb67056bb39b6a5f372191a1d0b0bb0dc1fe4d1
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709173"
---
# <a name="naming-parameters"></a>Parâmetros de nomeação
Além do motivo óbvio da legibilidade, é importante seguir as diretrizes para nomes de parâmetro, pois os parâmetros são exibidos na documentação e no designer quando as ferramentas de Design Visual fornecem funcionalidade de navegação de classe e IntelliSense.  
  
 **✓ DO** use camelCasing em nomes de parâmetro.  
  
 **✓ DO** usam nomes de parâmetro descritivo.  
  
 **✓ CONSIDER** usando nomes com base no significado do parâmetro em vez do tipo do parâmetro.  
  
### <a name="naming-operator-overload-parameters"></a>Parâmetros de sobrecarga de operador de nomenclatura  
 **✓ DO** usar `left` e `right` para nomes de parâmetro de sobrecarga de operador binário se não houver nenhum significado para os parâmetros.  
  
 **✓ DO** usar `value` para unário operador sobrecarregar os nomes de parâmetro se não houver nenhum significado para os parâmetros.  
  
 **✓ CONSIDER** nomes significativos para o operador de sobrecarga parâmetros se isso adiciona valor significativo.  
  
 **X DO NOT** use abreviações ou índices numéricos para o operador sobrecarregar os nomes de parâmetro.  
  
 *Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Veja também

- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
- [Diretrizes de nomenclatura](../../../docs/standard/design-guidelines/naming-guidelines.md)
