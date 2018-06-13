---
title: Membros protegidos
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- members [.NET Framework], protected
- protected members
- classes [.NET Framework], unsealed
- classes [.NET Framework], protected members
- unsealed classes
- customizing class behavior
ms.assetid: aa0b58ee-3956-494d-ab48-471ae5db8740
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5d4d334d9809f374442e19807d3b249a17a1d9df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571070"
---
# <a name="protected-members"></a>Membros protegidos
Membros protegidos por si só não fornecem nenhuma extensibilidade, mas eles podem tornar a extensibilidade por meio de subclassificação mais eficiente. Eles podem ser usados para expor as opções avançadas de personalização sem desnecessariamente complicar a principal interface pública.  
  
 Designers de Framework precisam ter cuidado com membros protegidos, porque o nome "protegido" pode dar uma falsa sensação de segurança. Qualquer pessoa que é capaz de subclasse de uma classe não lacrada e membros de acesso protegido e então as mesmas as práticas de codificação usadas para membros públicos se aplica a membros protegidos.  
  
 **✓ CONSIDERE** usando membros para a personalização avançada protegidos.  
  
 **FAZER ✓** tratar membros protegidos em classes não lacradas como public para fins de análise de segurança, documentação e compatibilidade.  
  
 Qualquer pessoa pode herdar de uma classe e acessar os membros protegidos.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)  
 [Designer voltado para extensibilidade](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
