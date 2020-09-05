---
ms.openlocfilehash: 06424c4fa40343a881356c20003300f65e93efbb
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496464"
---
### <a name="wf-serializes-expressionsliterallttgt-datetimes-differently-now-breaks-custom-xaml-parsers"></a><span data-ttu-id="64ef6-101">O WF agora serializa Expressions.Literal&lt;T&gt; DateTimes de modo diferente (interrompe analisadores XAML personalizados)</span><span class="sxs-lookup"><span data-stu-id="64ef6-101">WF serializes Expressions.Literal&lt;T&gt; DateTimes differently now (breaks custom XAML parsers)</span></span>

#### <a name="details"></a><span data-ttu-id="64ef6-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="64ef6-102">Details</span></span>

<span data-ttu-id="64ef6-103">O objeto <xref:System.Windows.Markup.ValueSerializer> associado converterá um objeto <xref:System.DateTime?displayProperty=fullName> ou <xref:System.DateTimeOffset?displayProperty=fullName> cujos componentes Second e <xref:System.DateTime.Millisecond?displayProperty=fullName> são diferentes de zero e (para um valor de <xref:System.DateTime?displayProperty=fullName>) cuja propriedade <xref:System.DateTime.Kind> não é Unspecified para a sintaxe de elemento de propriedade em vez de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="64ef6-103">The associated <xref:System.Windows.Markup.ValueSerializer> object will convert a <xref:System.DateTime?displayProperty=fullName> or <xref:System.DateTimeOffset?displayProperty=fullName> object whose Second and <xref:System.DateTime.Millisecond?displayProperty=fullName> components are non-zero and (for a <xref:System.DateTime?displayProperty=fullName> value) whose <xref:System.DateTime.Kind> property is not Unspecified to property element syntax instead of a string.</span></span> <span data-ttu-id="64ef6-104">Essa alteração permite que os valores <xref:System.DateTime?displayProperty=fullName> e <xref:System.DateTimeOffset?displayProperty=fullName> completem um ciclo.</span><span class="sxs-lookup"><span data-stu-id="64ef6-104">This change allows <xref:System.DateTime?displayProperty=fullName> and <xref:System.DateTimeOffset?displayProperty=fullName> values to be round-tripped.</span></span> <span data-ttu-id="64ef6-105">Os analisadores XAML personalizados que assumem que a entrada XAML está na sintaxe de atributo não funcionará corretamente.</span><span class="sxs-lookup"><span data-stu-id="64ef6-105">Custom XAML parsers that assume that input XAML is in the attribute syntax will not function correctly.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="64ef6-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="64ef6-106">Suggestion</span></span>

<span data-ttu-id="64ef6-107">Essa alteração permite que os valores <xref:System.DateTime?displayProperty=fullName> e <xref:System.DateTimeOffset?displayProperty=fullName> completem um ciclo.</span><span class="sxs-lookup"><span data-stu-id="64ef6-107">This change allows <xref:System.DateTime?displayProperty=fullName> and <xref:System.DateTimeOffset?displayProperty=fullName> values to be round-tripped.</span></span> <span data-ttu-id="64ef6-108">Os analisadores XAML personalizados que assumem que a entrada XAML está na sintaxe de atributo não funcionará corretamente.</span><span class="sxs-lookup"><span data-stu-id="64ef6-108">Custom XAML parsers that assume that input XAML is in the attribute syntax will not function correctly.</span></span>

| <span data-ttu-id="64ef6-109">Nome</span><span class="sxs-lookup"><span data-stu-id="64ef6-109">Name</span></span>    | <span data-ttu-id="64ef6-110">Valor</span><span class="sxs-lookup"><span data-stu-id="64ef6-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="64ef6-111">Escopo</span><span class="sxs-lookup"><span data-stu-id="64ef6-111">Scope</span></span>   |<span data-ttu-id="64ef6-112">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="64ef6-112">Edge</span></span>|
|<span data-ttu-id="64ef6-113">Versão</span><span class="sxs-lookup"><span data-stu-id="64ef6-113">Version</span></span>|<span data-ttu-id="64ef6-114">4.5</span><span class="sxs-lookup"><span data-stu-id="64ef6-114">4.5</span></span>|
|<span data-ttu-id="64ef6-115">Tipo</span><span class="sxs-lookup"><span data-stu-id="64ef6-115">Type</span></span>|<span data-ttu-id="64ef6-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="64ef6-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="64ef6-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="64ef6-117">Affected APIs</span></span>

<span data-ttu-id="64ef6-118">Não detectável via análise de API.</span><span class="sxs-lookup"><span data-stu-id="64ef6-118">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
