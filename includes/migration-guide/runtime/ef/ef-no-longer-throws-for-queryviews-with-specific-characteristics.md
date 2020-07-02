---
ms.openlocfilehash: c6c897c13c84ce4b2be21da18e5702365518f286
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619799"
---
### <a name="ef-no-longer-throws-for-queryviews-with-specific-characteristics"></a><span data-ttu-id="7bab8-101">EF não gera mais para QueryViews com características específicas</span><span class="sxs-lookup"><span data-stu-id="7bab8-101">EF no longer throws for QueryViews with specific characteristics</span></span>

#### <a name="details"></a><span data-ttu-id="7bab8-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="7bab8-102">Details</span></span>

<span data-ttu-id="7bab8-103">O Entity Framework já não gera uma exceção <xref:System.StackOverflowException?displayProperty=fullName> quando um aplicativo executa uma consulta que envolve QueryView com uma propriedade de navegação de 0..1 que tenta incluir as entidades relacionadas como parte da consulta.</span><span class="sxs-lookup"><span data-stu-id="7bab8-103">Entity Framework no longer throws a <xref:System.StackOverflowException?displayProperty=fullName> exception when an app executes a query that involves a QueryView with a 0..1 navigation property that attempts to include the related entities as part of the query.</span></span> <span data-ttu-id="7bab8-104">Por exemplo, chamando <code>.Include(e =&gt; e.RelatedNavProp)</code>.</span><span class="sxs-lookup"><span data-stu-id="7bab8-104">For example, by calling <code>.Include(e =&gt; e.RelatedNavProp)</code>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7bab8-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="7bab8-105">Suggestion</span></span>

<span data-ttu-id="7bab8-106">Essa alteração afeta apenas o código que usa relacionamentos de QueryViews com 1-0..1 ao executar consultas que chamam .Include.</span><span class="sxs-lookup"><span data-stu-id="7bab8-106">This change only affects code that uses QueryViews with 1-0..1 relationships when running queries that call .Include.</span></span> <span data-ttu-id="7bab8-107">Isso melhora a confiabilidade e deve ser transparente para quase todos os aplicativos.</span><span class="sxs-lookup"><span data-stu-id="7bab8-107">It improves reliability and should be transparent to almost all apps.</span></span> <span data-ttu-id="7bab8-108">No entanto, se causa um comportamento inesperado, é possível desabilitá-lo adicionando a seguinte entrada à seção <code>&lt;appSettings&gt;</code> do arquivo de configuração do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="7bab8-108">However, if it causes unexpected behavior, you can disable it by adding the following entry to the <code>&lt;appSettings&gt;</code> section of the app's configuration file:</span></span><pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyUserSpecifiedViews&quot; value=&quot;false&quot; /&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="7bab8-109">Name</span><span class="sxs-lookup"><span data-stu-id="7bab8-109">Name</span></span>    | <span data-ttu-id="7bab8-110">Valor</span><span class="sxs-lookup"><span data-stu-id="7bab8-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7bab8-111">Escopo</span><span class="sxs-lookup"><span data-stu-id="7bab8-111">Scope</span></span>   |<span data-ttu-id="7bab8-112">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="7bab8-112">Edge</span></span>|
|<span data-ttu-id="7bab8-113">Versão</span><span class="sxs-lookup"><span data-stu-id="7bab8-113">Version</span></span>|<span data-ttu-id="7bab8-114">4.5.2</span><span class="sxs-lookup"><span data-stu-id="7bab8-114">4.5.2</span></span>|
|<span data-ttu-id="7bab8-115">Type</span><span class="sxs-lookup"><span data-stu-id="7bab8-115">Type</span></span>|<span data-ttu-id="7bab8-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="7bab8-116">Runtime</span></span>|
