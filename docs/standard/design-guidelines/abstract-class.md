---
title: Design de classe abstrata
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, abstract classes
- abstract classes, design guidelines
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], abstract
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d3646e6d-5c1f-4922-8fb0-ec5effb30d60
author: KrzysztofCwalina
ms.openlocfilehash: 1982c7c97802dedd1d49c770be5a7ac00944cbfc
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53130857"
---
# <a name="abstract-class-design"></a>Design de classe abstrata
**X DO NOT** definir construtores internos públicos ou privados em tipos abstratos.  
  
 Construtores devem ser públicos somente se os usuários precisarão criar instâncias do tipo. Porque você não pode criar instâncias de um tipo abstrato, um tipo abstrato com um construtor público está incorretamente projetado e enganoso aos usuários.  
  
 **✓ DO** definir um construtor interno ou uma protegidos em classes abstratas.  
  
 Um construtor protegido é mais comum e simplesmente permite que a classe base fazer sua própria inicialização quando os subtipos são criados.  
  
 Um construtor interno pode ser usado para limitar as implementações concretas da classe abstrata para o assembly que define a classe.  
  
 **✓ DO** fornecer pelo menos um tipo concreto que herda de cada classe abstrata que você enviar.  
  
 Fazer isso ajuda a validar o design da classe abstrata. Por exemplo, <xref:System.IO.FileStream?displayProperty=nameWithType> é uma implementação do <xref:System.IO.Stream?displayProperty=nameWithType> classe abstrata.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpresso com permissão da Pearson Education, Inc. de [as diretrizes de Design do Framework: As convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008 pela Addison-Wesley Professional, como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também

- [Diretrizes de Design de tipo](../../../docs/standard/design-guidelines/type.md)  
- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
