---
title: Nomenclatura de recursos
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- names [.NET Framework], localized resources
- localization, naming guidelines
- resource names
- global applications, naming guidelines
- international applications, naming guidelines
ms.assetid: 8b0e97f3-7877-44fd-bc76-e05d36d5d79c
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 0387d820cc660bdf6cbafb9d76bbf0184c111881
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="naming-resources"></a>Nomenclatura de recursos
Como recursos localizáveis podem ser referenciados por meio de determinados objetos, como se fossem propriedades, as diretrizes de nomeação para os recursos são semelhantes às diretrizes de propriedade.  
  
 **FAZER ✓** usar PascalCasing em chaves de recurso.  
  
 **FAZER ✓** fornecer descritivo em vez de identificadores curtos.  
  
 **X não** usar palavras-chave das linguagens CLR principais.  
  
 **FAZER ✓** use somente caracteres alfanuméricos e sublinhados em nomes de recursos.  
  
 **FAZER ✓** usam a seguinte convenção de nomenclatura para os recursos de mensagem de exceção.  
  
 O identificador de recurso deve ser o nome do tipo de exceção mais um identificador curto da exceção:  
  
 `ArgumentExceptionIllegalCharacters`  
 `ArgumentExceptionInvalidName`  
 `ArgumentExceptionFileNameIsMalformed`  
  
 *Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)  
 [Diretrizes de nomenclatura](../../../docs/standard/design-guidelines/naming-guidelines.md)
