---
title: Classes não seladas
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- classes [.NET Framework], unsealed
- unsealed classes
- inheritance, classes
ms.assetid: 9a3bd505-90f5-4053-9f0d-3cf5fa3d3ebf
author: KrzysztofCwalina
ms.openlocfilehash: 8d7b1500506ec73a0d33d5352756cb85039358e5
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53153222"
---
# <a name="unsealed-classes"></a>Classes não seladas
Classes sealed não podem ser herdadas de, e evitar a extensibilidade. Em contraste, as classes que podem ser herdadas de são chamadas classes não seladas.  
  
 **✓ CONSIDER** usar classes não lacradas sem nenhum adicionado membros virtuais ou protegidos como uma ótima maneira de fornecer mais barato ainda muito mais valioso extensibilidade para uma estrutura.  
  
 Os desenvolvedores geralmente desejam herdar de classes não seladas para adicionar membros de conveniência, como construtores personalizados, novos métodos ou sobrecargas de método. Por exemplo, `System.Messaging.MessageQueue` é sem lacre e, portanto, permite que os usuários criem filas personalizadas esse padrão para um caminho de fila particular ou adicione métodos personalizados que simplificam a API para cenários específicos.  
  
 As classes são sem lacre por padrão em linguagens de programação mais e isso também é o padrão recomendado para a maioria das classes em estruturas. A extensibilidade proporcionada pelo tipos sem lacre é muito apreciados por usuários da estrutura e muito barato para fornecer devido a custos relativamente baixo de teste associados a tipos sem lacre.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpresso com permissão da Pearson Education, Inc. de [as diretrizes de Design do Framework: As convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008 pela Addison-Wesley Professional, como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também

- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)  
- [Designer voltado para extensibilidade](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
- [Selar](../../../docs/standard/design-guidelines/sealing.md)
