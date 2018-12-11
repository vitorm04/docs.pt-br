---
title: Design de propriedade
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines, properties
- properties [.NET Framework], design guidelines
ms.assetid: 127cbc0c-cbed-48fd-9c89-7c5d4f98f163
author: KrzysztofCwalina
ms.openlocfilehash: 1d119b48f0524b3e997aa2cb9ea2cbbd855afdf0
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53131450"
---
# <a name="property-design"></a>Design de propriedade
Embora as propriedades são tecnicamente muito semelhantes aos métodos, eles são bastante diferentes em termos de seus cenários de uso. Eles devem ser vistos como campos inteligentes. Eles têm a sintaxe de chamada de campos e a flexibilidade dos métodos.  
  
 **✓ DO** criar propriedades somente obtenção se o chamador não deve ser capaz de alterar o valor da propriedade.  
  
 Tenha em mente que, se o tipo de propriedade é um tipo de referência mutável, o valor da propriedade pode ser alterado, mesmo que a propriedade é somente obtenção.  
  
 **X DO NOT** fornecer somente conjunto de propriedades ou propriedades setter ter acessibilidade mais ampla que o getter.  
  
 Por exemplo, não use propriedades com um setter público e um getter protegido.  
  
 Se o getter de propriedade não pode ser fornecido, implemente a funcionalidade como um método em vez disso. Considere começar com o nome do método `Set` e execute com o que você seria ter chamado a propriedade. Por exemplo, <xref:System.AppDomain> tem um método chamado `SetCachePath` em vez de ter uma propriedade somente conjunto chamada `CachePath`.  
  
 **✓ DO** fornecem valores padrão adequado para todas as propriedades, garantindo que os padrões não resultam em uma falha de segurança ou um código extremamente ineficiente.  
  
 **✓ DO** permitem que propriedades sejam definidas em qualquer ordem, mesmo que isso resulte em um estado inválido temporário do objeto.  
  
 É comum para duas ou mais propriedades para ser inter-relacionados para um ponto em que alguns valores de uma propriedade podem ser inválidos considerando os valores de outras propriedades no mesmo objeto. Nesses casos, as exceções que resultam do estado inválido devem ser adiadas até que as propriedades inter-relacionados, na verdade, são usadas em conjunto pelo objeto.  
  
 **✓ DO** preservar o valor anterior, se um setter de propriedade gera uma exceção.  
  
 **X AVOID** Lançando exceções getters de propriedade.  
  
 Getters de propriedade devem ser operações simples e não devem ter qualquer pré-condições. Se um getter pode lançar uma exceção, ele provavelmente deveria ser reprojetado para ser um método. Observe que essa regra não se aplica a indexadores, em que esperamos exceções como resultado de validação de argumentos.  
  
### <a name="indexed-property-design"></a>Design de propriedade indexada  
 Uma propriedade indexada é uma propriedade especial que pode ter parâmetros e pode ser chamada com a sintaxe especial semelhante a indexação de matriz.  
  
 Propriedades indexadas são normalmente chamadas de indexadores. Indexadores devem ser usados apenas em APIs que fornecem acesso a itens em uma coleção lógica. Por exemplo, uma cadeia de caracteres é uma coleção de caracteres e o indexador em <xref:System.String?displayProperty=nameWithType> foi adicionado para acessar seus caracteres.  
  
 **✓ CONSIDER** usando indexadores para fornecer acesso aos dados armazenados em uma matriz interna.  
  
 **✓ CONSIDER** fornecendo indexadores em tipos que representam coleções de itens.  
  
 **X AVOID** usando propriedades com mais de um parâmetro indexadas.  
  
 Se o projeto requer vários parâmetros, reconsidere se a propriedade realmente representa um acessador para uma coleção lógica. Se não existir, use métodos. Considere começar com o nome do método `Get` ou `Set`.  
  
 **X AVOID** indexadores com tipos de parâmetro diferente de <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Int64?displayProperty=nameWithType>, <xref:System.String?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, ou um enum.  
  
 Se o projeto requer outros tipos de parâmetros, reavalie fortemente se a API realmente representa um acessador para uma coleção lógica. Se não existir, use um método. Considere começar com o nome do método `Get` ou `Set`.  
  
 **✓ DO** usar o nome `Item` para propriedades indexadas, a menos que haja um nome obviamente melhor (por exemplo, consulte o <xref:System.String.Chars%2A> propriedade em `System.String`).  
  
 No c#, os indexadores são por padrão, chamado Item. O <xref:System.Runtime.CompilerServices.IndexerNameAttribute> podem ser usados para personalizar esse nome.  
  
 **X DO NOT** fornecem um indexador e métodos que são semanticamente equivalentes.  
  
 **X DO NOT** fornecer mais de uma família de indexadores de sobrecarga em um tipo.  
  
 Isso é imposto pelo compilador c#.  
  
 **X DO NOT** propriedades indexadas de não-padrão de uso.  
  
 Isso é imposto pelo compilador c#.  
  
### <a name="property-change-notification-events"></a>Eventos de notificação de alteração de propriedade  
 Às vezes é útil para fornecer um evento notificando o usuário de alterações em um valor da propriedade. Por exemplo, `System.Windows.Forms.Control` gera uma `TextChanged` evento após o valor do seu `Text` propriedade foi alterada.  
  
 **✓ CONSIDER** gerando eventos de notificação quando valores de propriedade em APIs de alto nível (geralmente designer componentes) são modificados de alteração.  
  
 Se houver um bom cenário para um usuário saiba quando uma propriedade de um objeto está sendo alterado, o objeto deverá acionar um evento de notificação de alteração para a propriedade.  
  
 No entanto, é pouco provável que valha a pena a sobrecarga para acionar esses eventos para as APIs de baixo nível, como tipos de base ou coleções. Por exemplo, <xref:System.Collections.Generic.List%601> não geraria desses eventos quando um novo item é adicionado à lista e o `Count` as alterações de propriedade.  
  
 **✓ CONSIDER** gerando eventos de notificação quando o valor de uma propriedade é alterada por meio de forças externas de alteração.  
  
 Se um valor da propriedade for alterado por meio de alguns force externo (de forma diferente de chamando métodos no objeto), gere eventos indicam para o desenvolvedor que o valor está mudando e foi alterado. Um bom exemplo é o `Text` propriedade de um controle de caixa de texto. Quando o usuário digita texto em um `TextBox`, o valor da propriedade é alterado automaticamente.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpresso com permissão da Pearson Education, Inc. de [as diretrizes de Design do Framework: As convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008 pela Addison-Wesley Professional, como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também

- [Diretrizes de design de membro](../../../docs/standard/design-guidelines/member.md)  
- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
