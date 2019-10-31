---
title: 'Como: obter informações de tipo e membro usando reflexão'
ms.date: 09/03/2019
helpviewer_keywords:
- reflection, obtaining member information
- types [.NET Framework], obtaining member information from
ms.assetid: 348ae651-ccda-4f13-8eda-19e8337e9438
dev_langs:
- cpp
- csharp
- vb
ms.openlocfilehash: 9ffc173bbd0ed12eedea0c191f6d39baf181793a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130212"
---
# <a name="how-to-get-type-and-member-information-by-using-reflection"></a>Como: obter informações de tipo e membro usando reflexão
O namespace <xref:System.Reflection> contém muitos métodos para obter informações sobre tipos e seus membros. Este artigo demonstra um desses métodos, <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>. Para obter informações adicionais, consulte [visão geral de reflexão](reflection.md).
  
## <a name="example"></a>Exemplo

O exemplo a seguir obtém informações de tipo e membro usando reflexão:

[!code-cpp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cpp)]
[!code-csharp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cs)]
[!code-vb[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.vb)]

## <a name="see-also"></a>Consulte também

- [Programa com domínios de aplicativo](../app-domains/application-domains.md#programming-with-application-domains)
- [Reflexão](reflection.md)
- [Usar domínios de aplicativo](../app-domains/use.md)
