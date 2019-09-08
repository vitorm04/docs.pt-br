---
title: 'Mitigação: Verificações de dois-pontos no caminho'
ms.date: 03/30/2017
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a74c25a9bf4dd8b9ab86bd280881fe1a7999e1d5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70789984"
---
# <a name="mitigation-path-colon-checks"></a><span data-ttu-id="26903-102">Mitigação: Verificações de dois-pontos no caminho</span><span class="sxs-lookup"><span data-stu-id="26903-102">Mitigation: Path Colon Checks</span></span>
<span data-ttu-id="26903-103">Começando com os aplicativos direcionados ao .NET Framework 4.6.2, várias alterações foram feitas para dar suporte aos caminhos anteriormente sem suporte (em termos de comprimento e formato).</span><span class="sxs-lookup"><span data-stu-id="26903-103">Starting with apps that target the .NET Framework 4.6.2, a number of changes were made to support previously unsupported paths (both in terms of length and format).</span></span> <span data-ttu-id="26903-104">Em particular, as verificações da sintaxe adequada do separador de unidade (os dois-pontos) foram corrigidas.</span><span class="sxs-lookup"><span data-stu-id="26903-104">In particular, checks for the proper drive separator syntax (the colon) were made more correct.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="26903-105">Impacto</span><span class="sxs-lookup"><span data-stu-id="26903-105">Impact</span></span>  
 <span data-ttu-id="26903-106">Essas alterações bloqueiam alguns caminhos de URI aos quais esses os métodos <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> e <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> anteriormente davam suporte.</span><span class="sxs-lookup"><span data-stu-id="26903-106">These changes block some URI paths the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods previously supported.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="26903-107">Redução</span><span class="sxs-lookup"><span data-stu-id="26903-107">Mitigation</span></span>  
 <span data-ttu-id="26903-108">Para contornar o problema de um caminho aceitável anteriormente que não tem mais suporte pelos métodos <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> e <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType>, é possível fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="26903-108">To work around the problem of a previously acceptable path that is no longer supported by the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods, you can do the following:</span></span>  
  
- <span data-ttu-id="26903-109">Remova manualmente o esquema de uma URL.</span><span class="sxs-lookup"><span data-stu-id="26903-109">Manually remove the scheme from a URL.</span></span> <span data-ttu-id="26903-110">Por exemplo, remova `file://` de uma URL.</span><span class="sxs-lookup"><span data-stu-id="26903-110">For example, remove `file://` from a URL.</span></span>  
  
- <span data-ttu-id="26903-111">Passe o URI para um construtor <xref:System.Uri> e recupere o valor da propriedade <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="26903-111">Pass the URI to a <xref:System.Uri> constructor,  and retrieve the value of the <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> property.</span></span>  
  
- <span data-ttu-id="26903-112">Recuse a normalização do novo caminho definindo a opção `Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> como `true`.</span><span class="sxs-lookup"><span data-stu-id="26903-112">Opt out of the new path normalization by setting the `Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> switch to `true`.</span></span>  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
    </runtime>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="26903-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="26903-113">See also</span></span>

- [<span data-ttu-id="26903-114">Alterações de redirecionamento</span><span class="sxs-lookup"><span data-stu-id="26903-114">Retargeting Changes</span></span>](retargeting-changes-in-the-net-framework-4-6-2.md)
