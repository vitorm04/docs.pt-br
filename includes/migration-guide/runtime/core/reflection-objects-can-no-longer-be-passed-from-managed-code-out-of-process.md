---
ms.openlocfilehash: a54b17b2002bd0f85b8b47c5e37e040470d6c494
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621037"
---
### <a name="reflection-objects-can-no-longer-be-passed-from-managed-code-to-out-of-process-dcom-clients"></a><span data-ttu-id="33156-101">Os objetos Reflection não podem mais ser passados de código gerenciado para clientes DCOM fora do processo</span><span class="sxs-lookup"><span data-stu-id="33156-101">Reflection objects can no longer be passed from managed code to out-of-process DCOM clients</span></span>

#### <a name="details"></a><span data-ttu-id="33156-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="33156-102">Details</span></span>

<span data-ttu-id="33156-103">Os objetos Reflection não podem mais ser passados de código gerenciado para clientes DCOM fora do processo.</span><span class="sxs-lookup"><span data-stu-id="33156-103">Reflection objects can no longer be passed from managed code to out-of-process DCOM clients.</span></span> <span data-ttu-id="33156-104">Os seguintes tipos são afetados:</span><span class="sxs-lookup"><span data-stu-id="33156-104">The following types are affected:</span></span><ul><li><xref:System.Reflection.Assembly?displayProperty=fullName></li><li><span data-ttu-id="33156-105"><xref:System.Reflection.MemberInfo?displayProperty=fullName> (e seus tipos derivados, incluindo <xref:System.Reflection.FieldInfo?displayProperty=fullName>, <xref:System.Reflection.MethodInfo?displayProperty=fullName>, <xref:System.Type?displayProperty=fullName> e <xref:System.Reflection.TypeInfo?displayProperty=fullName>)</span><span class="sxs-lookup"><span data-stu-id="33156-105"><xref:System.Reflection.MemberInfo?displayProperty=fullName> (and its derived types, including <xref:System.Reflection.FieldInfo?displayProperty=fullName>, <xref:System.Reflection.MethodInfo?displayProperty=fullName>, <xref:System.Type?displayProperty=fullName>, and <xref:System.Reflection.TypeInfo?displayProperty=fullName>)</span></span></li><li><xref:System.Reflection.MethodBody?displayProperty=fullName></li><li><xref:System.Reflection.Module?displayProperty=fullName></li><li><span data-ttu-id="33156-106"><xref:System.Reflection.ParameterInfo?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="33156-106"><xref:System.Reflection.ParameterInfo?displayProperty=fullName>.</span></span></li></ul><span data-ttu-id="33156-107">Chamadas a <code>IMarshal</code> para o retorno do objeto <code>E_NOINTERFACE</code>.</span><span class="sxs-lookup"><span data-stu-id="33156-107">Calls to <code>IMarshal</code> for the object return <code>E_NOINTERFACE</code>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="33156-108">Sugestão</span><span class="sxs-lookup"><span data-stu-id="33156-108">Suggestion</span></span>

<span data-ttu-id="33156-109">Atualize o código de marshaling para trabalhar com objetos de não reflexão</span><span class="sxs-lookup"><span data-stu-id="33156-109">Update marshaling code to work with non-reflection objects</span></span>

| <span data-ttu-id="33156-110">Name</span><span class="sxs-lookup"><span data-stu-id="33156-110">Name</span></span>    | <span data-ttu-id="33156-111">Valor</span><span class="sxs-lookup"><span data-stu-id="33156-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="33156-112">Escopo</span><span class="sxs-lookup"><span data-stu-id="33156-112">Scope</span></span>   |<span data-ttu-id="33156-113">Secundária</span><span class="sxs-lookup"><span data-stu-id="33156-113">Minor</span></span>|
|<span data-ttu-id="33156-114">Versão</span><span class="sxs-lookup"><span data-stu-id="33156-114">Version</span></span>|<span data-ttu-id="33156-115">4.6</span><span class="sxs-lookup"><span data-stu-id="33156-115">4.6</span></span>|
|<span data-ttu-id="33156-116">Type</span><span class="sxs-lookup"><span data-stu-id="33156-116">Type</span></span>|<span data-ttu-id="33156-117">Runtime</span><span class="sxs-lookup"><span data-stu-id="33156-117">Runtime</span></span>|
