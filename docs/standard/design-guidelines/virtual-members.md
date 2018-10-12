---
title: Membros virtuais
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- overridable members
- virtual members
- members [.NET Framework], virtual
ms.assetid: 8ff4eb97-0364-43ec-8a02-934b5cd94d19
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b92b648e7886fb0214238e32eacae2870b470340
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49121059"
---
# <a name="virtual-members"></a>Membros virtuais
Membros virtuais podem ser substituídos, portanto, alterar o comportamento da subclasse. Eles são muito semelhantes aos retornos de chamada em termos de extensibilidade que eles fornecem, mas eles são melhores em termos de desempenho de execução e o consumo de memória. Além disso, os membros virtuais se sentir mais naturais em cenários que exigem a criação de um especial de um tipo existente (especialização).  
  
 Membros virtuais executam melhor eventos e retornos de chamada, mas não executam melhor do que métodos não virtuais.  
  
 A principal desvantagem de membros virtuais é que o comportamento de um membro virtual só pode ser modificado no momento da compilação. O comportamento de um retorno de chamada pode ser modificado no tempo de execução.  
  
 Membros virtuais, assim como os retornos de chamada (e talvez mais do que os retornos de chamada), são caros de criar, testar e manter, porque qualquer chamada para um membro virtual pode ser substituída de forma imprevisível e pode executar código arbitrário. Além disso, muito mais esforço geralmente é necessário para definir claramente o contrato de membros virtuais, portanto, o custo de criação e documentá-los é maior.  
  
 **X DO NOT** tornar membros virtuais, a menos que você tem uma boa razão para isso e você está ciente de todos os custos relacionados à criação, teste e manutenção membros virtuais.  
  
 Os membros virtuais serão menos tolerante em termos das alterações que podem ser feitas a eles sem interromper a compatibilidade. Além disso, eles são mais lentos que os membros não-virtual, principalmente porque as chamadas para os membros virtuais não são embutidas.  
  
 **✓ CONSIDER** limitando extensibilidade apenas o que é absolutamente necessário.  
  
 **✓ DO** prefira acessibilidade protegida acessibilidade pública para membros virtuais. Os membros públicos devem fornecer extensibilidade (se necessário) chamando um membro virtual protegida.  
  
 Os membros públicos de uma classe devem fornecer o conjunto certo de funcionalidade para os consumidores diretos dessa classe. Membros virtuais são projetados para ser substituído em subclasses e acessibilidade protegida é uma ótima maneira de definir o escopo de todos os pontos de extensibilidade virtual onde eles podem ser usados.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também

- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)  
- [Designer voltado para extensibilidade](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
