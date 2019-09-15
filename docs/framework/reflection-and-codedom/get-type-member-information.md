---
title: 'Como: Obter informações de tipo e membro usando reflexão'
ms.date: 09/03/2019
helpviewer_keywords:
- reflection, obtaining member information
- types [.NET Framework], obtaining member information from
ms.assetid: 348ae651-ccda-4f13-8eda-19e8337e9438
author: rpetrusha
ms.author: ronpet
dev_langs:
- cpp
- csharp
- vb
ms.openlocfilehash: da71845ea276267220636cfd661465ea02b2b50d
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972917"
---
# <a name="how-to-get-type-and-member-information-by-using-reflection"></a>Como: Obter informações de tipo e membro usando reflexão
O <xref:System.Reflection> namespace contém muitos métodos para obter informações sobre tipos e seus membros. Este artigo demonstra um desses métodos, <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>. Para obter informações adicionais, consulte [visão geral de reflexão](reflection.md).
  
## <a name="example"></a>Exemplo

O exemplo a seguir obtém informações de tipo e membro usando reflexão:

[!code-cpp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cpp)]
[!code-csharp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cs)]
[!code-vb[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.vb)]

## <a name="see-also"></a>Consulte também

- [Programa com domínios de aplicativo](../app-domains/application-domains.md#programming-with-application-domains)
- [Reflexão](reflection.md)
- [Usar domínios de aplicativo](../app-domains/use.md)
