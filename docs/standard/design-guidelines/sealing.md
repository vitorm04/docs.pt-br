---
title: Lacrar
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- limiting extensibility
- classes [.NET Framework], sealing
- preventing customization
- sealed classes
ms.assetid: cc42267f-bb7a-427a-845e-df97408528d4
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8caa253a3f17c58f542317de579c4f7832c4efac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="sealing"></a>Lacrar
Um dos recursos orientados a objeto estruturas é que os desenvolvedores podem estender e personalizá-los de maneiras inesperadas pelos designers do framework. Este é o poder e o risco de design extensível. Quando você cria a estrutura, ele é, portanto, muito importante projetar cuidadosamente para extensibilidade quando for necessário e para limitar a extensibilidade quando é perigoso.  
  
 Um mecanismo avançado que impede a extensibilidade é lacrar. Você pode lacrar classe ou membros individuais. Lacrar uma classe impede que os usuários de herdar da classe. Lacrar um membro impede que os usuários ignorem um determinado membro.  
  
 **X não** lacrar classes sem ter uma boa razão para isso.  
  
 Não é uma boa razão lacrar uma classe, porque você não pode pensar em um cenário de extensibilidade. Como os usuários do Framework herdar das classes por várias razões nonobvious, como a adição de membros de conveniência. Consulte [Classes não lacradas](../../../docs/standard/design-guidelines/unsealed-classes.md) para obter exemplos dos motivos nonobvious usuários desejam herdar de um tipo.  
  
 Boas razões para isso uma classe incluem o seguinte:  
  
-   A classe é uma classe estática. Consulte [Design de classe estática](../../../docs/standard/design-guidelines/static-class.md).  
  
-   A classe armazena segredos sensível à segurança em membros protegidos herdados.  
  
-   A classe herda muitos membros virtuais e o custo de lacrá-los individualmente seria superam os benefícios de deixar a classe sem lacre.  
  
-   A classe é um atributo que requer a pesquisa de tempo de execução muito rápido. Atributos lacrados têm níveis de desempenho ligeiramente maiores que sem lacre. consulte [atributos](../../../docs/standard/design-guidelines/attributes.md).  
  
 **X não** declarar membros virtuais ou protegidos em tipos lacrados.  
  
 Por definição, tipos lacrados não podem ser herdados de. Isso significa que membros protegidos em tipos lacrados não podem ser chamados e métodos virtuais em tipos lacrados não podem ser substituídos.  
  
 **✓ CONSIDERE** lacrar membros que você substituir.  
  
 Problemas que podem resultar de introduzir membros virtuais (discutido na [membros virtuais](../../../docs/standard/design-guidelines/virtual-members.md)) se aplicam a substituições, embora a um nível um pouco menor. Lacrar uma substituição protege contra esses problemas a partir desse ponto na hierarquia de herança.  
  
 *Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)  
 [Criação de extensibilidade](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 [Classes não lacradas](../../../docs/standard/design-guidelines/unsealed-classes.md)
