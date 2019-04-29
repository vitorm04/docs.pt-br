---
title: Diretrizes de Design de tipo
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines
- type design guidelines, about type design guidelines
- class library design guidelines [.NET Framework], type design guidelines
- types [.NET Framework], design guidelines
ms.assetid: 6b49314e-8bba-43ea-97ca-4e0255812f95
author: KrzysztofCwalina
ms.openlocfilehash: 16f2a095f461a406eedbd2b34b0c91d3ac43bbe5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61650096"
---
# <a name="type-design-guidelines"></a>Diretrizes de Design de tipo
Da perspectiva do CLR, há apenas duas categorias de tipos — fazer referência a tipos e tipos de valor — mas com a finalidade de uma discussão sobre o design de estrutura, dividimos tipos em grupos mais lógicos, cada um com suas próprias regras de design específico.  
  
 As classes são o caso geral de tipos de referência. Eles formam a maior parte dos tipos na maioria das estruturas. Classes deve sua popularidade, para o amplo conjunto de recursos orientados a objeto, que oferecem suporte e sua aplicabilidade geral. Classes base e classes abstratas são grupos lógicos especiais relacionados à extensibilidade.  
  
 Interfaces são tipos que podem ser implementados por tipos de referência e tipos de valor. Assim, elas servem como raízes de polimórficas hierarquias de tipos de referência e tipos de valor. Além disso, as interfaces podem ser usadas para simular a herança múltipla, que não tem suporte nativo pelo CLR.  
  
 Structs são o caso geral de tipos de valor e deve ser reservados para tipos de pequenos e simples, semelhantes a primitivos de linguagem.  
  
 Enumerações são um caso especial de tipos de valor usados para definir conjuntos de curtos de valores, como dias da semana, cores de console e assim por diante.  
  
 Classes estáticas são tipos que se destina a ser contêineres para membros estáticos. Normalmente, eles são usados para fornecer atalhos para outras operações.  
  
 Delegados, exceções, atributos, matrizes e coleções são todos os casos especiais de tipos de referência que se destina para usos específicos, e diretrizes para design e uso são discutidas em outro lugar neste livro.  
  
 **✓ DO** Certifique-se de que cada tipo é um conjunto bem definido de membros relacionados, não apenas um conjunto aleatório de funcionalidades relacionadas.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Escolhendo entre a classe e Struct](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)  
 [Design de classe abstrata](../../../docs/standard/design-guidelines/abstract-class.md)  
 [Design de classe estática](../../../docs/standard/design-guidelines/static-class.md)  
 [Design de interface](../../../docs/standard/design-guidelines/interface.md)  
 [Design de Struct](../../../docs/standard/design-guidelines/struct.md)  
 [Design de enumeração](../../../docs/standard/design-guidelines/enum.md)  
 [Tipos aninhados](../../../docs/standard/design-guidelines/nested-types.md)  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpresso com permissão da Pearson Education, Inc. de [as diretrizes de Design do Framework: As convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008 pela Addison-Wesley Professional, como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também

- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
