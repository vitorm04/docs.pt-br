---
title: Membros protegidos
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- members [.NET Framework], protected
- protected members
- classes [.NET Framework], unsealed
- classes [.NET Framework], protected members
- unsealed classes
- customizing class behavior
ms.assetid: aa0b58ee-3956-494d-ab48-471ae5db8740
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7c3aacd0f08641c01200f0b1791a78413a306590
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="protected-members"></a>Membros protegidos
Membros protegidos por si só não fornecem nenhuma extensibilidade, mas eles podem tornar a extensibilidade por meio de subclassificação mais eficiente. Eles podem ser usados para expor as opções avançadas de personalização sem desnecessariamente complicar a principal interface pública.  
  
 Designers de Framework precisam ter cuidado com membros protegidos, porque o nome "protegido" pode dar uma falsa sensação de segurança. Qualquer pessoa que é capaz de subclasse de uma classe não lacrada e membros de acesso protegido e então as mesmas as práticas de codificação usadas para membros públicos se aplica a membros protegidos.  
  
 **✓ CONSIDERE** usando membros para a personalização avançada protegidos.  
  
 **FAZER ✓** tratar membros protegidos em classes não lacradas como public para fins de análise de segurança, documentação e compatibilidade.  
  
 Qualquer pessoa pode herdar de uma classe e acessar os membros protegidos.  
  
 *Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)  
 [Criação de extensibilidade](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
