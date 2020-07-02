---
ms.openlocfilehash: 424e8ff704b888aa3d2c1254ac712da4034f59b8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616020"
---
### <a name="obsoleteattribute-exports-as-both-obsoleteattribute-and-deprecatedattribute-in-winmd-scenarios"></a><span data-ttu-id="4ebaf-101">ObsoleteAttribute exporta ObsoleteAttribute e DeprecatedAttribute em cenários WinMD</span><span class="sxs-lookup"><span data-stu-id="4ebaf-101">ObsoleteAttribute exports as both ObsoleteAttribute and DeprecatedAttribute in WinMD scenarios</span></span>

#### <a name="details"></a><span data-ttu-id="4ebaf-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="4ebaf-102">Details</span></span>

<span data-ttu-id="4ebaf-103">Quando você cria uma biblioteca de Metadados do Windows (arquivo .winmd), o atributo <xref:System.ObsoleteAttribute?displayProperty=fullName> é exportado como <xref:System.ObsoleteAttribute?displayProperty=fullName> e [ Windows.Foundation.DeprecatedAttribute](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute).</span><span class="sxs-lookup"><span data-stu-id="4ebaf-103">When you create a Windows Metadata library (.winmd file), the <xref:System.ObsoleteAttribute?displayProperty=fullName> attribute is exported as both <xref:System.ObsoleteAttribute?displayProperty=fullName> and [Windows.Foundation.DeprecatedAttribute](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute).</span></span>

#### <a name="suggestion"></a><span data-ttu-id="4ebaf-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="4ebaf-104">Suggestion</span></span>

<span data-ttu-id="4ebaf-105">A recompilação do código-fonte existente que usa o atributo <xref:System.ObsoleteAttribute?displayProperty=fullName> pode gerar avisos durante o consumo desse código do C++/CX ou JavaScript. Não é recomendável aplicar <xref:System.ObsoleteAttribute?displayProperty=fullName> e [Windows.Foundation.DeprecatedAttribute](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute) ao código em assemblies gerenciados, isso pode gerar avisos de compilação.</span><span class="sxs-lookup"><span data-stu-id="4ebaf-105">Recompilation of existing source code that uses the <xref:System.ObsoleteAttribute?displayProperty=fullName> attribute may generate warnings when consuming that code from C++/CX or JavaScript.We do not recommend applying both <xref:System.ObsoleteAttribute?displayProperty=fullName> and [Windows.Foundation.DeprecatedAttribute](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute) to code in managed assemblies; it may result in build warnings.</span></span>

| <span data-ttu-id="4ebaf-106">Name</span><span class="sxs-lookup"><span data-stu-id="4ebaf-106">Name</span></span>    | <span data-ttu-id="4ebaf-107">Valor</span><span class="sxs-lookup"><span data-stu-id="4ebaf-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="4ebaf-108">Escopo</span><span class="sxs-lookup"><span data-stu-id="4ebaf-108">Scope</span></span>   | <span data-ttu-id="4ebaf-109">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="4ebaf-109">Edge</span></span>        |
| <span data-ttu-id="4ebaf-110">Versão</span><span class="sxs-lookup"><span data-stu-id="4ebaf-110">Version</span></span> | <span data-ttu-id="4ebaf-111">4.5.1</span><span class="sxs-lookup"><span data-stu-id="4ebaf-111">4.5.1</span></span>       |
| <span data-ttu-id="4ebaf-112">Type</span><span class="sxs-lookup"><span data-stu-id="4ebaf-112">Type</span></span>    | <span data-ttu-id="4ebaf-113">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="4ebaf-113">Retargeting</span></span> |
