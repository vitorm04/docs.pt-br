---
title: Como obter as informações de tipo e membro de um assembly
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- obtaining assembly information
- assemblies [.NET Framework], obtaining information from
ms.assetid: 348ae651-ccda-4f13-8eda-19e8337e9438
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 44fcded298f33a420a505900f618c1c67f4b9b6f
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50180056"
---
# <a name="how-to-obtain-type-and-member-information-from-an-assembly"></a><span data-ttu-id="15f8b-102">Como obter as informações de tipo e membro de um assembly</span><span class="sxs-lookup"><span data-stu-id="15f8b-102">How to: Obtain Type and Member Information from an Assembly</span></span>
<span data-ttu-id="15f8b-103">O namespace <xref:System.Reflection> contém vários métodos para obter informações de um assembly.</span><span class="sxs-lookup"><span data-stu-id="15f8b-103">The <xref:System.Reflection> namespace contains many methods for obtaining information from an assembly.</span></span> <span data-ttu-id="15f8b-104">Esta seção demonstra um desses métodos.</span><span class="sxs-lookup"><span data-stu-id="15f8b-104">This section demonstrates one of these methods.</span></span> <span data-ttu-id="15f8b-105">Para saber mais, veja [Visão geral da reflexão](../../../docs/framework/reflection-and-codedom/reflection.md).</span><span class="sxs-lookup"><span data-stu-id="15f8b-105">For additional information, see [Reflection Overview](../../../docs/framework/reflection-and-codedom/reflection.md).</span></span>  
  
 <span data-ttu-id="15f8b-106">O exemplo a seguir obtém informações de tipo e membro de um assembly.</span><span class="sxs-lookup"><span data-stu-id="15f8b-106">The following example obtains type and member information from an assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15f8b-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="15f8b-107">Example</span></span>  
 [!code-cpp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source6.cpp#8)]
 [!code-csharp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source6.cs#8)]
 [!code-vb[Conceptual.Types.ViewInfo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source6.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="15f8b-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="15f8b-108">See Also</span></span>  
- [<span data-ttu-id="15f8b-109">Programação com domínios do aplicativo</span><span class="sxs-lookup"><span data-stu-id="15f8b-109">Programming with Application Domains</span></span>](./application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="15f8b-110">Reflexão</span><span class="sxs-lookup"><span data-stu-id="15f8b-110">Reflection</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
- [<span data-ttu-id="15f8b-111">Usar domínios do aplicativo</span><span class="sxs-lookup"><span data-stu-id="15f8b-111">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)
