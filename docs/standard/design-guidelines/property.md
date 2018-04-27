---
title: Design de propriedade
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- member design guidelines, properties
- properties [.NET Framework], design guidelines
ms.assetid: 127cbc0c-cbed-48fd-9c89-7c5d4f98f163
caps.latest.revision: 12
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6dcb164daea6809f0d0e9c221f182d5019385bc1
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="property-design"></a>Design de propriedade
Embora tecnicamente muito semelhantes aos métodos de propriedades, eles são muito diferentes em termos de seus cenários de uso. Eles devem ser considerados como campos inteligentes. Eles têm a sintaxe de chamada de campos e a flexibilidade de métodos.  
  
 **FAZER ✓** criar propriedades somente obtenção se o chamador não deve ser capaz de alterar o valor da propriedade.  
  
 Tenha em mente que, se o tipo de propriedade é um tipo de referência mutável, o valor da propriedade pode ser alterado, mesmo se a propriedade é somente obtenção.  
  
 **X não** fornecer somente conjunto de propriedades ou propriedades setter ter acessibilidade mais ampla que o getter.  
  
 Por exemplo, não use propriedades com um setter público e um getter protegido.  
  
 Se a propriedade getter não pode ser fornecido, implemente a funcionalidade como um método em vez disso. Comece com o nome do método `Set` e acompanhe o que poderia ter chamado a propriedade. Por exemplo, <xref:System.AppDomain> tem um método chamado `SetCachePath` em vez de ter uma propriedade somente conjunto chamada `CachePath`.  
  
 **FAZER ✓** fornecem valores padrão adequado para todas as propriedades, garantindo que os padrões não resultam em uma falha de segurança ou um código extremamente ineficiente.  
  
 **FAZER ✓** permitem que propriedades sejam definidas em qualquer ordem, mesmo que isso resulte em um estado inválido temporário do objeto.  
  
 É comum para duas ou mais propriedades para ser relacionados a um ponto em que alguns valores de uma propriedade podem ser inválidos dados os valores de outras propriedades no mesmo objeto. Nesses casos, exceções resultantes do estado inválido devem ser adiadas até que as propriedades inter-relacionados, na verdade, são usadas juntos pelo objeto.  
  
 **FAZER ✓** preservar o valor anterior, se um setter de propriedade gera uma exceção.  
  
 **X Evite** Lançando exceções getters de propriedade.  
  
 Getters de propriedade devem ser operações simples e não devem ter qualquer pré-condições. Se um getter pode lançar uma exceção, ela provavelmente deveria ser reprojetada para ser um método. Observe que essa regra não se aplica a indexadores, onde esperamos exceções como resultado de validação de argumentos.  
  
### <a name="indexed-property-design"></a>Propriedade indexada Design  
 Uma propriedade indexada é uma propriedade especial que pode ter parâmetros e pode ser chamada com a sintaxe especial semelhante a indexação de array.  
  
 Propriedades indexadas são conhecidas como indexadores. Indexadores devem ser usados somente nas APIs que fornecem acesso a itens em uma coleção lógica. Por exemplo, uma cadeia de caracteres é um conjunto de caracteres e o indexador em <xref:System.String?displayProperty=nameWithType> foi adicionado para acessar seus caracteres.  
  
 **✓ CONSIDERE** usando indexadores para fornecer acesso aos dados armazenados em uma matriz interna.  
  
 **✓ CONSIDERE** fornecendo indexadores em tipos que representam coleções de itens.  
  
 **X Evite** usando propriedades com mais de um parâmetro indexadas.  
  
 Se o projeto requer vários parâmetros, reconsidere se a propriedade realmente representa um acessador para uma coleção lógica. Se não estiver, use métodos. Comece com o nome do método `Get` ou `Set`.  
  
 **X Evite** indexadores com tipos de parâmetro diferente de <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Int64?displayProperty=nameWithType>, <xref:System.String?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, ou um enum.  
  
 Se o projeto requer outros tipos de parâmetros, altamente reavalie se a API realmente representa um acessador para uma coleção lógica. Se não estiver, use um método. Comece com o nome do método `Get` ou `Set`.  
  
 **FAZER ✓** usar o nome `Item` para propriedades indexadas, a menos que haja um nome obviamente melhor (por exemplo, consulte o <xref:System.String.Chars%2A> propriedade em `System.String`).  
  
 No c#, indexadores são, por padrão, um Item nomeado. O <xref:System.Runtime.CompilerServices.IndexerNameAttribute> pode ser usado para personalizar esse nome.  
  
 **X não** fornecem um indexador e métodos que são semanticamente equivalentes.  
  
 **X não** fornecer mais de uma família de indexadores de sobrecarga em um tipo.  
  
 Isso é imposto pelo compilador c#.  
  
 **X não** propriedades indexadas de não-padrão de uso.  
  
 Isso é imposto pelo compilador c#.  
  
### <a name="property-change-notification-events"></a>Eventos de notificação de alteração de propriedade  
 Às vezes é útil fornecer um evento que notifica o usuário sobre as alterações em um valor de propriedade. Por exemplo, `System.Windows.Forms.Control` gera um `TextChanged` evento após o valor do seu `Text` propriedade foi alterada.  
  
 **✓ CONSIDERE** gerando eventos de notificação quando valores de propriedade em APIs de alto nível (geralmente designer componentes) são modificados de alteração.  
  
 Se houver um cenário válido para um usuário a saber quando uma propriedade de um objeto está sendo alterado, o objeto deve gerar um evento de notificação de alteração para a propriedade.  
  
 No entanto, é improvável que vale a sobrecarga para gerar eventos para APIs de baixo nível, como tipos base ou coleções. Por exemplo, <xref:System.Collections.Generic.List%601> não geraria tais eventos quando um novo item é adicionado à lista e o `Count` alterações de propriedade.  
  
 **✓ CONSIDERE** gerando eventos de notificação quando o valor de uma propriedade é alterada por meio de forças externas de alteração.  
  
 Se um valor de propriedade for alterado por meio de alguns force externo (de forma diferente ao chamar métodos no objeto), aumentar os eventos indicam para o desenvolvedor que o valor está sendo alterada e foi alterado. Um bom exemplo é o `Text` propriedade de um controle de caixa de texto. Quando o usuário digita texto em uma `TextBox`, o valor da propriedade alterada automaticamente.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de design de membro](../../../docs/standard/design-guidelines/member.md)  
 [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
