---
title: Design de eventos
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- pre-events
- events [.NET Framework], design guidelines
- member design guidelines, events
- event handlers [.NET Framework], event design guidelines
- post-events
- signatures, event handling
ms.assetid: 67b3c6e2-6a8f-480d-a78f-ebeeaca1b95a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b257da73d33fae54ef464e9dd69906316b87fd88
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44064061"
---
# <a name="event-design"></a>Design de eventos
Eventos são a forma mais usada de retornos de chamada (construções que permitem que o framework chamar o código de usuário). Outros mecanismos de retorno de chamada incluem membros fazer delegados, os membros virtuais e plug-ins baseados em interface. Dados de estudos de usabilidade indicam que a maioria dos desenvolvedores estão mais familiarizado com o uso de eventos que estão usando outros mecanismos de retorno de chamada. Eventos são integrados perfeitamente com o Visual Studio e muitos idiomas.  
  
 É importante observar que há dois grupos de eventos: eventos gerados antes de um estado das alterações do sistema, chamado pré-eventos e eventos gerados depois que um estado for alterado, chamado pós eventos. Um exemplo de um pré-evento de seria `Form.Closing`, que é gerado antes de um formulário é fechado. Um exemplo de um pós-evento de seria `Form.Closed`, que é gerado depois que um formulário é fechado.  
  
 **✓ DO** usam o termo "raise" eventos em vez de "fire" ou "disparar".  
  
 **✓ DO** use <xref:System.EventHandler%601?displayProperty=nameWithType> em vez de criar manualmente novas delegados para serem usados como manipuladores de eventos.  
  
 **✓ CONSIDER** usando uma subclasse de <xref:System.EventArgs> como o argumento do evento, a menos que seja absolutamente-se de que o evento não será necessário executar todos os dados para o método de manipulação de eventos caso em que você pode usar o `EventArgs` digitados diretamente.  
  
 Se você enviar uma API usando `EventArgs` diretamente, você nunca poderá adicionar dados a ser realizada com o evento sem interromper a compatibilidade. Se você usar uma subclasse, mesmo se inicialmente completamente vazia, você poderá adicionar propriedades para a subclasse quando necessário.  
  
 **✓ DO** usar um método virtual protegido para gerar cada evento. Isso só é aplicável aos eventos não estáticos em classes sem lacre, não para structs, classes sealed ou eventos estáticos.  
  
 A finalidade do método é fornecer uma maneira para uma classe derivada manipular o evento usando uma substituição. Substituindo é uma maneira mais flexível, mais rápida e mais natural para lidar com eventos de classe base em classes derivadas. Por convenção, o nome do método deve começar com "On" e ser seguido pelo nome do evento.  
  
 A classe derivada pode optar por não chamar a implementação base do método na sua substituição. Esteja preparado para isso, não incluindo nenhum processamento no método que é necessário para a classe base funcionar corretamente.  
  
 **✓ DO** ter um parâmetro para o método protegido que gera um evento.  
  
 O parâmetro deve ser nomeado `e` e devem ser digitados como a classe de argumento do evento.  
  
 **X DO NOT** passar nulo como o remetente quando gerar um evento não estático.  
  
 **✓ DO** passar nulo como o remetente ao gerar um evento estático.  
  
 **X DO NOT** passar nulo como o parâmetro de dados de evento ao gerar um evento.  
  
 Você deve passar `EventArgs.Empty` se você não quiser passar nenhum dado para o método de manipulação de eventos. Os desenvolvedores esperam esse parâmetro não deve ser nulo.  
  
 **✓ CONSIDER** gerando eventos que o usuário final pode cancelar. Isso se aplica apenas aos pré eventos de.  
  
 Use <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> ou suas subclasses como o argumento de evento para permitir que o usuário final cancelar eventos.  
  
### <a name="custom-event-handler-design"></a>Design de manipulador de evento personalizado  
 Há casos em que `EventHandler<T>` não podem ser usadas, como quando o framework precisa trabalhar com versões anteriores do CLR, que não oferecia suporte a genéricos. Nesses casos, você talvez precise criar e desenvolver um delegado de manipulador de eventos personalizado.  
  
 **✓ DO** usar um tipo de retorno de void para manipuladores de eventos.  
  
 Um manipulador de eventos pode chamar vários métodos, possivelmente em vários objetos de manipulação de eventos. Se os métodos de manipulação de eventos foram permitidos para retornar um valor, deve haver vários valores de retorno para cada invocação do evento.  
  
 **✓ DO** usar `object` como o tipo do primeiro parâmetro do manipulador de eventos e chamá-la `sender`.  
  
 **✓ DO** usar <xref:System.EventArgs?displayProperty=nameWithType> ou suas subclasses como o tipo do segundo parâmetro do manipulador de eventos e chamá-la `e`.  
  
 **X DO NOT** ter mais de dois parâmetros em manipuladores de eventos.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também

- [Diretrizes de design de membro](../../../docs/standard/design-guidelines/member.md)  
- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
