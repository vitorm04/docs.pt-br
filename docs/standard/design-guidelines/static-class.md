---
title: Design de classe estática
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, static classes
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], static
- static classes [.NET Framework]
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d67c14d8-c4dd-443f-affb-4ccae677c9b6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c3a0a51fc6055190f9a0189de2e17d98f88036ea
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44367353"
---
# <a name="static-class-design"></a>Design de classe estática
Uma classe estática é definida como uma classe que contém apenas membros estáticos (claro além os membros de instância herdados de <xref:System.Object?displayProperty=nameWithType> e, possivelmente, um construtor particular). Algumas linguagens fornecem suporte interno para classes estáticas. No c# 2.0 e posterior, quando uma classe é declarada como estático, é abstrato, selado, e nenhum membro de instância pode ser substituído ou declarado.  
  
 Classes estáticas são um meio-termo entre puro design orientado a objeto e simplicidade. Eles normalmente são usados para fornecer atalhos para outras operações (como <xref:System.IO.File?displayProperty=nameWithType>), os detentores dos métodos de extensão ou a funcionalidade para o qual um wrapper completo orientado a objeto é injustificado (como <xref:System.Environment?displayProperty=nameWithType>).  
  
 **✓ DO** usam classes estáticas com moderação.  
  
 Classes static devem ser usadas apenas como classes de suporte para o núcleo orientada a objeto do framework.  
  
 **X DO NOT** tratar classes estáticas como um bucket diverso.  
  
 **X DO NOT** declarar ou substituir membros de instância em classes estáticas.  
  
 **✓ DO** declarar classes estáticas como lacrado, abstract e adicione um construtor de instância privada se a linguagem de programação não tem suporte interno para classes estáticas.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também

- [Diretrizes de Design de tipo](../../../docs/standard/design-guidelines/type.md)  
- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
