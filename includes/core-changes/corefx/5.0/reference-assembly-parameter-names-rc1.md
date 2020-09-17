---
ms.openlocfilehash: 760c9ce2427bc1f5e9276e66ecb6d2cf2ed83c16
ms.sourcegitcommit: a8730298170b8d96b4272e0c3dfc9819c606947b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90738808"
---
### <a name="parameter-names-changed-in-rc1"></a><span data-ttu-id="cfeae-101">Nomes de parâmetros alterados no RC1</span><span class="sxs-lookup"><span data-stu-id="cfeae-101">Parameter names changed in RC1</span></span>

<span data-ttu-id="cfeae-102">Alguns nomes de parâmetro de assembly de referência foram alterados para corresponder nomes de parâmetro nos assemblies de implementação.</span><span class="sxs-lookup"><span data-stu-id="cfeae-102">Some reference assembly parameter names have changed to match parameter names in the implementation assemblies.</span></span>

#### <a name="change-description"></a><span data-ttu-id="cfeae-103">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="cfeae-103">Change description</span></span>

<span data-ttu-id="cfeae-104">Nas versões anteriores do .NET 5,0 Preview e RC, alguns nomes de parâmetros de [assembly de referência](../../../../docs/standard/assembly/reference-assemblies.md) são diferentes para seus parâmetros correspondentes no assembly de implementação.</span><span class="sxs-lookup"><span data-stu-id="cfeae-104">In previous .NET 5.0 preview and RC versions, some [reference assembly](../../../../docs/standard/assembly/reference-assemblies.md) parameter names are different to their corresponding parameters in the implementation assembly.</span></span> <span data-ttu-id="cfeae-105">Isso pode causar problemas ao usar argumentos nomeados e reflexão.</span><span class="sxs-lookup"><span data-stu-id="cfeae-105">This can cause problems while using named arguments and reflection.</span></span>

<span data-ttu-id="cfeae-106">No .NET 5,0 RC2, esses nomes de parâmetro incompatíveis foram atualizados nos assemblies de referência para corresponder exatamente aos nomes de parâmetro correspondentes nos assemblies de implementação.</span><span class="sxs-lookup"><span data-stu-id="cfeae-106">In .NET 5.0 RC2, these mismatched parameter names were updated in the reference assemblies to exactly match the corresponding parameter names in the implementation assemblies.</span></span>

<span data-ttu-id="cfeae-107">A tabela a seguir mostra as APIs e os nomes de parâmetro que foram alterados.</span><span class="sxs-lookup"><span data-stu-id="cfeae-107">The following table shows the APIs and parameter names that changed.</span></span>

| <span data-ttu-id="cfeae-108">API</span><span class="sxs-lookup"><span data-stu-id="cfeae-108">API</span></span> | <span data-ttu-id="cfeae-109">Nome do parâmetro antigo</span><span class="sxs-lookup"><span data-stu-id="cfeae-109">Old parameter name</span></span> | <span data-ttu-id="cfeae-110">Nome do novo parâmetro</span><span class="sxs-lookup"><span data-stu-id="cfeae-110">New parameter name</span></span> |
| - | - | - |
| <xref:System.Diagnostics.ActivityContext.%23ctor(System.Diagnostics.ActivityTraceId,System.Diagnostics.ActivitySpanId,System.Diagnostics.ActivityTraceFlags,System.String,System.Boolean)> | `traceOptions` | `traceFlags` |
| <xref:System.Globalization.CompareInfo.IsPrefix(System.ReadOnlySpan{System.Char},System.ReadOnlySpan{System.Char},System.Globalization.CompareOptions,System.Int32@)?displayProperty=nameWithType> | `suffix` | `prefix` |

#### <a name="reason-for-change"></a><span data-ttu-id="cfeae-111">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="cfeae-111">Reason for change</span></span>

<span data-ttu-id="cfeae-112">Os nomes de parâmetro foram alterados quanto à consistência e para evitar falhas ao usar argumentos nomeados e reflexão.</span><span class="sxs-lookup"><span data-stu-id="cfeae-112">The parameter names were changed for consistency and to avoid failures when using named arguments and reflection.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="cfeae-113">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="cfeae-113">Version introduced</span></span>

<span data-ttu-id="cfeae-114">5,0 RC2</span><span class="sxs-lookup"><span data-stu-id="cfeae-114">5.0 RC2</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="cfeae-115">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="cfeae-115">Recommended action</span></span>

<span data-ttu-id="cfeae-116">Se você encontrar um erro de compilador devido a uma alteração de nome de parâmetro, atualize o nome do parâmetro de acordo.</span><span class="sxs-lookup"><span data-stu-id="cfeae-116">If you encounter a compiler error due to a parameter name change, update the parameter name accordingly.</span></span>

#### <a name="category"></a><span data-ttu-id="cfeae-117">Categoria</span><span class="sxs-lookup"><span data-stu-id="cfeae-117">Category</span></span>

<span data-ttu-id="cfeae-118">Bibliotecas principais do .NET</span><span class="sxs-lookup"><span data-stu-id="cfeae-118">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="cfeae-119">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="cfeae-119">Affected APIs</span></span>

- <xref:System.Diagnostics.ActivityContext.%23ctor(System.Diagnostics.ActivityTraceId,System.Diagnostics.ActivitySpanId,System.Diagnostics.ActivityTraceFlags,System.String,System.Boolean)>
- <xref:System.Globalization.CompareInfo.IsPrefix(System.ReadOnlySpan{System.Char},System.ReadOnlySpan{System.Char},System.Globalization.CompareOptions,System.Int32@)?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Diagnostics.ActivityContext.#ctor(System.Diagnostics.ActivityTraceId,System.Diagnostics.ActivitySpanId,System.Diagnostics.ActivityTraceFlags,System.String,System.Boolean)`
- `M:System.Globalization.CompareInfo.IsPrefix(System.ReadOnlySpan{System.Char},System.ReadOnlySpan{System.Char},System.Globalization.CompareOptions,System.Int32@)`

-->
