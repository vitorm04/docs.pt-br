---
title: Design de eventos
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pre-events
- events [.NET Framework], design guidelines
- member design guidelines, events
- event handlers [.NET Framework], event design guidelines
- post-events
- signatures, event handling
ms.assetid: 67b3c6e2-6a8f-480d-a78f-ebeeaca1b95a
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a07392ba805b5f2a3913b01a15dd0e1668f0ccf7
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="event-design"></a>Design de eventos
Os eventos são a forma mais usada de retornos de chamada (construções que permitem que a estrutura chamar o código de usuário). Outros mecanismos de retorno de chamada incluem membros colocar delegados, membros virtuais e plug-ins com base em interface. Dados de estudos de usabilidade indicam que a maioria dos desenvolvedores são mais familiarizado com o uso de eventos que estão usando outros mecanismos de retorno de chamada. Eventos são integrados perfeitamente com o Visual Studio e muitos idiomas.  
  
 É importante observar que há dois grupos de eventos: eventos gerado antes de um estado das alterações do sistema, chamado pré-eventos e eventos gerados depois de um estado de alterações, chamado pós-eventos. Um exemplo de um pré-evento de seria `Form.Closing`, que é gerado antes de um formulário é fechado. Um exemplo de um pós-evento de seria `Form.Closed`, que é gerado depois que um formulário é fechado.  
  
 **FAZER ✓** usam o termo "raise" eventos em vez de "fire" ou "disparar".  
  
 **FAZER ✓** use <xref:System.EventHandler%601?displayProperty=nameWithType> em vez de criar manualmente novas delegados para serem usados como manipuladores de eventos.  
  
 **✓ CONSIDERE** usando uma subclasse de <xref:System.EventArgs> como o argumento do evento, a menos que seja absolutamente-se de que o evento não será necessário executar todos os dados para o método de manipulação de eventos caso em que você pode usar o `EventArgs` digitados diretamente.  
  
 Se você enviar usando uma API `EventArgs` diretamente, você nunca poderá adicionar dados a ser executado com o evento sem perder a compatibilidade. Se você usar uma subclasse, mesmo se inicialmente completamente vazio, você poderá adicionar propriedades a subclasse quando necessário.  
  
 **FAZER ✓** usar um método virtual protegido para gerar cada evento. Isso só é aplicável para eventos não estáticos nas classes sem lacre, não para structs, classes lacradas ou eventos estáticos.  
  
 A finalidade do método é fornecer uma maneira para uma classe derivada para manipular o evento de uso de uma substituição. Substituindo é uma maneira mais flexível, mais rápida e mais natural para tratar eventos de classe base em classes derivadas. Por convenção, o nome do método deve começar com "On" e ser seguido pelo nome do evento.  
  
 A classe derivada pode optar por não chamar a implementação base do método na sua substituição. Esteja preparado para isso, não incluindo nenhum processamento no método que é necessário para a classe base funcionar corretamente.  
  
 **FAZER ✓** ter um parâmetro para o método protegido que gera um evento.  
  
 O parâmetro deve ser nomeado `e` e deve ser digitado como a classe de argumento do evento.  
  
 **X não** passar nulo como o remetente quando gerar um evento não estático.  
  
 **FAZER ✓** passar nulo como o remetente ao gerar um evento estático.  
  
 **X não** passar nulo como o parâmetro de dados de evento ao gerar um evento.  
  
 Você deve passar `EventArgs.Empty` se você não deseja transmitir os dados para o método de manipulação de eventos. Os desenvolvedores espera que esse parâmetro não deve ser nulo.  
  
 **✓ CONSIDERE** gerando eventos que o usuário final pode cancelar. Isso só se aplica a pré eventos.  
  
 Use <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> ou suas subclasses como o argumento do evento para permitir que o usuário final cancelar eventos.  
  
### <a name="custom-event-handler-design"></a>Design do manipulador de eventos personalizados  
 Há casos em que `EventHandler<T>` não pode ser usado, como quando o framework precisa trabalhar com versões anteriores do CLR, o que não oferecia suporte a genéricos. Nesses casos, você precisará criar e desenvolver um representante do manipulador de eventos personalizados.  
  
 **FAZER ✓** usar um tipo de retorno de void para manipuladores de eventos.  
  
 Um manipulador de eventos pode chamar vários métodos, possivelmente em vários objetos de manipulação de eventos. Se os métodos de manipulação de eventos foram permitidos para retornar um valor, seria vários valores de retorno para cada invocação de eventos.  
  
 **FAZER ✓** usar `object` como o tipo do primeiro parâmetro do manipulador de eventos e chamá-la `sender`.  
  
 **FAZER ✓** usar <xref:System.EventArgs?displayProperty=nameWithType> ou suas subclasses como o tipo do segundo parâmetro do manipulador de eventos e chamá-la `e`.  
  
 **X não** ter mais de dois parâmetros em manipuladores de eventos.  
  
 *Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de design de membro](../../../docs/standard/design-guidelines/member.md)  
 [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
