---
title: Eventos e retornos de chamada
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- events [.NET Framework], extensibility
- methods [.NET Framework], callback
- callback methods
- callbacks
ms.assetid: 48b55c60-495f-4089-9396-97f9122bba7c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 390c12af7107bb78fc261c55ea15390cf9eaa5b7
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43862943"
---
# <a name="events-and-callbacks"></a>Eventos e retornos de chamada
Retornos de chamada são os pontos de extensibilidade que permitem que uma estrutura para a chamada de retorno no código do usuário por meio de um delegado. Esses delegados geralmente são passados para o framework por meio de um parâmetro de um método.  
  
 Os eventos são um caso especial de retornos de chamada que dá suporte à sintaxe conveniente e consistente para fornecer o delegado (um manipulador de eventos). Além disso, o preenchimento de declaração e designers do Visual Studio fornecem ajuda usando as APIs baseadas em evento. (Consulte [Design de eventos](../../../docs/standard/design-guidelines/event.md).)  
  
 **✓ CONSIDER** usando retornos de chamada para permitir que os usuários forneçam um código personalizado a ser executado pelo framework.  
  
 **✓ CONSIDER** usando eventos para permitir que os usuários personalizar o comportamento de uma estrutura sem a necessidade de Noções básicas sobre o design orientado a objeto.  
  
 **✓ DO** eventos prefira retornos de chamada comum, pois eles são mais familiares para uma variedade maior de desenvolvedores e integram-se a conclusão de instrução do Visual Studio.  
  
 **X AVOID** usando retornos de chamada nas APIs de desempenho confidenciais.  
  
 **✓ DO** usar o novo `Func<...>`, `Action<...>`, ou `Expression<...>` tipos em vez de delegados personalizados, ao definir APIs com retornos de chamada.  
  
 `Func<...>` e `Action<...>` representam os delegados genéricos. `Expression<...>` representa as definições de função que podem ser compiladas e invocadas posteriormente no tempo de execução, mas pode também ser serializadas e passadas para processos remotos.  
  
 **✓ DO** medir e compreender as implicações de desempenho do uso de `Expression<...>`, em vez de usar `Func<...>` e `Action<...>` delegados.  
  
 `Expression<...>` tipos são na maioria dos casos logicamente equivalente a `Func<...>` e `Action<...>` delegados. A principal diferença entre eles é que os delegados são deve ser usado em cenários de processo local; expressões são destinadas para casos em que é benéfico e é possível avaliar a expressão em um computador ou processo remoto.  
  
 **✓ DO** entender que, ao chamar um delegado, que está executando código arbitrário e que pode ter repercussões de segurança, a exatidão e a compatibilidade.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também

- [Designer voltado para extensibilidade](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
