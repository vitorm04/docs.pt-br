---
title: Diretrizes de Design de membro
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- member design guidelines [.NET Framework], about member design guidelines
- members [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], members
- member design guidelines [.NET Framework]
ms.assetid: 0ce93180-1d7b-4f8c-9306-f828b2d66b8f
caps.latest.revision: 14
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8f4e33735a934b1ac41c34ccb9698c172ada28e1
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="member-design-guidelines"></a>Diretrizes de Design de membro
Métodos, propriedades, eventos, construtores e campos são chamados, coletivamente como membros. Os membros são, por fim, o meio pelo qual funcionalidade do framework é exposta aos usuários finais de uma estrutura.  
  
 Membros podem ser virtual ou, concreto ou abstrato, estático ou instância e podem ter vários escopos diferentes de acessibilidade. Todos os essa variedade fornece expressividade incrível mas ao mesmo tempo requer cuidado por parte do designer de estrutura.  
  
 Este capítulo oferece diretrizes básicas que devem ser seguidas durante a criação de membros de qualquer tipo.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Sobrecarga de membro](../../../docs/standard/design-guidelines/member-overloading.md)  
 [Design de propriedade](../../../docs/standard/design-guidelines/property.md)  
 [Design do construtor](../../../docs/standard/design-guidelines/constructor.md)  
 [Design de eventos](../../../docs/standard/design-guidelines/event.md)  
 [Design de campo](../../../docs/standard/design-guidelines/field.md)  
 [Métodos de Extensão](../../../docs/standard/design-guidelines/extension-methods.md)  
 [Sobrecargas de operador](../../../docs/standard/design-guidelines/operator-overloads.md)  
 [Design de parâmetro](../../../docs/standard/design-guidelines/parameter-design.md)  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
