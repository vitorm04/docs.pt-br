---
title: 'Como: obter informações sobre tipo e membro usando reflexo'
description: Saiba como obter informações de tipo e membro com reflexão, usando o namespace System. Reflection.
ms.date: 09/03/2019
helpviewer_keywords:
- reflection, obtaining member information
- types [.NET Framework], obtaining member information from
ms.assetid: 348ae651-ccda-4f13-8eda-19e8337e9438
dev_langs:
- cpp
- csharp
- vb
ms.openlocfilehash: fa7af39c0addb328944a03236c26982301caf722
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865314"
---
# <a name="how-to-get-type-and-member-information-by-using-reflection"></a><span data-ttu-id="ac9ac-103">Como: obter informações sobre tipo e membro usando reflexo</span><span class="sxs-lookup"><span data-stu-id="ac9ac-103">How to: Get type and member information by using reflection</span></span>
<span data-ttu-id="ac9ac-104">O <xref:System.Reflection> namespace contém muitos métodos para obter informações sobre tipos e seus membros.</span><span class="sxs-lookup"><span data-stu-id="ac9ac-104">The <xref:System.Reflection> namespace contains many methods for obtaining information about types and their members.</span></span> <span data-ttu-id="ac9ac-105">Este artigo demonstra um desses métodos, <xref:System.Type.GetMembers%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="ac9ac-105">This article demonstrates one of these methods, <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ac9ac-106">Para obter informações adicionais, consulte [visão geral de reflexão](reflection.md).</span><span class="sxs-lookup"><span data-stu-id="ac9ac-106">For additional information, see [Reflection overview](reflection.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="ac9ac-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ac9ac-107">Example</span></span>

<span data-ttu-id="ac9ac-108">O exemplo a seguir obtém informações de tipo e membro usando reflexão:</span><span class="sxs-lookup"><span data-stu-id="ac9ac-108">The following example obtains type and member information by using reflection:</span></span>

[!code-cpp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cpp)]
[!code-csharp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cs)]
[!code-vb[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.vb)]

## <a name="see-also"></a><span data-ttu-id="ac9ac-109">Veja também</span><span class="sxs-lookup"><span data-stu-id="ac9ac-109">See also</span></span>

- [<span data-ttu-id="ac9ac-110">Programa com domínios de aplicativo</span><span class="sxs-lookup"><span data-stu-id="ac9ac-110">Program with application domains</span></span>](../app-domains/application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="ac9ac-111">Reflexão</span><span class="sxs-lookup"><span data-stu-id="ac9ac-111">Reflection</span></span>](reflection.md)
- [<span data-ttu-id="ac9ac-112">Usar domínios de aplicativo</span><span class="sxs-lookup"><span data-stu-id="ac9ac-112">Use application domains</span></span>](../app-domains/use.md)
