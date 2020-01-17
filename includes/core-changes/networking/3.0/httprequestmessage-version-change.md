---
ms.openlocfilehash: 9aff20e35469f9e786f0f790fda4ffaa04e76e64
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116426"
---
### <a name="default-value-of-httprequestmessageversion-changed-to-11"></a><span data-ttu-id="b30f6-101">Valor padrão de HttpRequestMessage. Version alterado para 1,1</span><span class="sxs-lookup"><span data-stu-id="b30f6-101">Default value of HttpRequestMessage.Version changed to 1.1</span></span>

<span data-ttu-id="b30f6-102">O valor padrão da propriedade <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> foi alterado de 2,0 para 1,1.</span><span class="sxs-lookup"><span data-stu-id="b30f6-102">The default value of the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property has changed from 2.0 to 1.1.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b30f6-103">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="b30f6-103">Version introduced</span></span>

<span data-ttu-id="b30f6-104">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="b30f6-104">.NET Core 3.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="b30f6-105">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="b30f6-105">Change description</span></span>

<span data-ttu-id="b30f6-106">No .NET Core 1,0 até 2,0, o valor padrão da propriedade <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> é 1,1.</span><span class="sxs-lookup"><span data-stu-id="b30f6-106">In .NET Core 1.0 through 2.0, the default value of the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property is 1.1.</span></span> <span data-ttu-id="b30f6-107">A partir do .NET Core 2,1, ele foi alterado para 2,1.</span><span class="sxs-lookup"><span data-stu-id="b30f6-107">Starting with .NET Core 2.1, it was changed to 2.1.</span></span>

<span data-ttu-id="b30f6-108">A partir do .NET Core 3,0, o número de versão padrão retornado pela propriedade <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> é mais uma vez 1,1.</span><span class="sxs-lookup"><span data-stu-id="b30f6-108">Starting with .NET Core 3.0, the default version number returned by the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property is once again 1.1.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b30f6-109">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="b30f6-109">Recommended action</span></span>

<span data-ttu-id="b30f6-110">Atualize seu código se ele depender da propriedade <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> retornando um valor padrão de 2,0.</span><span class="sxs-lookup"><span data-stu-id="b30f6-110">Update your code if it depends on the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property returning a default value of 2.0.</span></span>

#### <a name="category"></a><span data-ttu-id="b30f6-111">Categoria</span><span class="sxs-lookup"><span data-stu-id="b30f6-111">Category</span></span>

<span data-ttu-id="b30f6-112">Rede do</span><span class="sxs-lookup"><span data-stu-id="b30f6-112">Networking</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b30f6-113">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="b30f6-113">Affected APIs</span></span>

- <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName>

<!--
a def
### Affected APIs

- `P:System.Net.Http.HttpRequestMessage.Version`

-->
