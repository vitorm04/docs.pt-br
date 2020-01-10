---
title: Design de eventos
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- pre-events
- events [.NET Framework], design guidelines
- member design guidelines, events
- event handlers [.NET Framework], event design guidelines
- post-events
- signatures, event handling
ms.assetid: 67b3c6e2-6a8f-480d-a78f-ebeeaca1b95a
ms.openlocfilehash: 78d765a7af77b1e6a6ecd483677cea2d4c6b0d5b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709420"
---
# <a name="event-design"></a>Design de eventos
Os eventos são a forma mais comumente usada de retornos de chamada (construções que permitem que a estrutura chame no código do usuário). Outros mecanismos de retorno de chamada incluem membros que utilizam delegados, membros virtuais e plug-ins baseados em interface. os dados de estudos de usabilidade indicam que a maioria dos desenvolvedores é mais confortável usando eventos do que usar os outros mecanismos de retorno de chamada . Os eventos são perfeitamente integrados ao Visual Studio e a várias linguagens.  
  
 É importante observar que há dois grupos de eventos: eventos gerados antes que um estado do sistema seja alterado, chamado pré-eventos e eventos gerados depois de um Estado ser alterado, chamado post-events. Um exemplo de um pré-evento seria `Form.Closing`, que é gerado antes que um formulário seja fechado. Um exemplo de um post-Event seria `Form.Closed`, que é gerado depois que um formulário é fechado.  
  
 **✓ DO** usam o termo "raise" eventos em vez de "fire" ou "disparar".  
  
 **✓ DO** use <xref:System.EventHandler%601?displayProperty=nameWithType> em vez de criar manualmente novas delegados para serem usados como manipuladores de eventos.  
  
 **✓ CONSIDER** usando uma subclasse de <xref:System.EventArgs> como o argumento do evento, a menos que seja absolutamente-se de que o evento não será necessário executar todos os dados para o método de manipulação de eventos caso em que você pode usar o `EventArgs` digitados diretamente.  
  
 Se você enviar uma API usando `EventArgs` diretamente, nunca será possível adicionar dados a serem transportados com o evento sem a necessidade de perder a compatibilidade. Se você usar uma subclasse, mesmo que inicialmente completamente vazia, você poderá adicionar propriedades à subclasse quando necessário.  
  
 **✓ DO** usar um método virtual protegido para gerar cada evento. Isso só é aplicável a eventos não estáticos em classes sem lacre, não a structs, a classes seladas ou a eventos estáticos.  
  
 A finalidade do método é fornecer uma maneira para uma classe derivada manipular o evento usando uma substituição. A substituição é uma maneira mais flexível, mais rápida e natural de lidar com eventos de classe base em classes derivadas. Por convenção, o nome do método deve começar com "on" e ser seguido do nome do evento.  
  
 A classe derivada pode optar por não chamar a implementação base do método em sua substituição. Esteja preparado para isso por não incluir nenhum processamento no método necessário para que a classe base funcione corretamente.  
  
 **✓ DO** ter um parâmetro para o método protegido que gera um evento.  
  
 O parâmetro deve ser nomeado `e` e deve ser digitado como a classe de argumento de evento.  
  
 **X DO NOT** passar nulo como o remetente quando gerar um evento não estático.  
  
 **✓ DO** passar nulo como o remetente ao gerar um evento estático.  
  
 **X DO NOT** passar nulo como o parâmetro de dados de evento ao gerar um evento.  
  
 Você deve passar `EventArgs.Empty` se não quiser passar dados para o método de manipulação de eventos. Os desenvolvedores esperam que esse parâmetro não seja nulo.  
  
 **✓ CONSIDER** gerando eventos que o usuário final pode cancelar. Isso se aplica apenas a eventos anteriores.  
  
 Use <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> ou sua subclasse como o argumento de evento para permitir que o usuário final cancele eventos.  
  
### <a name="custom-event-handler-design"></a>Design do manipulador de eventos personalizado  
 Há casos em que `EventHandler<T>` não pode ser usado, como quando a estrutura precisa trabalhar com versões anteriores do CLR, o que não oferecia suporte a genéricos. Nesses casos, talvez seja necessário criar e desenvolver um delegado de manipulador de eventos personalizado.  
  
 **✓ DO** usar um tipo de retorno de void para manipuladores de eventos.  
  
 Um manipulador de eventos pode invocar vários métodos de manipulação de eventos, possivelmente em vários objetos. Se os métodos de manipulação de eventos tivessem permissão para retornar um valor, haveria vários valores de retorno para cada invocação de evento.  
  
 **✓ DO** usar `object` como o tipo do primeiro parâmetro do manipulador de eventos e chamá-la `sender`.  
  
 **✓ DO** usar <xref:System.EventArgs?displayProperty=nameWithType> ou suas subclasses como o tipo do segundo parâmetro do manipulador de eventos e chamá-la `e`.  
  
 **X DO NOT** ter mais de dois parâmetros em manipuladores de eventos.  
  
 *Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Veja também

- [Diretrizes de design de membro](../../../docs/standard/design-guidelines/member.md)
- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
