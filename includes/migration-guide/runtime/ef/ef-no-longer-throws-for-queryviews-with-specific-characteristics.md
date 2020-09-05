---
ms.openlocfilehash: ceae6b85c14862b1b1183d01def0dda723ee0c2b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497925"
---
### <a name="ef-no-longer-throws-for-queryviews-with-specific-characteristics"></a><span data-ttu-id="64a8f-101">EF não gera mais para QueryViews com características específicas</span><span class="sxs-lookup"><span data-stu-id="64a8f-101">EF no longer throws for QueryViews with specific characteristics</span></span>

#### <a name="details"></a><span data-ttu-id="64a8f-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="64a8f-102">Details</span></span>

<span data-ttu-id="64a8f-103">O Entity Framework já não gera uma exceção <xref:System.StackOverflowException?displayProperty=fullName> quando um aplicativo executa uma consulta que envolve QueryView com uma propriedade de navegação de 0..1 que tenta incluir as entidades relacionadas como parte da consulta.</span><span class="sxs-lookup"><span data-stu-id="64a8f-103">Entity Framework no longer throws a <xref:System.StackOverflowException?displayProperty=fullName> exception when an app executes a query that involves a QueryView with a 0..1 navigation property that attempts to include the related entities as part of the query.</span></span> <span data-ttu-id="64a8f-104">Por exemplo, chamando <code>.Include(e =&gt; e.RelatedNavProp)</code>.</span><span class="sxs-lookup"><span data-stu-id="64a8f-104">For example, by calling <code>.Include(e =&gt; e.RelatedNavProp)</code>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="64a8f-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="64a8f-105">Suggestion</span></span>

<span data-ttu-id="64a8f-106">Essa alteração afeta apenas o código que usa relacionamentos de QueryViews com 1-0..1 ao executar consultas que chamam .Include.</span><span class="sxs-lookup"><span data-stu-id="64a8f-106">This change only affects code that uses QueryViews with 1-0..1 relationships when running queries that call .Include.</span></span> <span data-ttu-id="64a8f-107">Isso melhora a confiabilidade e deve ser transparente para quase todos os aplicativos.</span><span class="sxs-lookup"><span data-stu-id="64a8f-107">It improves reliability and should be transparent to almost all apps.</span></span> <span data-ttu-id="64a8f-108">No entanto, se causa um comportamento inesperado, é possível desabilitá-lo adicionando a seguinte entrada à seção <code>&lt;appSettings&gt;</code> do arquivo de configuração do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="64a8f-108">However, if it causes unexpected behavior, you can disable it by adding the following entry to the <code>&lt;appSettings&gt;</code> section of the app's configuration file:</span></span><pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyUserSpecifiedViews&quot; value=&quot;false&quot; /&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="64a8f-109">Nome</span><span class="sxs-lookup"><span data-stu-id="64a8f-109">Name</span></span>    | <span data-ttu-id="64a8f-110">Valor</span><span class="sxs-lookup"><span data-stu-id="64a8f-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="64a8f-111">Escopo</span><span class="sxs-lookup"><span data-stu-id="64a8f-111">Scope</span></span>   |<span data-ttu-id="64a8f-112">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="64a8f-112">Edge</span></span>|
|<span data-ttu-id="64a8f-113">Versão</span><span class="sxs-lookup"><span data-stu-id="64a8f-113">Version</span></span>|<span data-ttu-id="64a8f-114">4.5.2</span><span class="sxs-lookup"><span data-stu-id="64a8f-114">4.5.2</span></span>|
|<span data-ttu-id="64a8f-115">Tipo</span><span class="sxs-lookup"><span data-stu-id="64a8f-115">Type</span></span>|<span data-ttu-id="64a8f-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="64a8f-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="64a8f-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="64a8f-117">Affected APIs</span></span>

<span data-ttu-id="64a8f-118">Não detectável via análise de API.</span><span class="sxs-lookup"><span data-stu-id="64a8f-118">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
