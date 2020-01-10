---
title: Recursos de nomenclatura
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], localized resources
- localization, naming guidelines
- resource names
- global applications, naming guidelines
- international applications, naming guidelines
ms.assetid: 8b0e97f3-7877-44fd-bc76-e05d36d5d79c
ms.openlocfilehash: b64a3ef6e12f8ea1abf7efd9c22f2f4333dda5c8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709160"
---
# <a name="naming-resources"></a>Recursos de nomenclatura
Como os recursos localizáveis podem ser referenciados por meio de determinados objetos como se fossem Propriedades, as diretrizes de nomenclatura para recursos são semelhantes às diretrizes de propriedade.  
  
 **✓ DO** usar PascalCasing em chaves de recurso.  
  
 **✓ DO** fornecer descritivo em vez de identificadores curtos.  
  
 **X DO NOT** usar palavras-chave das linguagens CLR principais.  
  
 **✓ DO** use somente caracteres alfanuméricos e sublinhados em nomes de recursos.  
  
 **✓ DO** usam a seguinte convenção de nomenclatura para os recursos de mensagem de exceção.  
  
 O identificador de recurso deve ser o nome do tipo de exceção, além de um identificador curto da exceção:  
  
 `ArgumentExceptionIllegalCharacters`  
 `ArgumentExceptionInvalidName`  
 `ArgumentExceptionFileNameIsMalformed`  
  
 *Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Veja também

- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
- [Diretrizes de nomenclatura](../../../docs/standard/design-guidelines/naming-guidelines.md)
