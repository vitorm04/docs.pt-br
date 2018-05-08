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
ms.openlocfilehash: 90cc40024de627f151a4d0df879a65e5900004b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="events-and-callbacks"></a>Eventos e retornos de chamada
Retornos de chamada são os pontos de extensibilidade que permitem que uma estrutura de retorno de chamada no código de usuário por meio de um representante. Esses representantes geralmente são passados para o framework por meio de um parâmetro de um método.  
  
 Os eventos são um caso especial de retornos de chamada que dá suporte à sintaxe consistente e conveniente para fornecer o delegado (um manipulador de eventos). Além disso, a conclusão de instrução e designers de Visual Studio fornecem ajuda usando APIs com base em eventos. (Consulte [evento Design](../../../docs/standard/design-guidelines/event.md).)  
  
 **✓ CONSIDERE** usando retornos de chamada para permitir que os usuários forneçam um código personalizado a ser executado pelo framework.  
  
 **✓ CONSIDERE** usando eventos para permitir que os usuários personalizar o comportamento de uma estrutura sem a necessidade de Noções básicas sobre o design orientado a objeto.  
  
 **FAZER ✓** eventos prefira retornos de chamada comum, pois eles são mais familiares para uma variedade maior de desenvolvedores e integram-se a conclusão de instrução do Visual Studio.  
  
 **X Evite** usando retornos de chamada nas APIs de desempenho confidenciais.  
  
 **FAZER ✓** usar o novo `Func<...>`, `Action<...>`, ou `Expression<...>` tipos em vez de delegados personalizados, ao definir APIs com retornos de chamada.  
  
 `Func<...>` e `Action<...>` representar delegados genéricos. `Expression<...>` representa as definições de função que podem ser compiladas e subsequentemente invocadas em tempo de execução, mas também ser serializadas e passadas para processos remotos.  
  
 **FAZER ✓** medir e compreender as implicações de desempenho do uso de `Expression<...>`, em vez de usar `Func<...>` e `Action<...>` delegados.  
  
 `Expression<...>` tipos são na maioria dos casos logicamente equivalente à `Func<...>` e `Action<...>` delegados. A principal diferença entre eles é que os delegados destinam-se a ser usado em cenários de processo local; expressões são voltadas para casos onde é possível avaliar a expressão em um computador ou um processo remoto e útil.  
  
 **FAZER ✓** entender que, ao chamar um delegado, que está executando código arbitrário e que pode ter repercussões de segurança, a exatidão e a compatibilidade.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também  
 [Designer voltado para extensibilidade](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
