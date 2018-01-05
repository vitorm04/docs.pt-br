---
title: "Abstrações (tipos abstratos e Interfaces)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interfaces [.NET Framework], abstract
- abstract interfaces [.NET Framework]
- abstract types [.NET Framework]
- types [.NET Framework], abstract
ms.assetid: 0a632bc7-9b03-44ee-8842-c82f88672a45
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 276c5883487d8fba47d7fb80060d4c947e0f6cd6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="abstractions-abstract-types-and-interfaces"></a>Abstrações (tipos abstratos e Interfaces)
Uma abstração é um tipo que descreve um contrato, mas não fornece uma implementação completa do contrato. Abstrações geralmente são implementadas como interfaces ou classes abstratas e entram com um conjunto bem definido de documentação de referência que descreve a semântica necessária dos tipos de implementação do contrato. Algumas das abstrações mais importantes no .NET Framework incluem <xref:System.IO.Stream>, <xref:System.Collections.Generic.IEnumerable%601>, e <xref:System.Object>.  
  
 Você pode estender estruturas de implementação de um tipo concreto que dá suporte ao contrato de uma abstração e usando esse tipo concreto com estrutura APIs consumo (operando em) a abstração.  
  
 Uma abstração significativa e útil que é capaz de suportar o teste de tempo é muito difícil de design. A dificuldade principal está obtendo o conjunto certo de membros, não mais e menos não. Se uma abstração tem muitos membros, será difícil ou impossível mesmo implementar. Se ela tiver muito poucos membros para a funcionalidade prometido, torna-se inúteis em muitos cenários interessantes.  
  
 Muitos abstrações em uma estrutura também afetam usabilidade do framework. Geralmente é muito difícil de entender uma abstração sem entender como ele se encaixa maior das implementações concretas e as APIs que operam na abstração. Além disso, os nomes das abstrações e seus membros são necessariamente abstratos, que geralmente torna criptografadas e não-receptiva sem primeiro entender o contexto mais amplo de uso.  
  
 No entanto, abstrações fornecem extensibilidade extremamente eficiente que geralmente não podem corresponder a outros mecanismos de extensibilidade. Eles são a essência de vários padrões de arquitetura, como plug-ins, inversão de controle (IoC), pipelines e assim por diante. Eles também são extremamente importantes para a capacidade de teste de estruturas. BOM abstrações possibilitam o stub dependências intensa para fins de teste de unidade. Em resumo, as abstrações são responsáveis pela riqueza procurada a estruturas moderna e orientada a objeto.  
  
 **X não** fornecem abstrações, a menos que eles são testados com o desenvolvimento de várias implementações concretas e APIs, as abstrações de consumo.  
  
 **FAZER ✓** escolha cuidadosamente entre uma classe abstrata e uma interface ao projetar uma abstração.  
  
 **✓ CONSIDERE** fornecendo testes de referência para implementações concretas das abstrações. Esses testes devem permitir que os usuários testar se suas implementações implementam corretamente o contrato.  
  
 *Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)  
 [Designer voltado para extensibilidade](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
