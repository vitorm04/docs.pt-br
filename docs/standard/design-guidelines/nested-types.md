---
title: Tipos aninhados
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- types, nested
- public nested types
- type design guidelines, nested types
- nested types
- members [.NET Framework], type
- class library design guidelines [.NET Framework], nested types
ms.assetid: 12feb7f0-b793-4d96-b090-42d6473bab8c
caps.latest.revision: 9
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 681e11ef3994e4c38dee9f99c6c82cc4b103a0db
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="nested-types"></a>Tipos aninhados
Um tipo aninhado é um tipo definido dentro do escopo de outro tipo, que é chamado o tipo de delimitador. Um tipo aninhado tem acesso a todos os membros do seu tipo delimitador. Por exemplo, ele tem acesso a campos particulares definidos no tipo de delimitador e protegido campos definidos em todos os ascendentes do tipo delimitador.  
  
 Em geral, os tipos aninhados devem ser usados com moderação. Há vários motivos para isso. Alguns desenvolvedores não são totalmente familiarizados com o conceito. Esses desenvolvedores podem, por exemplo, ter problemas com a sintaxe de declaração de variáveis de tipos aninhados. Tipos aninhados são também muito acoplados com seus tipos de delimitadores e como tal, não são adequados para tipos de uso geral.  
  
 Tipos aninhados são mais adequados para modelar os detalhes de implementação dos seus tipos de delimitadores. O usuário final deve ter raramente para declarar variáveis de um tipo aninhado e quase nunca deve ter que instanciar explicitamente os tipos aninhados. Por exemplo, o enumerador de uma coleção pode ser um tipo aninhado de coleção. Enumeradores são instanciados geralmente por seu tipo delimitador e como muitos idiomas oferecem suporte a instrução foreach, variáveis de enumerador raramente têm de ser declarada pelo usuário final.  
  
 **FAZER ✓** usar tipos aninhados quando a relação entre o tipo aninhado e seu tipo externo é tal que a semântica de acessibilidade de membros é desejável.  
  
 **X não** tipos aninhados públicos em uso como um agrupamento lógico construir; use namespaces para isso.  
  
 **X Evite** exposto publicamente tipos aninhados. A única exceção a isso é se as variáveis do tipo aninhado precisam ser declarado apenas em cenários raros, como subclasses ou outros cenários de personalização avançada.  
  
 **X não** usar tipos aninhados, se o tipo é provavelmente serão mencionados fora do tipo recipiente.  
  
 Por exemplo, um enum passado para um método definido em uma classe não deve ser definido como um tipo aninhado na classe.  
  
 **X não** usar tipos aninhados se eles precisam ser instanciado pelo código do cliente.  Se um tipo tem um construtor público, ele provavelmente não deve ser aninhado.  
  
 Se um tipo pode ser instanciado, parece que indicam o tipo tem um lugar no framework em seu próprio (você pode criá-lo, trabalhar com ele e destruí-lo sem nunca usando o tipo externo) e, portanto, não devem ser aninhados. Tipos internos não devem ser reutilizados amplamente fora do tipo externo sem qualquer relação qualquer que seja o tipo externo.  
  
 **X não** definir um tipo aninhado como um membro de uma interface. Muitos idiomas não dão suporte a esse uma construção.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de Design de tipo](../../../docs/standard/design-guidelines/type.md)  
 [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
