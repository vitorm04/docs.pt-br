---
ms.openlocfilehash: b50a108d2efbfd3da0d690cb02537a12f766b26b
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237277"
---
### <a name="default-value-of-httprequestmessageversion-changed-to-11"></a><span data-ttu-id="4edc5-101">Valor padrão de HttpRequestMessage. Version alterado para 1,1</span><span class="sxs-lookup"><span data-stu-id="4edc5-101">Default value of HttpRequestMessage.Version changed to 1.1</span></span> 

<span data-ttu-id="4edc5-102">O valor padrão da propriedade <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> foi alterado de 2,0 para 1,1.</span><span class="sxs-lookup"><span data-stu-id="4edc5-102">The default value of the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property has changed from 2.0 to 1.1.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="4edc5-103">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="4edc5-103">Version introduced</span></span>

<span data-ttu-id="4edc5-104">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="4edc5-104">.NET Core 3.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="4edc5-105">Alterar descrição</span><span class="sxs-lookup"><span data-stu-id="4edc5-105">Change description</span></span>

<span data-ttu-id="4edc5-106">No .NET Core 1,0 até 2,0, o valor padrão da propriedade <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> é 1,1.</span><span class="sxs-lookup"><span data-stu-id="4edc5-106">In .NET Core 1.0 through 2.0, the default value of the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property is 1.1.</span></span> <span data-ttu-id="4edc5-107">A partir do .NET Core 2,1, ele foi alterado para 2,1.</span><span class="sxs-lookup"><span data-stu-id="4edc5-107">Starting with .NET Core 2.1, it was changed to 2.1.</span></span> 

<span data-ttu-id="4edc5-108">A partir do .NET Core 3,0, o número de versão padrão retornado pela propriedade <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> é mais uma vez 1,1.</span><span class="sxs-lookup"><span data-stu-id="4edc5-108">Starting with .NET Core 3.0, the default version number returned by the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property is once again 1.1.</span></span>
 
#### <a name="recommended-action"></a><span data-ttu-id="4edc5-109">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="4edc5-109">Recommended action</span></span>

<span data-ttu-id="4edc5-110">Atualize seu código se ele depender da propriedade <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> retornando um valor padrão de 2,0.</span><span class="sxs-lookup"><span data-stu-id="4edc5-110">Update your code if it depends on the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property returning a default value of 2.0.</span></span>

#### <a name="category"></a><span data-ttu-id="4edc5-111">Categoria</span><span class="sxs-lookup"><span data-stu-id="4edc5-111">Category</span></span>

<span data-ttu-id="4edc5-112">Rede</span><span class="sxs-lookup"><span data-stu-id="4edc5-112">Networking</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4edc5-113">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="4edc5-113">Affected APIs</span></span>

- <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName>

<!--
a def
### Affected APIs

- `P:System.Net.Http.HttpRequestMessage.Version`

-- >

