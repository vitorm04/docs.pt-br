---
ms.openlocfilehash: f011f6ebe0fa85a59f3e69c93bba9eddc4c1689b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497063"
---
### <a name="reflection-objects-can-no-longer-be-passed-from-managed-code-to-out-of-process-dcom-clients"></a><span data-ttu-id="ba017-101">Os objetos Reflection não podem mais ser passados de código gerenciado para clientes DCOM fora do processo</span><span class="sxs-lookup"><span data-stu-id="ba017-101">Reflection objects can no longer be passed from managed code to out-of-process DCOM clients</span></span>

#### <a name="details"></a><span data-ttu-id="ba017-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="ba017-102">Details</span></span>

<span data-ttu-id="ba017-103">Os objetos Reflection não podem mais ser passados de código gerenciado para clientes DCOM fora do processo.</span><span class="sxs-lookup"><span data-stu-id="ba017-103">Reflection objects can no longer be passed from managed code to out-of-process DCOM clients.</span></span> <span data-ttu-id="ba017-104">Os seguintes tipos são afetados:</span><span class="sxs-lookup"><span data-stu-id="ba017-104">The following types are affected:</span></span>

- <xref:System.Reflection.Assembly?displayProperty=fullName>
- <span data-ttu-id="ba017-105"><xref:System.Reflection.MemberInfo?displayProperty=fullName> (e seus tipos derivados, incluindo <xref:System.Reflection.FieldInfo?displayProperty=fullName>, <xref:System.Reflection.MethodInfo?displayProperty=fullName>, <xref:System.Type?displayProperty=fullName> e <xref:System.Reflection.TypeInfo?displayProperty=fullName>)</span><span class="sxs-lookup"><span data-stu-id="ba017-105"><xref:System.Reflection.MemberInfo?displayProperty=fullName> (and its derived types, including <xref:System.Reflection.FieldInfo?displayProperty=fullName>, <xref:System.Reflection.MethodInfo?displayProperty=fullName>, <xref:System.Type?displayProperty=fullName>, and <xref:System.Reflection.TypeInfo?displayProperty=fullName>)</span></span>
- <xref:System.Reflection.MethodBody?displayProperty=fullName>
- <xref:System.Reflection.Module?displayProperty=fullName>
- <xref:System.Reflection.ParameterInfo?displayProperty=fullName>

<span data-ttu-id="ba017-106">Chamadas a <code>IMarshal</code> para o retorno do objeto <code>E_NOINTERFACE</code>.</span><span class="sxs-lookup"><span data-stu-id="ba017-106">Calls to <code>IMarshal</code> for the object return <code>E_NOINTERFACE</code>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ba017-107">Sugestão</span><span class="sxs-lookup"><span data-stu-id="ba017-107">Suggestion</span></span>

<span data-ttu-id="ba017-108">Atualize o código de marshaling para trabalhar com objetos que não são de reflexão.</span><span class="sxs-lookup"><span data-stu-id="ba017-108">Update marshaling code to work with non-reflection objects.</span></span>

| <span data-ttu-id="ba017-109">Nome</span><span class="sxs-lookup"><span data-stu-id="ba017-109">Name</span></span>    | <span data-ttu-id="ba017-110">Valor</span><span class="sxs-lookup"><span data-stu-id="ba017-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ba017-111">Escopo</span><span class="sxs-lookup"><span data-stu-id="ba017-111">Scope</span></span>   |<span data-ttu-id="ba017-112">Secundária</span><span class="sxs-lookup"><span data-stu-id="ba017-112">Minor</span></span>|
|<span data-ttu-id="ba017-113">Versão</span><span class="sxs-lookup"><span data-stu-id="ba017-113">Version</span></span>|<span data-ttu-id="ba017-114">4.6</span><span class="sxs-lookup"><span data-stu-id="ba017-114">4.6</span></span>|
|<span data-ttu-id="ba017-115">Tipo</span><span class="sxs-lookup"><span data-stu-id="ba017-115">Type</span></span>|<span data-ttu-id="ba017-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="ba017-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="ba017-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="ba017-117">Affected APIs</span></span>

- <xref:System.Reflection.Assembly?displayProperty=fullName>
- <xref:System.Reflection.FieldInfo?displayProperty=fullName>
- <xref:System.Reflection.MemberInfo?displayProperty=fullName>
- <xref:System.Reflection.MethodBody?displayProperty=fullName>
- <xref:System.Reflection.MethodInfo?displayProperty=fullName>
- <xref:System.Reflection.Module?displayProperty=fullName>
- <xref:System.Reflection.ParameterInfo?displayProperty=fullName>
- <xref:System.Reflection.TypeInfo?displayProperty=fullName>
- <xref:System.Type?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Reflection.Assembly`
- `T:System.Reflection.FieldInfo`
- `T:System.Reflection.MemberInfo`
- `T:System.Reflection.MethodBody`
- `T:System.Reflection.MethodInfo`
- `T:System.Reflection.Module`
- `T:System.Reflection.ParameterInfo`
- `T:System.Reflection.TypeInfo`
- `T:System.Type`

-->
