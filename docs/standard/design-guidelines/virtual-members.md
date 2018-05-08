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
ms.openlocfilehash: fa4227fc4476b86f07216650b22fccc25af7dd98
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="virtual-members"></a>Membros virtuais
Membros virtuais podem ser substituídos, portanto, alterar o comportamento da subclasse. Eles são bastante semelhantes para retornos de chamada em termos de extensibilidade que eles fornecem, mas eles são melhores em termos de desempenho de execução e o consumo de memória. Além disso, os membros virtuais achar mais naturais em cenários que exigem a criação especial de tipo de um tipo existente (especialização).  
  
 Membros virtuais têm desempenho melhor que eventos e retornos de chamada, mas não executar melhor métodos não virtuais.  
  
 A principal desvantagem de membros virtuais é que o comportamento de um membro virtual só pode ser modificado no momento da compilação. O comportamento de um retorno de chamada pode ser modificado no tempo de execução.  
  
 Membros virtuais, como retornos de chamada (e talvez mais de retornos de chamada), são caros criar, testar e manter, porque qualquer chamada para um membro virtual pode ser substituída de forma imprevisível e pode executar código arbitrário. Além disso, muito mais esforço geralmente é necessário definir claramente o contrato de membros virtuais, portanto, o custo de projetar e documentá-los é maior.  
  
 **X não** tornar membros virtuais, a menos que você tem uma boa razão para isso e você está ciente de todos os custos relacionados à criação, teste e manutenção membros virtuais.  
  
 Membros virtuais são menos tolerante com em termos de alterações que podem ser feitas a eles sem perder a compatibilidade. Além disso, eles são mais lentos do que os membros não virtual, principalmente como chamadas para membros virtuais não são embutidas.  
  
 **✓ CONSIDERE** limitando extensibilidade apenas o que é absolutamente necessário.  
  
 **FAZER ✓** prefira acessibilidade protegida acessibilidade pública para membros virtuais. Membros públicos devem fornecer extensibilidade (se necessário) por chamar um membro virtual protegido.  
  
 Os membros públicos de uma classe devem fornecer o conjunto certo de funcionalidade para consumidores diretos dessa classe. Membros virtuais são projetados para ser substituído em subclasses e acessibilidade protegida é uma ótima maneira de definir o escopo de todos os pontos de extensibilidade virtual onde eles podem ser usados.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)  
 [Designer voltado para extensibilidade](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
