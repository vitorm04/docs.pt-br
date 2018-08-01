---
title: Design de classe abstrata
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, abstract classes
- abstract classes, design guidelines
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], abstract
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d3646e6d-5c1f-4922-8fb0-ec5effb30d60
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 28052cc6848d77acbdf8e9381146ca6fb06c15d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33570519"
---
# <a name="abstract-class-design"></a>Design de classe abstrata
**X DO NOT** definir construtores internos públicos ou privados em tipos abstratos.  
  
 Construtores devem ser públicos somente se os usuários precisarão criar instâncias do tipo. Porque você não pode criar instâncias de um tipo abstrato, um tipo abstrato com um construtor público incorretamente é projetado e falsos para os usuários.  
  
 **✓ DO** definir um construtor interno ou uma protegidos em classes abstratas.  
  
 Um construtor protegido é mais comum e simplesmente permite que a classe base fazer seu próprios inicialização quando os subtipos são criados.  
  
 Um construtor interno pode ser usado para limitar as implementações concretas de classe abstrata para o assembly que define a classe.  
  
 **✓ DO** fornecer pelo menos um tipo concreto que herda de cada classe abstrata que você enviar.  
  
 Fazer isso ajuda a validar o design da classe abstrata. Por exemplo, <xref:System.IO.FileStream?displayProperty=nameWithType> é uma implementação de <xref:System.IO.Stream?displayProperty=nameWithType> classe abstrata.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de Design de tipo](../../../docs/standard/design-guidelines/type.md)  
 [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
