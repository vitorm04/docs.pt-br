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
ms.openlocfilehash: 4574dffc3f9dd1b60d655bfde33a4ddc1a81d350
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44140938"
---
# <a name="protected-members"></a>Membros protegidos
Membros protegidos por si só não fornecem todos extensibilidade, mas eles podem tornar mais poderosa extensibilidade por meio de subclasse. Eles podem ser usados para expor as opções avançadas de personalização sem complicar desnecessariamente a principal interface pública.  
  
 Designers do Framework precisam ter cuidado com membros protegidos porque o nome "protegido" pode fornecer uma falsa sensação de segurança. Qualquer pessoa é capaz de subclasse de uma classe não lacrada e membros protegido de acesso e, então todos os mesmos defensivas práticas de codificação usadas para os membros públicos se aplicam a membros protegidos.  
  
 **✓ CONSIDER** usando membros para a personalização avançada protegidos.  
  
 **✓ DO** tratar membros protegidos em classes não lacradas como public para fins de análise de segurança, documentação e compatibilidade.  
  
 Qualquer pessoa pode herdar de uma classe e acessar os membros protegidos.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também

- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)  
- [Designer voltado para extensibilidade](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
