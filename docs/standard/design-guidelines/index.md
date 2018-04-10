---
title: Diretrizes de design de estrutura
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- libraries, .NET Framework class library
- class library design guidelines [.NET Framework], about
- class library design guidelines [.NET Framework]
ms.assetid: 5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b
caps.latest.revision: 14
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c48b3cbaae4155a894ba77263505b2ca85238427
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="framework-design-guidelines"></a>Diretrizes de design de estrutura
Esta seção fornece diretrizes para a criação de bibliotecas que estendem e interagem com o .NET Framework. A meta é ajudar os designers de biblioteca a garantir a consistência de API e facilidade de uso, fornecendo um modelo de programação unificado que é independente da linguagem de programação usada para desenvolvimento. É recomendável que você siga estas diretrizes de design ao desenvolver classes e componentes que estendem o .NET Framework. Projeto de biblioteca inconsistente negativamente afeta a produtividade do desenvolvedor e desencoraja adoção.  
  
 As diretrizes são organizadas como recomendações simples prefixadas com os termos de `Do`, `Consider`, `Avoid`, e `Do not`. Estas diretrizes destinam-se para ajudar a entender as compensações entre as diferentes soluções de designers de biblioteca de classe. Pode haver situações em que o design de boa biblioteca requer que violam essas diretrizes de design. Tais casos devem ser raros, e é importante que você tenha um motivo claro e convincente para sua decisão.  
  
 Essas diretrizes foram extraídas do catálogo de *diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição*, Krzysztof Cwalina e Brad Abrams.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Diretrizes de nomenclatura](../../../docs/standard/design-guidelines/naming-guidelines.md)  
 Fornece diretrizes de nomeação de assemblies, namespaces, tipos e membros em bibliotecas de classe.  
  
 [Diretrizes de Design de tipo](../../../docs/standard/design-guidelines/type.md)  
 Fornece diretrizes para usar classes estáticas e abstratos, interfaces, enumerações, estruturas e outros tipos.  
  
 [Diretrizes de design de membro](../../../docs/standard/design-guidelines/member.md)  
 Fornece diretrizes para criar e usar propriedades, métodos, construtores, campos, eventos, operadores e parâmetros.  
  
 [Designer voltado para extensibilidade](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 Discute os mecanismos de extensibilidade, como subclassificação, usando membros virtuais, eventos e retornos de chamada e explica como escolher os mecanismos que melhor atende aos requisitos do framework.  
  
 [Diretrizes de design para exceções](../../../docs/standard/design-guidelines/exceptions.md)  
 Descreve as diretrizes de design para criação, gerar e capturar exceções.  
  
 [Diretrizes de uso](../../../docs/standard/design-guidelines/usage-guidelines.md)  
 Descreve as diretrizes para usar tipos comuns, como matrizes, atributos e coleções, dando suporte a serialização e sobrecarga de operadores de igualdade.  
  
 [Padrões comuns de Design](../../../docs/standard/design-guidelines/common-design-patterns.md)  
 Fornece diretrizes para escolher e implementar propriedades de dependência e o padrão dispose.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também  
 [Visão Geral](../../../docs/framework/get-started/overview.md)  
 [Roteiro para o .NET Framework](http://msdn.microsoft.com/library/0b46b7c6-9163-4f99-8e58-0d1ee7da8c67)  
 [Guia de desenvolvimento](../../../docs/framework/development-guide.md)
