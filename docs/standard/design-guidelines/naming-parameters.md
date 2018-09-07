---
title: Parâmetros de nomeação
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- parameters, names
- names [.NET Framework], parameters
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8e6a8a1dcdcb8fa3311b040c72987f0f76e681fc
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44086466"
---
# <a name="naming-parameters"></a>Parâmetros de nomeação
Além do motivo óbvio de legibilidade, é importante seguir as diretrizes para nomes de parâmetro porque os parâmetros são exibidos na documentação e no designer quando ferramentas de design visual fornecem Intellisense e a funcionalidade de navegação de classe.  
  
 **✓ DO** use camelCasing em nomes de parâmetro.  
  
 **✓ DO** usam nomes de parâmetro descritivo.  
  
 **✓ CONSIDER** usando nomes com base no significado do parâmetro em vez do tipo do parâmetro.  
  
### <a name="naming-operator-overload-parameters"></a>Parâmetros de sobrecarga de operador de nomenclatura  
 **✓ DO** usar `left` e `right` para nomes de parâmetro de sobrecarga de operador binário se não houver nenhum significado para os parâmetros.  
  
 **✓ DO** usar `value` para unário operador sobrecarregar os nomes de parâmetro se não houver nenhum significado para os parâmetros.  
  
 **✓ CONSIDER** nomes significativos para o operador de sobrecarga parâmetros se isso adiciona valor significativo.  
  
 **X DO NOT** use abreviações ou índices numéricos para o operador sobrecarregar os nomes de parâmetro.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também

- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)  
- [Diretrizes de nomenclatura](../../../docs/standard/design-guidelines/naming-guidelines.md)
