---
ms.openlocfilehash: 3e8601ba76dfb05e3d70b3af7440bd7e228768d0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621010"
---
### <a name="allow-unicode-in-uris-that-resemble-unc-shares"></a><span data-ttu-id="55902-101">Permitir Unicode em URIs semelhantes a compartilhamentos UNC</span><span class="sxs-lookup"><span data-stu-id="55902-101">Allow Unicode in URIs that resemble UNC shares</span></span>

#### <a name="details"></a><span data-ttu-id="55902-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="55902-102">Details</span></span>

<span data-ttu-id="55902-103">No <xref:System.Uri?displayProperty=fullName>, a criação de um URI de arquivo contendo um nome do compartilhamento UNC e caracteres Unicode não resultará mais em um URI com estado interno inválido.</span><span class="sxs-lookup"><span data-stu-id="55902-103">In <xref:System.Uri?displayProperty=fullName>, constructing a file URI containing both a UNC share name and Unicode characters will no longer result in a URI with invalid internal state.</span></span> <span data-ttu-id="55902-104">O comportamento será alterado somente quando todos os itens a seguir forem verdadeiros:</span><span class="sxs-lookup"><span data-stu-id="55902-104">The behavior will change only when all of the following are true:</span></span><ul><li><span data-ttu-id="55902-105">O URI tiver o esquema <code>file:</code> e for seguido por quatro ou mais barras.</span><span class="sxs-lookup"><span data-stu-id="55902-105">The URI has the scheme <code>file:</code> and is followed by four or more slashes.</span></span></li><li><span data-ttu-id="55902-106">O nome do host começar com um sublinhado ou outro símbolo não reservado.</span><span class="sxs-lookup"><span data-stu-id="55902-106">The host name begins with an underscore or other non-reserved symbol.</span></span></li><li><span data-ttu-id="55902-107">O URI contiver caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="55902-107">The URI contains Unicode characters.</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="55902-108">Sugestão</span><span class="sxs-lookup"><span data-stu-id="55902-108">Suggestion</span></span>

<span data-ttu-id="55902-109">Os aplicativos que funcionam com URIs que contêm Unicode de forma consistente podem ter aceitado o uso desse comportamento para não permitir referências a compartilhamentos UNC.</span><span class="sxs-lookup"><span data-stu-id="55902-109">Applications working with URIs consistently containing Unicode could have conceivably used this behavior to disallow references to UNC shares.</span></span> <span data-ttu-id="55902-110">Esses aplicativos devem usar <xref:System.Uri.IsUnc>.</span><span class="sxs-lookup"><span data-stu-id="55902-110">Those applications should use <xref:System.Uri.IsUnc> instead.</span></span>

| <span data-ttu-id="55902-111">Name</span><span class="sxs-lookup"><span data-stu-id="55902-111">Name</span></span>    | <span data-ttu-id="55902-112">Valor</span><span class="sxs-lookup"><span data-stu-id="55902-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="55902-113">Escopo</span><span class="sxs-lookup"><span data-stu-id="55902-113">Scope</span></span>   |<span data-ttu-id="55902-114">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="55902-114">Edge</span></span>|
|<span data-ttu-id="55902-115">Versão</span><span class="sxs-lookup"><span data-stu-id="55902-115">Version</span></span>|<span data-ttu-id="55902-116">4.7.2</span><span class="sxs-lookup"><span data-stu-id="55902-116">4.7.2</span></span>|
|<span data-ttu-id="55902-117">Type</span><span class="sxs-lookup"><span data-stu-id="55902-117">Type</span></span>|<span data-ttu-id="55902-118">Runtime</span><span class="sxs-lookup"><span data-stu-id="55902-118">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="55902-119">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="55902-119">Affected APIs</span></span>

-<xref:System.Uri?displayProperty=nameWithType></li></ul>|
