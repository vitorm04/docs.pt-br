---
title: Designer voltado para extensibilidade
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- extending class libraries
- extensibility with class libraries in .NET Framework
- class library design guidelines [.NET Framework], extensibility
- class library extensibility [.NET Framework]
ms.assetid: 1cdb8740-871a-456c-9bd9-db96ca8d79b3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9c1690d0cdf1f57eaf0a794d6e71babfa4fa6425
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46485594"
---
# <a name="designing-for-extensibility"></a>Designer voltado para extensibilidade
Um aspecto importante da criação de uma estrutura é verificar se que a extensibilidade do framework foi considerada com cuidado. Isso exige que você compreenda os custos e benefícios associados com vários mecanismos de extensibilidade. Este capítulo ajuda você a decidir qual dos mecanismos de extensibilidade — a criação de subclasses, eventos, os membros virtuais, retornos de chamada e assim por diante — pode lidar melhor com os requisitos de sua estrutura.  
  
 Há várias maneiras para permitir a extensibilidade em estruturas. Eles variam do menos potentes, porém mais baratos para muito eficientes, mas caros. Qualquer necessidade de extensibilidade de determinado, você deve escolher o mecanismo de extensibilidade menos dispendioso que atenda aos requisitos. Tenha em mente que geralmente é possível adicionar mais extensibilidade posteriormente, mas nunca elevá-lo imediatamente sem introduzir alterações significativas.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Classes não seladas](../../../docs/standard/design-guidelines/unsealed-classes.md)  
 [Membros protegidos](../../../docs/standard/design-guidelines/protected-members.md)  
 [Eventos e retornos de chamada](../../../docs/standard/design-guidelines/events-and-callbacks.md)  
 [Membros virtuais](../../../docs/standard/design-guidelines/virtual-members.md)  
 [Abstrações (tipos e interfaces abstratos)](../../../docs/standard/design-guidelines/abstractions-abstract-types-and-interfaces.md)  
 [Classes base para implementar abstrações](../../../docs/standard/design-guidelines/base-classes-for-implementing-abstractions.md)  
 [Selar](../../../docs/standard/design-guidelines/sealing.md)  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também

- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
