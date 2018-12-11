---
title: Diretrizes de design de estrutura
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- libraries, .NET Framework class library
- class library design guidelines [.NET Framework], about
- class library design guidelines [.NET Framework]
ms.assetid: 5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b
author: KrzysztofCwalina
ms.openlocfilehash: 736069926a2a3fdc4856a51c5226f725b22c1d5f
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53147594"
---
# <a name="framework-design-guidelines"></a>Diretrizes de design de estrutura
Esta seção fornece diretrizes para a criação de bibliotecas que estendem e interagem com o .NET Framework. O objetivo é ajudar os designers de bibliotecas a garantir a consistência de API e facilidade de uso, fornecendo um modelo de programação unificado que é independente da linguagem de programação usada para o desenvolvimento. É recomendável que você siga estas diretrizes de design ao desenvolver classes e componentes que estendam o .NET Framework. Design de bibliotecas inconsistente negativamente afeta a produtividade do desenvolvedor e desencoraja a adoção.  
  
 As diretrizes são organizadas como recomendações simples prefixadas com os termos `Do`, `Consider`, `Avoid`, e `Do not`. Estas diretrizes destinam-se a ajudar os designers de biblioteca de classes a entender as compensações entre as diferentes soluções. Pode haver situações em que o design de boa biblioteca requer que você viole essas diretrizes de design. Nesses casos, devem ser raros, e é importante que você tenha um motivo claro e convincente para sua decisão.  
  
 Estas diretrizes foram extraídas do livro *as diretrizes de Design do Framework: As convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2nd Edition*, por Krzysztof Cwalina e Brad Abrams.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Diretrizes de nomenclatura](../../../docs/standard/design-guidelines/naming-guidelines.md)  
 Fornece diretrizes para a nomeação de assemblies, namespaces, tipos e membros em bibliotecas de classes.  
  
 [Diretrizes de Design de tipo](../../../docs/standard/design-guidelines/type.md)  
 Fornece diretrizes para usar classes abstratas e estáticas, interfaces, enumerações, estruturas e outros tipos.  
  
 [Diretrizes de design de membro](../../../docs/standard/design-guidelines/member.md)  
 Fornece diretrizes para criação e uso de propriedades, métodos, construtores, campos, eventos, operadores e parâmetros.  
  
 [Designer voltado para extensibilidade](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 Discute os mecanismos de extensibilidade, como a criação de subclasses, usando eventos, os membros virtuais e retornos de chamada e explica como escolher os mecanismos que melhor atendem aos requisitos da sua estrutura.  
  
 [Diretrizes de design para exceções](../../../docs/standard/design-guidelines/exceptions.md)  
 Descreve as diretrizes de design para projetar, lançar e capturar exceções.  
  
 [Diretrizes de uso](../../../docs/standard/design-guidelines/usage-guidelines.md)  
 Descreve diretrizes para usando tipos comuns, como matrizes, atributos e coleções, suporte à serialização e sobrecarga de operadores de igualdade.  
  
 [Padrões comuns de Design](../../../docs/standard/design-guidelines/common-design-patterns.md)  
 Fornece diretrizes para escolher e implementar as propriedades de dependência e o padrão de descarte.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpresso com permissão da Pearson Education, Inc. de [as diretrizes de Design do Framework: As convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008 pela Addison-Wesley Professional, como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também

- [Visão geral](../../../docs/framework/get-started/overview.md)  
- [Roteiro para o .NET Framework](https://msdn.microsoft.com/library/0b46b7c6-9163-4f99-8e58-0d1ee7da8c67)  
- [Guia de desenvolvimento](../../../docs/framework/development-guide.md)
