---
title: Estrutura de Design
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- deallocating structures
- allocating structures
- value types, structures
- structure design
- type design guidelines, structures
- structures [.NET Framework], design guidelines
ms.assetid: 1f48b2d8-608c-4be6-9ba4-d8f203ed9f9f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2621aa96cf89b453d5faec3357d0890ca36251d4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572730"
---
# <a name="struct-design"></a>Estrutura de Design
O tipo de valor de uso geral é mais conhecido como uma estrutura, sua palavra-chave c#. Esta seção fornece diretrizes para o design da estrutura geral.  
  
 **X DO NOT** fornecer um construtor padrão para um struct.  
  
 Seguir essa diretriz permite matrizes de estruturas a ser criado sem a necessidade de executar o construtor em cada item da matriz. Observe que c# não permite estruturas ter construtores padrão.  
  
 **X DO NOT** definir tipos de valor mutável.  
  
 Tipos de valor mutável tem vários problemas. Por exemplo, quando uma propriedade getter retorna um tipo de valor, o chamador recebe uma cópia. Como a cópia é criada implicitamente, os desenvolvedores podem não estar cientes de que eles são mutação a cópia e não o valor original. Além disso, alguns idiomas (linguagens dinâmicas, em particular) tem problemas para usar tipos de valor mutável porque mesmo variáveis locais, quando cancelada, fazer com que uma cópia a serem feitas.  
  
 **✓ DO** Certifique-se de que um estado em que todos os dados da instância é definido como zero, false ou null (conforme apropriado) é válido.  
  
 Isso impede que acidental criação de instâncias inválidas quando uma matriz de estruturas de é criada.  
  
 **✓ DO** implementar <xref:System.IEquatable%601> em tipos de valor.  
  
 O <xref:System.Object.Equals%2A?displayProperty=nameWithType> método em tipos de valor faz com que a conversão boxing e sua implementação padrão não é muito eficiente, pois ela usa reflexão. <xref:System.IEquatable%601.Equals%2A> pode ter um desempenho muito melhor e pode ser implementado para que ele não fará com que a conversão boxing.  
  
 **X DO NOT** estender explicitamente <xref:System.ValueType>. Na verdade, a maioria das linguagens evitar isso.  
  
 Em geral, structs pode ser muito útil, mas só deve ser usadas para valores pequenos, único, imutáveis que não serão demarcados com frequência.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de Design de tipo](../../../docs/standard/design-guidelines/type.md)  
 [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)  
 [Escolhendo entre a classe e Struct](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)
