---
title: Design de Struct
ms.date: 10/22/2008
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
ms.openlocfilehash: 8841a30f1dd0420b2ea45740b1e33bde5199c3f9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709043"
---
# <a name="struct-design"></a>Design de Struct
O tipo de valor de uso geral é geralmente referido como struct, sua C# palavra-chave. Esta seção fornece diretrizes para o design geral de struct.  
  
 **X** não forneça um construtor sem parâmetros para uma struct.  
  
 Seguir essa diretriz permite que matrizes de structs sejam criadas sem a necessidade de executar o Construtor em cada item da matriz. Observe que C# o não permite que structs tenham construtores sem parâmetros.  
  
 **X DO NOT** definir tipos de valor mutável.  
  
 Os tipos de valores mutáveis têm vários problemas. Por exemplo, quando um getter de propriedade retorna um tipo de valor, o chamador recebe uma cópia. Como a cópia é criada implicitamente, os desenvolvedores podem não estar cientes de que estão modificando a cópia e não o valor original. Além disso, algumas linguagens (linguagens dinâmicas, em particular) têm problemas ao usar tipos de valor mutável porque até mesmo variáveis locais, quando desreferenciadas, fazem com que uma cópia seja feita.  
  
 **✓ DO** Certifique-se de que um estado em que todos os dados da instância é definido como zero, false ou null (conforme apropriado) é válido.  
  
 Isso impede a criação acidental de instâncias inválidas quando uma matriz de structs é criada.  
  
 **✓ DO** implementar <xref:System.IEquatable%601> em tipos de valor.  
  
 O método <xref:System.Object.Equals%2A?displayProperty=nameWithType> em tipos de valor causa boxing, e sua implementação padrão não é muito eficiente, pois ela usa reflexão. <xref:System.IEquatable%601.Equals%2A> pode ter um desempenho muito melhor e pode ser implementado para que não cause boxing.  
  
 **X DO NOT** estender explicitamente <xref:System.ValueType>. Na verdade, a maioria dos idiomas impede isso.  
  
 Em geral, as estruturas podem ser muito úteis, mas devem ser usadas somente para valores pequenos, únicos e imutáveis que não serão emoldurados com frequência.  
  
 *Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Veja também

- [Diretrizes de Design de tipo](../../../docs/standard/design-guidelines/type.md)
- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
- [Escolhendo entre a classe e Struct](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)
