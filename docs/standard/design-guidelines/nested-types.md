---
title: Tipos aninhados
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- types, nested
- public nested types
- type design guidelines, nested types
- nested types
- members [.NET Framework], type
- class library design guidelines [.NET Framework], nested types
ms.assetid: 12feb7f0-b793-4d96-b090-42d6473bab8c
ms.openlocfilehash: dd13116b13ac8e2d7a3af6ef014eb4f393909515
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743703"
---
# <a name="nested-types"></a>Tipos aninhados
Um tipo aninhado é um tipo definido dentro do escopo de outro tipo, que é chamado de tipo de delimitador. Um tipo aninhado tem acesso a todos os membros de seu tipo delimitador. Por exemplo, ele tem acesso a campos privados definidos no tipo delimitador e a campos protegidos definidos em todos os ascendentes do tipo delimitador.

 Em geral, os tipos aninhados devem ser usados com moderação. Há várias razões para isso. Alguns desenvolvedores não estão totalmente familiarizados com o conceito. Esses desenvolvedores podem, por exemplo, ter problemas com a sintaxe de declaração de variáveis de tipos aninhados. Os tipos aninhados também são rigidamente acoplados aos tipos delimitadores e, como tal, não são adequados para tipos de finalidade geral.

 Os tipos aninhados são mais adequados para modelar detalhes de implementação de seus tipos delimitadores. O usuário final raramente deve ter que declarar variáveis de um tipo aninhado e quase nunca deve ter que instanciar tipos aninhados explicitamente. Por exemplo, o enumerador de uma coleção pode ser um tipo aninhado dessa coleção. Enumeradores geralmente são instanciados por seu tipo delimitador e, como muitas linguagens dão suporte à instrução foreach, as variáveis do enumerador raramente precisam ser declaradas pelo usuário final.

 ✔️ usam tipos aninhados quando a relação entre o tipo aninhado e seu tipo externo é tal que a semântica de acessibilidade de membro é desejável.

 ❌ não usam tipos aninhados públicos como uma construção de agrupamento lógico; Use namespaces para isso.

 ❌ evitar tipos aninhados publicamente expostos. A única exceção a isso é se as variáveis do tipo aninhado precisam ser declaradas apenas em cenários raros, como subclasse ou outros cenários de personalização avançada.

 ❌ não usar tipos aninhados se for provável que o tipo seja referenciado fora do tipo recipiente.

 Por exemplo, uma enumeração passada para um método definido em uma classe não deve ser definida como um tipo aninhado na classe.

 ❌ não use tipos aninhados se eles precisarem ser instanciados pelo código do cliente.  Se um tipo tiver um construtor público, ele provavelmente não deve ser aninhado.

 Se um tipo puder ser instanciado, isso parecerá indicar que o tipo tem um local na estrutura por si só (você pode criá-lo, trabalhar com ele e destruí-lo sem nunca usar o tipo externo) e, portanto, não deve ser aninhado. Os tipos internos não devem ser amplamente reutilizados fora do tipo externo sem nenhuma relação com o tipo externo.

 ❌ não definem um tipo aninhado como membro de uma interface. Muitas linguagens não oferecem suporte a tal construção.

 *Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*

 *Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*

## <a name="see-also"></a>Veja também

- [Diretrizes de Design de tipo](../../../docs/standard/design-guidelines/type.md)
- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
