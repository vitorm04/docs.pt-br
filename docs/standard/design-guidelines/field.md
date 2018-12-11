---
title: Design de campo
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- fields, design guidelines
- read-only fields
- member design guidelines, fields
ms.assetid: 7cb4b0f3-7a10-4c93-b84d-733f7134fcf8
author: KrzysztofCwalina
ms.openlocfilehash: 34c5a163e545b78c188f37b2819962b4c7c56f80
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53144345"
---
# <a name="field-design"></a>Design de campo
O princípio de encapsulamento é uma das noções mais importantes no design orientado a objeto. Esse princípio declara que os dados armazenados dentro de um objeto devem ser acessíveis somente a esse objeto.  
  
 Uma maneira útil de interpretar o princípio é dizer que um tipo deve ser projetado para que as alterações para os campos desse tipo (alterações de nome ou tipo) podem ser feitas sem quebra de código diferente para os membros do tipo. Essa interpretação imediatamente implica que todos os campos devem ser privados.  
  
 Podemos excluir campos estáticos e constante de somente leitura dessa restrição estrito, porque esses campos, quase por definição, nunca deve alterar.  
  
 **X DO NOT** fornecem campos de instância público ou protegido.  
  
 Você deve fornecer as propriedades para acessar os campos em vez de torná-los públicos ou protegidos.  
  
 **✓ DO** usar campos de constantes para constantes que nunca serão alterado.  
  
 O compilador irá consumir os valores dos campos constantes diretamente no código de chamada. Portanto, os valores constantes nunca podem ser alterados sem o risco de perder a compatibilidade.  
  
 **✓ DO** usar estático público `readonly` campos para instâncias de objeto predefinido.  
  
 Se houver instâncias predefinidas do tipo, declará-los como somente leitura campos estáticos públicos do tipo em si.  
  
 **X DO NOT** atribuir instâncias dos tipos mutáveis para `readonly` campos.  
  
 Um tipo mutável é um tipo com instâncias que podem ser modificados depois que eles são instanciados. Por exemplo, fluxos, a maioria das coleções e matrizes são tipos mutáveis, mas <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>, e <xref:System.String?displayProperty=nameWithType> são todos imutáveis. O modificador somente leitura em um campo de tipo de referência impede que a instância armazenada no campo que está sendo substituído, mas não impede que dados da instância do campo que está sendo modificada chamando membros alterando a instância.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpresso com permissão da Pearson Education, Inc. de [as diretrizes de Design do Framework: As convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008 pela Addison-Wesley Professional, como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também

- [Diretrizes de design de membro](../../../docs/standard/design-guidelines/member.md)  
- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
