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
# <a name="how-to-get-type-and-member-information-by-using-reflection"></a><span data-ttu-id="f76de-102">Como: obter informações de tipo e membro usando reflexão</span><span class="sxs-lookup"><span data-stu-id="f76de-102">How to: Get type and member information by using reflection</span></span>
<span data-ttu-id="f76de-103">O namespace <xref:System.Reflection> contém muitos métodos para obter informações sobre tipos e seus membros.</span><span class="sxs-lookup"><span data-stu-id="f76de-103">The <xref:System.Reflection> namespace contains many methods for obtaining information about types and their members.</span></span> <span data-ttu-id="f76de-104">Este artigo demonstra um desses métodos, <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f76de-104">This article demonstrates one of these methods, <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f76de-105">Para obter informações adicionais, consulte [visão geral de reflexão](reflection.md).</span><span class="sxs-lookup"><span data-stu-id="f76de-105">For additional information, see [Reflection overview](reflection.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="f76de-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f76de-106">Example</span></span>

<span data-ttu-id="f76de-107">O exemplo a seguir obtém informações de tipo e membro usando reflexão:</span><span class="sxs-lookup"><span data-stu-id="f76de-107">The following example obtains type and member information by using reflection:</span></span>

[!code-cpp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cpp)]
[!code-csharp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cs)]
[!code-vb[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.vb)]

## <a name="see-also"></a><span data-ttu-id="f76de-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f76de-108">See also</span></span>

- [<span data-ttu-id="f76de-109">Programa com domínios de aplicativo</span><span class="sxs-lookup"><span data-stu-id="f76de-109">Program with application domains</span></span>](../app-domains/application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="f76de-110">Reflexão</span><span class="sxs-lookup"><span data-stu-id="f76de-110">Reflection</span></span>](reflection.md)
- [<span data-ttu-id="f76de-111">Usar domínios de aplicativo</span><span class="sxs-lookup"><span data-stu-id="f76de-111">Use application domains</span></span>](../app-domains/use.md)
