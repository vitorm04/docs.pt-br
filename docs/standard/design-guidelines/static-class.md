---
title: "Design de classe estática"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- type design guidelines, static classes
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], static
- static classes [.NET Framework]
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d67c14d8-c4dd-443f-affb-4ccae677c9b6
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8c36bf5790d033eddb6bb7e0d910482143a9bcac
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="static-class-design"></a>Design de classe estática
Uma classe estática é definida como uma classe que contém somente os membros estáticos (obviamente além os membros de instância herdados de <xref:System.Object?displayProperty=nameWithType> e possivelmente um construtor particular). Alguns idiomas dão suporte interno para classes estáticas. No c# 2.0 e posterior, quando uma classe é declarada como estático, é lacrado, abstrata e nenhum membro de instância pode ser substituído ou declarado.  
  
 Classes static são um meio-termo entre design simples e orientada a objeto e simplicidade. Eles são usados para fornecer atalhos para outras operações (como <xref:System.IO.File?displayProperty=nameWithType>), os proprietários de métodos de extensão ou a funcionalidade para a qual um wrapper completo orientada a objeto é injustificado (como <xref:System.Environment?displayProperty=nameWithType>).  
  
 **FAZER ✓** usam classes estáticas com moderação.  
  
 Classes static devem ser usados apenas como classes de suporte para o núcleo orientada a objeto do framework.  
  
 **X não** tratar classes estáticas como um bucket diverso.  
  
 **X não** declarar ou substituir membros de instância em classes estáticas.  
  
 **FAZER ✓** declarar classes estáticas como lacrado, abstract e adicione um construtor de instância privada se a linguagem de programação não tem suporte interno para classes estáticas.  
  
 *Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de Design de tipo](../../../docs/standard/design-guidelines/type.md)  
 [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
