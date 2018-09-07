---
title: Classes base para implementar abstrações
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- abstractions [.NET Framework]
- base classes, abstractions
ms.assetid: 37a2d9a4-9721-482a-a40f-eee2c1d97875
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f326ee895251678c7a23ea84a11e83951edf2cc
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44078633"
---
# <a name="base-classes-for-implementing-abstractions"></a>Classes base para implementar abstrações
Estritamente falando, uma classe se torna uma classe base quando outra classe for derivada dela. Para fins desta seção, no entanto, uma classe base é uma classe projetada principalmente para fornecer uma abstração comum ou para outras classes de reutilizar parte implementação padrão entanto herança. Classes base geralmente ficam no meio de hierarquias de herança entre uma abstração na raiz de uma hierarquia e várias implementações personalizadas na parte inferior.  
  
 Eles servem como auxiliares de implementação para implementar abstrações. Por exemplo, uma das abstrações da estrutura para conjuntos ordenados de itens é o <xref:System.Collections.Generic.IList%601> interface. Implementando <xref:System.Collections.Generic.IList%601> não é trivial, e, portanto, o Framework fornece várias classes base, como <xref:System.Collections.ObjectModel.Collection%601> e <xref:System.Collections.ObjectModel.KeyedCollection%602>, que funcionam como auxiliares para coleções personalizadas de implementação.  
  
 Classes base geralmente não são adequadas para servir como abstrações por si só, porque eles tendem a conter muita implementação. Por exemplo, o `Collection<T>` classe base contém muita implementação relacionada ao fato de que ele implementa não genérica `IList` interface (para integrar-se melhor com coleções não genéricas) e ao fato de que ele é uma coleção de itens armazenados em memória em um de seus campos.  
  
 Conforme discutido anteriormente, as classes base podem fornecer ajuda valiosa para usuários que precisam implementar abstrações, mas ao mesmo tempo, eles podem ser uma responsabilidade significativa. Eles Adicionar área de superfície e aumentam a profundidade das hierarquias de herança e, assim, conceitualmente complicam a estrutura. Portanto, as classes base devem ser usadas somente se eles fornecem valor significativo para os usuários do framework. Eles devem ser evitados se eles fornecem valor apenas para os implementadores do framework, no qual a delegação caso a uma implementação interna em vez da herança de uma classe base deve ser fortemente considerada.  
  
 **✓ CONSIDER** abstrato as classes base tornando mesmo se eles não contêm membros abstratos. Isso claramente se comunica com os usuários que a classe destina-se exclusivamente a ser herdada.  
  
 **✓ CONSIDER** colocando classes base em um namespace separado dos tipos de cenário principal. Por definição, as classes base são destinadas a cenários de extensibilidade avançada e, portanto, não são interessantes para a maioria dos usuários.  
  
 **X AVOID** nomeando classes base com um sufixo "Base" se a classe é destinada para uso em APIs públicas.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também

- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)  
- [Designer voltado para extensibilidade](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
