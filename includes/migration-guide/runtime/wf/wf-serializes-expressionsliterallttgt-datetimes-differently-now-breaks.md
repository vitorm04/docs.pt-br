---
ms.openlocfilehash: 87013a04f7ff975e40a3c49c41c1c5acc2374066
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619875"
---
### <a name="wf-serializes-expressionsliterallttgt-datetimes-differently-now-breaks-custom-xaml-parsers"></a><span data-ttu-id="7c858-101">O WF agora serializa Expressions.Literal&lt;T&gt; DateTimes de modo diferente (interrompe analisadores XAML personalizados)</span><span class="sxs-lookup"><span data-stu-id="7c858-101">WF serializes Expressions.Literal&lt;T&gt; DateTimes differently now (breaks custom XAML parsers)</span></span>

#### <a name="details"></a><span data-ttu-id="7c858-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="7c858-102">Details</span></span>

<span data-ttu-id="7c858-103">O objeto <xref:System.Windows.Markup.ValueSerializer> associado converterá um objeto <xref:System.DateTime?displayProperty=fullName> ou <xref:System.DateTimeOffset?displayProperty=fullName> cujos componentes Second e <xref:System.DateTime.Millisecond?displayProperty=fullName> são diferentes de zero e (para um valor de <xref:System.DateTime?displayProperty=fullName>) cuja propriedade <xref:System.DateTime.Kind> não é Unspecified para a sintaxe de elemento de propriedade em vez de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="7c858-103">The associated <xref:System.Windows.Markup.ValueSerializer> object will convert a <xref:System.DateTime?displayProperty=fullName> or <xref:System.DateTimeOffset?displayProperty=fullName> object whose Second and <xref:System.DateTime.Millisecond?displayProperty=fullName> components are non-zero and (for a <xref:System.DateTime?displayProperty=fullName> value) whose <xref:System.DateTime.Kind> property is not Unspecified to property element syntax instead of a string.</span></span> <span data-ttu-id="7c858-104">Essa alteração permite que os valores <xref:System.DateTime?displayProperty=fullName> e <xref:System.DateTimeOffset?displayProperty=fullName> completem um ciclo.</span><span class="sxs-lookup"><span data-stu-id="7c858-104">This change allows <xref:System.DateTime?displayProperty=fullName> and <xref:System.DateTimeOffset?displayProperty=fullName> values to be round-tripped.</span></span> <span data-ttu-id="7c858-105">Os analisadores XAML personalizados que assumem que a entrada XAML está na sintaxe de atributo não funcionará corretamente.</span><span class="sxs-lookup"><span data-stu-id="7c858-105">Custom XAML parsers that assume that input XAML is in the attribute syntax will not function correctly.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7c858-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="7c858-106">Suggestion</span></span>

<span data-ttu-id="7c858-107">Essa alteração permite que os valores <xref:System.DateTime?displayProperty=fullName> e <xref:System.DateTimeOffset?displayProperty=fullName> completem um ciclo.</span><span class="sxs-lookup"><span data-stu-id="7c858-107">This change allows <xref:System.DateTime?displayProperty=fullName> and <xref:System.DateTimeOffset?displayProperty=fullName> values to be round-tripped.</span></span> <span data-ttu-id="7c858-108">Os analisadores XAML personalizados que assumem que a entrada XAML está na sintaxe de atributo não funcionará corretamente.</span><span class="sxs-lookup"><span data-stu-id="7c858-108">Custom XAML parsers that assume that input XAML is in the attribute syntax will not function correctly.</span></span>

| <span data-ttu-id="7c858-109">Name</span><span class="sxs-lookup"><span data-stu-id="7c858-109">Name</span></span>    | <span data-ttu-id="7c858-110">Valor</span><span class="sxs-lookup"><span data-stu-id="7c858-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7c858-111">Escopo</span><span class="sxs-lookup"><span data-stu-id="7c858-111">Scope</span></span>   |<span data-ttu-id="7c858-112">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="7c858-112">Edge</span></span>|
|<span data-ttu-id="7c858-113">Versão</span><span class="sxs-lookup"><span data-stu-id="7c858-113">Version</span></span>|<span data-ttu-id="7c858-114">4.5</span><span class="sxs-lookup"><span data-stu-id="7c858-114">4.5</span></span>|
|<span data-ttu-id="7c858-115">Type</span><span class="sxs-lookup"><span data-stu-id="7c858-115">Type</span></span>|<span data-ttu-id="7c858-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="7c858-116">Runtime</span></span>|
