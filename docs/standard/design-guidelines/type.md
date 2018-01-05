---
title: Diretrizes de Design de tipo
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- type design guidelines
- type design guidelines, about type design guidelines
- class library design guidelines [.NET Framework], type design guidelines
- types [.NET Framework], design guidelines
ms.assetid: 6b49314e-8bba-43ea-97ca-4e0255812f95
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6b02abef0180b6de82e26837863849cce35c994f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="type-design-guidelines"></a>Diretrizes de Design de tipo
Da perspectiva do CLR, há apenas duas categorias de tipos — referenciar tipos e tipos de valor —, mas com a finalidade de uma discussão sobre o design de estrutura, dividimos tipos em grupos mais lógicos, cada um com suas próprias regras de design específico.  
  
 As classes são o caso geral de tipos de referência. Eles formam a maior parte dos tipos na maioria das estruturas. Classes devem sua popularidade, para o sofisticado conjunto de recursos orientados a objeto que oferecem suporte e sua aplicabilidade geral. Classes base e classes abstratas são grupos lógicos especiais relacionados à extensibilidade.  
  
 Interfaces são tipos que podem ser implementados por tipos de referência e tipos de valor. Portanto, elas podem servir como raízes de polimórficas hierarquias de tipos de referência e tipos de valor. Além disso, as interfaces podem ser usadas para simular a herança múltipla, que não tem suporte nativo pelo CLR.  
  
 Estruturas são o caso geral de tipos de valor e devem ser reservadas para tipos de pequenos e simples, semelhantes a primitivos de linguagem.  
  
 Enumerações são um caso especial de tipos de valor usado para definir conjuntos de curtos de valores, como dias da semana, cores de console e assim por diante.  
  
 Classes static são tipos devem ser contêineres para membros estáticos. Eles são usados para fornecer atalhos para outras operações.  
  
 Delegados, exceções, atributos, matrizes e coleções são todos os casos especiais de tipos de referência que se destina para usos específicos e diretrizes de design e uso são discutidas em outro lugar neste livro.  
  
 **FAZER ✓** Certifique-se de que cada tipo é um conjunto bem definido de membros relacionados, não apenas um conjunto aleatório de funcionalidades relacionadas.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Escolhendo entre a classe e Struct](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)  
 [Design de classe abstrata](../../../docs/standard/design-guidelines/abstract-class.md)  
 [Design de classe estática](../../../docs/standard/design-guidelines/static-class.md)  
 [Design de interface](../../../docs/standard/design-guidelines/interface.md)  
 [Design de Struct](../../../docs/standard/design-guidelines/struct.md)  
 [Design de enumeração](../../../docs/standard/design-guidelines/enum.md)  
 [Tipos aninhados](../../../docs/standard/design-guidelines/nested-types.md)  
 *Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
