---
ms.openlocfilehash: 5ad9c494fd02059e05cc744aad3b06cfc9399995
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77451870"
---
### <a name="default-value-of-httprequestmessageversion-changed-to-11"></a><span data-ttu-id="8ad44-101">Valor padrão de HttpRequestMessage.Version alterado para 1.1</span><span class="sxs-lookup"><span data-stu-id="8ad44-101">Default value of HttpRequestMessage.Version changed to 1.1</span></span>

<span data-ttu-id="8ad44-102">O valor padrão <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> da propriedade passou de 2,0 para 1,1.</span><span class="sxs-lookup"><span data-stu-id="8ad44-102">The default value of the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property has changed from 2.0 to 1.1.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="8ad44-103">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="8ad44-103">Version introduced</span></span>

<span data-ttu-id="8ad44-104">3.0</span><span class="sxs-lookup"><span data-stu-id="8ad44-104">3.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="8ad44-105">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="8ad44-105">Change description</span></span>

<span data-ttu-id="8ad44-106">No .NET Core 1.0 a 2.0, <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> o valor padrão da propriedade é de 1,1.</span><span class="sxs-lookup"><span data-stu-id="8ad44-106">In .NET Core 1.0 through 2.0, the default value of the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property is 1.1.</span></span> <span data-ttu-id="8ad44-107">A partir do .NET Core 2.1, foi alterado para 2.1.</span><span class="sxs-lookup"><span data-stu-id="8ad44-107">Starting with .NET Core 2.1, it was changed to 2.1.</span></span>

<span data-ttu-id="8ad44-108">Começando com .NET Core 3.0, o número <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> da versão padrão retornado pela propriedade é novamente 1.1.</span><span class="sxs-lookup"><span data-stu-id="8ad44-108">Starting with .NET Core 3.0, the default version number returned by the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property is once again 1.1.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="8ad44-109">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="8ad44-109">Recommended action</span></span>

<span data-ttu-id="8ad44-110">Atualize seu código se <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> depender da propriedade que retornar um valor padrão de 2.0.</span><span class="sxs-lookup"><span data-stu-id="8ad44-110">Update your code if it depends on the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property returning a default value of 2.0.</span></span>

#### <a name="category"></a><span data-ttu-id="8ad44-111">Categoria</span><span class="sxs-lookup"><span data-stu-id="8ad44-111">Category</span></span>

<span data-ttu-id="8ad44-112">Rede</span><span class="sxs-lookup"><span data-stu-id="8ad44-112">Networking</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8ad44-113">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="8ad44-113">Affected APIs</span></span>

- <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Net.Http.HttpRequestMessage.Version`

-->
