---
title: Abstrações (tipos e Interfaces abstratos)
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- interfaces [.NET Framework], abstract
- abstract interfaces [.NET Framework]
- abstract types [.NET Framework]
- types [.NET Framework], abstract
ms.assetid: 0a632bc7-9b03-44ee-8842-c82f88672a45
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0ad8b2dd3dbf2a7a75c98a3115d4351dfea4e1a0
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44182116"
---
# <a name="abstractions-abstract-types-and-interfaces"></a>Abstrações (tipos e Interfaces abstratos)
Uma abstração é um tipo que descreve um contrato, mas não fornece uma implementação completa do contrato. Abstrações geralmente são implementadas como classes abstratas ou interfaces, e entram com um conjunto bem definido de documentação de referência que descreve a semântica necessária dos tipos de implementação do contrato. Algumas das abstrações mais importantes no .NET Framework incluem <xref:System.IO.Stream>, <xref:System.Collections.Generic.IEnumerable%601>, e <xref:System.Object>.  
  
 Você pode estender estruturas implementando um tipo concreto que dá suporte ao contrato de uma abstração e usando esse tipo concreto com framework APIs consumo (operando em) a abstração.  
  
 Uma abstração de significativa e úteis que é capaz de suportar o teste de tempo é muito difícil de design. A dificuldade principal é obter o conjunto certo de membros, não há mais e menos não. Se uma abstração tem muitos membros, fica difícil ou até mesmo impossível implementar. Se ela tiver muito poucos membros para a funcionalidade prometido, se tornará inútil em muitos cenários interessantes.  
  
 Número excessivo de abstrações em uma estrutura também afetam de usabilidade do framework. Geralmente é muito difícil de entender uma abstração sem compreender como ele se adapta a imagem maior de APIs operando com a abstração e as implementações concretas. Além disso, os nomes das abstrações e seus membros são necessariamente abstratos, que muitas vezes os torna confuso e não-receptiva sem primeiro compreender o contexto mais amplo de uso.  
  
 No entanto, as abstrações fornecem extensibilidade extremamente poderosa que geralmente não podem corresponder a outros mecanismos de extensibilidade. Eles são a essência de muitos padrões de arquitetura, como plug-ins, inversão de controle (IoC), pipelines e assim por diante. Eles também são extremamente importantes para a capacidade de teste de estruturas. Boa abstrações tornam possível criar um stub dependências pesadas para fins de teste de unidade. Em resumo, as abstrações são responsáveis pela riqueza mais ansiada das estruturas modernas orientadas a objeto.  
  
 **X DO NOT** fornecem abstrações, a menos que eles são testados com o desenvolvimento de várias implementações concretas e APIs, as abstrações de consumo.  
  
 **✓ DO** escolha cuidadosamente entre uma classe abstrata e uma interface ao projetar uma abstração.  
  
 **✓ CONSIDER** fornecendo testes de referência para implementações concretas das abstrações. Esses testes devem permitir que os usuários testar se suas implementações implementam corretamente o contrato.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também

- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)  
- [Designer voltado para extensibilidade](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
