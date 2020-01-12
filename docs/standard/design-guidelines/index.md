---
title: Diretrizes de design de estrutura
titleSuffix: ''
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- libraries, .NET Framework class library
- class library design guidelines [.NET Framework], about
- class library design guidelines [.NET Framework]
ms.assetid: 5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b
ms.openlocfilehash: 8abe64476a5d3d1319dfa30dd7a06dc2bb541a0f
ms.sourcegitcommit: dfad244ba549702b649bfef3bb057e33f24a8fb2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/12/2020
ms.locfileid: "75904621"
---
# <a name="framework-design-guidelines"></a>Diretrizes de design de estrutura
Esta seção fornece diretrizes para a criação de bibliotecas que estendem e interagem com o .NET Framework. O objetivo é ajudar os designers de biblioteca a garantir a consistência da API e a facilidade de uso, fornecendo um modelo de programação unificado que é independente da linguagem de programação usada para desenvolvimento. Recomendamos que você siga essas diretrizes de design ao desenvolver classes e componentes que estendam o .NET Framework. O design de biblioteca inconsistente afeta negativamente a produtividade do desenvolvedor e não incentiva a adoção.  
  
 As diretrizes são organizadas como recomendações simples prefixadas com os termos `Do`, `Consider`, `Avoid`e `Do not`. Essas diretrizes destinam-se a ajudar os designers de biblioteca de classes a entender as compensações entre diferentes soluções. Pode haver situações em que um bom design de biblioteca exija que você viole essas diretrizes de design. Esses casos devem ser raros, e é importante que você tenha um motivo claro e convincente para sua decisão.  
  
 Essas diretrizes são extraídas das diretrizes de *design da estrutura de livros: convenções, idiomas e padrões para bibliotecas .net reutilizáveis, 2ª edição*, por Krzysztof Cwalina e Brad Abrams.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Diretrizes de nomenclatura](../../../docs/standard/design-guidelines/naming-guidelines.md)  
 Fornece diretrizes para nomear assemblies, namespaces, tipos e membros em bibliotecas de classes.  
  
 [Diretrizes de Design de tipo](../../../docs/standard/design-guidelines/type.md)  
 Fornece diretrizes para usar classes estáticas e abstratas, interfaces, enumerações, estruturas e outros tipos.  
  
 [Diretrizes de design de membro](../../../docs/standard/design-guidelines/member.md)  
 Fornece diretrizes para criar e usar propriedades, métodos, construtores, campos, eventos, operadores e parâmetros.  
  
 [Designer voltado para extensibilidade](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 Discute mecanismos de extensibilidade, como subclasses, uso de eventos, membros virtuais e retornos de chamada, e explica como escolher os mecanismos que melhor atendem aos requisitos da estrutura.  
  
 [Diretrizes de design para exceções](../../../docs/standard/design-guidelines/exceptions.md)  
 Descreve as diretrizes de design para criar, lançar e capturar exceções.  
  
 [Diretrizes de uso](../../../docs/standard/design-guidelines/usage-guidelines.md)  
 Descreve as diretrizes para o uso de tipos comuns, como matrizes, atributos e coleções, suporte à serialização e sobrecarga de operadores de igualdade.  
  
 [Padrões comuns de Design](../../../docs/standard/design-guidelines/common-design-patterns.md)  
 Fornece diretrizes para escolher e implementar propriedades de dependência.  
  
 *Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Veja também

- [Visão Geral](../../../docs/framework/get-started/overview.md)
- [Guia de desenvolvimento](../../../docs/framework/development-guide.md)
