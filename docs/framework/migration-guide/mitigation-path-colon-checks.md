---
title: 'Mitigação: verificações de dois-pontos no caminho'
description: Saiba mais sobre as alterações feitas no .NET Framework 4.6.2 para dar suporte a verificações da sintaxe do separador de unidade apropriada (os dois-pontos).
ms.date: 03/30/2017
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
ms.openlocfilehash: f32ee54f88bc4747fd0d8065b0dce06b151d1d9a
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475444"
---
# <a name="mitigation-path-colon-checks"></a><span data-ttu-id="5ecbb-103">Mitigação: verificações de dois-pontos no caminho</span><span class="sxs-lookup"><span data-stu-id="5ecbb-103">Mitigation: Path Colon Checks</span></span>
<span data-ttu-id="5ecbb-104">Começando com os aplicativos direcionados ao .NET Framework 4.6.2, várias alterações foram feitas para dar suporte aos caminhos anteriormente sem suporte (em termos de comprimento e formato).</span><span class="sxs-lookup"><span data-stu-id="5ecbb-104">Starting with apps that target the .NET Framework 4.6.2, a number of changes were made to support previously unsupported paths (both in terms of length and format).</span></span> <span data-ttu-id="5ecbb-105">Em particular, as verificações da sintaxe adequada do separador de unidade (os dois-pontos) foram corrigidas.</span><span class="sxs-lookup"><span data-stu-id="5ecbb-105">In particular, checks for the proper drive separator syntax (the colon) were made more correct.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="5ecbb-106">Impacto</span><span class="sxs-lookup"><span data-stu-id="5ecbb-106">Impact</span></span>  
 <span data-ttu-id="5ecbb-107">Essas alterações bloqueiam alguns caminhos de URI aos quais esses os métodos <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> e <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> anteriormente davam suporte.</span><span class="sxs-lookup"><span data-stu-id="5ecbb-107">These changes block some URI paths the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods previously supported.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="5ecbb-108">Atenuação</span><span class="sxs-lookup"><span data-stu-id="5ecbb-108">Mitigation</span></span>  
 <span data-ttu-id="5ecbb-109">Para contornar o problema de um caminho aceitável anteriormente que não tem mais suporte pelos métodos <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> e <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType>, é possível fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="5ecbb-109">To work around the problem of a previously acceptable path that is no longer supported by the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods, you can do the following:</span></span>  
  
- <span data-ttu-id="5ecbb-110">Remova manualmente o esquema de uma URL.</span><span class="sxs-lookup"><span data-stu-id="5ecbb-110">Manually remove the scheme from a URL.</span></span> <span data-ttu-id="5ecbb-111">Por exemplo, remova `file://` de uma URL.</span><span class="sxs-lookup"><span data-stu-id="5ecbb-111">For example, remove `file://` from a URL.</span></span>  
  
- <span data-ttu-id="5ecbb-112">Passe o URI para um construtor <xref:System.Uri> e recupere o valor da propriedade <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5ecbb-112">Pass the URI to a <xref:System.Uri> constructor,  and retrieve the value of the <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> property.</span></span>  
  
- <span data-ttu-id="5ecbb-113">Recuse a normalização do novo caminho definindo a opção `Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> como `true`.</span><span class="sxs-lookup"><span data-stu-id="5ecbb-113">Opt out of the new path normalization by setting the `Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> switch to `true`.</span></span>  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />
    </runtime>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="5ecbb-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5ecbb-114">See also</span></span>

- [<span data-ttu-id="5ecbb-115">Compatibilidade de aplicativos</span><span class="sxs-lookup"><span data-stu-id="5ecbb-115">Application compatibility</span></span>](application-compatibility.md)
