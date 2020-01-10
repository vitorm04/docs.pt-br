---
title: Designer voltado para extensibilidade
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- extending class libraries
- extensibility with class libraries in .NET Framework
- class library design guidelines [.NET Framework], extensibility
- class library extensibility [.NET Framework]
ms.assetid: 1cdb8740-871a-456c-9bd9-db96ca8d79b3
ms.openlocfilehash: cd5db2d1e299df1b3d0f706ebc507e6855b72505
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709459"
---
# <a name="designing-for-extensibility"></a>Designer voltado para extensibilidade
Um aspecto importante da criação de uma estrutura é garantir que a extensibilidade da estrutura tenha sido cuidadosamente considerada. Isso exige que você compreenda os custos e os benefícios associados a vários mecanismos de extensibilidade. Este capítulo ajuda você a decidir quais dos mecanismos de extensibilidade — a subclasse, os eventos, os membros virtuais, os retornos de chamada e assim por diante — pode atender melhor aos requisitos de sua estrutura.  
  
 Há várias maneiras de permitir a extensibilidade em estruturas. Elas variam de menos poderosas, mas menos dispendiosas a muito poderosas, mas caras. Para qualquer requisito de extensibilidade específico, você deve escolher o mecanismo de extensibilidade menos dispendioso que atenda aos requisitos. Tenha em mente que geralmente é possível adicionar mais extensibilidade posteriormente, mas você nunca pode descartar sem introduzir alterações significativas.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Classes não seladas](../../../docs/standard/design-guidelines/unsealed-classes.md)  
 [Membros protegidos](../../../docs/standard/design-guidelines/protected-members.md)  
 [Eventos e retornos de chamada](../../../docs/standard/design-guidelines/events-and-callbacks.md)  
 [Membros virtuais](../../../docs/standard/design-guidelines/virtual-members.md)  
 [Abstrações (tipos e interfaces abstratos)](../../../docs/standard/design-guidelines/abstractions-abstract-types-and-interfaces.md)  
 [Classes base para implementar abstrações](../../../docs/standard/design-guidelines/base-classes-for-implementing-abstractions.md)  
 [Selar](../../../docs/standard/design-guidelines/sealing.md)  
 *Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Veja também

- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
