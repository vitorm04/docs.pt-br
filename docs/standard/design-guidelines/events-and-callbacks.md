---
title: Eventos e retornos de chamada
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- events [.NET Framework], extensibility
- methods [.NET Framework], callback
- callback methods
- callbacks
ms.assetid: 48b55c60-495f-4089-9396-97f9122bba7c
ms.openlocfilehash: 80c16e29f1d8a0653295ebc3cf25be6fb78b7dc9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709407"
---
# <a name="events-and-callbacks"></a>Eventos e retornos de chamada
Os retornos de chamada são pontos de extensibilidade que permitem que uma estrutura chame de volta no código do usuário por meio de um delegado. Esses delegados são geralmente passados para a estrutura por meio de um parâmetro de um método.  
  
 Os eventos são um caso especial de retornos de chamada que dão suporte a sintaxe conveniente e consistente para fornecer o delegado (um manipulador de eventos). Além disso, a conclusão e os designers de instruções do Visual Studio fornecem ajuda no uso de APIs baseadas em eventos. (Consulte [design de eventos](../../../docs/standard/design-guidelines/event.md).)  
  
 **✓ CONSIDER** usando retornos de chamada para permitir que os usuários forneçam um código personalizado a ser executado pelo framework.  
  
 **✓ CONSIDER** usando eventos para permitir que os usuários personalizar o comportamento de uma estrutura sem a necessidade de Noções básicas sobre o design orientado a objeto.  
  
 **✓ DO** eventos prefira retornos de chamada comum, pois eles são mais familiares para uma variedade maior de desenvolvedores e integram-se a conclusão de instrução do Visual Studio.  
  
 **X AVOID** usando retornos de chamada nas APIs de desempenho confidenciais.  
  
 **✓ DO** usar o novo `Func<...>`, `Action<...>`, ou `Expression<...>` tipos em vez de delegados personalizados, ao definir APIs com retornos de chamada.  
  
 `Func<...>` e `Action<...>` representam delegados genéricos. `Expression<...>` representa as definições de função que podem ser compiladas e, posteriormente, invocadas no tempo de execução, mas também podem ser serializadas e passadas para processos remotos.  
  
 **✓ DO** medir e compreender as implicações de desempenho do uso de `Expression<...>`, em vez de usar `Func<...>` e `Action<...>` delegados.  
  
 os tipos de `Expression<...>` estão na maioria dos casos logicamente equivalentes a delegados `Func<...>` e `Action<...>`. A principal diferença entre eles é que os delegados se destinam a serem usados em cenários de processo local; as expressões são destinadas a casos em que é benéfico e possível avaliar a expressão em um computador ou processo remoto.  
  
 **✓ DO** entender que, ao chamar um delegado, que está executando código arbitrário e que pode ter repercussões de segurança, a exatidão e a compatibilidade.  
  
 *Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Veja também

- [Designer voltado para extensibilidade](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
