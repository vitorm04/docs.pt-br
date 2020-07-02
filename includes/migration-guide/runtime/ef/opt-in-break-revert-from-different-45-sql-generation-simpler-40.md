---
ms.openlocfilehash: 22b5abbe769733e8d5ca3e78dd9e6e13b2363737
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619796"
---
### <a name="opt-in-break-to-revert-from-different-45-sql-generation-to-simpler-40-sql-generation"></a><span data-ttu-id="91a9f-101">Interrupção de aceitação será revertida de geração de SQL 4.5 diferente para geração de SQL 4.0 mais simples</span><span class="sxs-lookup"><span data-stu-id="91a9f-101">Opt-in break to revert from different 4.5 SQL generation to simpler 4.0 SQL generation</span></span>

#### <a name="details"></a><span data-ttu-id="91a9f-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="91a9f-102">Details</span></span>

<span data-ttu-id="91a9f-103">As consultas que produzem instruções JOIN e contêm uma chamada para uma operação de limitação sem usar primeiro o OrderBy agora produzem um SQL mais simples.</span><span class="sxs-lookup"><span data-stu-id="91a9f-103">Queries that produce JOIN statements and contain a call to a limiting operation without first using OrderBy now produce simpler SQL.</span></span> <span data-ttu-id="91a9f-104">Após a atualização para o .NET Framework 4.5, essas consultas produziram SQLs mais complicados do que as versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="91a9f-104">After upgrading to .NET Framework 4.5, these queries produced more complicated SQL than previous versions.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="91a9f-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="91a9f-105">Suggestion</span></span>

<span data-ttu-id="91a9f-106">Por padrão, esse recurso está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="91a9f-106">This feature is disabled by default.</span></span> <span data-ttu-id="91a9f-107">Se Entity Framework gera instruções JOIN adicionais que causam a degradação do desempenho, pode-se habilitar esse recurso adicionando a seguinte entrada à seção <code>&lt;appSettings&gt;</code> do arquivo (app.config) de configuração da aplicação:</span><span class="sxs-lookup"><span data-stu-id="91a9f-107">If Entity Framework generates extra JOIN statements that cause performance degradation, you can enable this feature by adding the following entry to the <code>&lt;appSettings&gt;</code> section of the application configuration (app.config) file:</span></span><pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyLimitOperations&quot; value=&quot;true&quot; /&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="91a9f-108">Name</span><span class="sxs-lookup"><span data-stu-id="91a9f-108">Name</span></span>    | <span data-ttu-id="91a9f-109">Valor</span><span class="sxs-lookup"><span data-stu-id="91a9f-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="91a9f-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="91a9f-110">Scope</span></span>   |<span data-ttu-id="91a9f-111">Transparente</span><span class="sxs-lookup"><span data-stu-id="91a9f-111">Transparent</span></span>|
|<span data-ttu-id="91a9f-112">Versão</span><span class="sxs-lookup"><span data-stu-id="91a9f-112">Version</span></span>|<span data-ttu-id="91a9f-113">4.5.2</span><span class="sxs-lookup"><span data-stu-id="91a9f-113">4.5.2</span></span>|
|<span data-ttu-id="91a9f-114">Type</span><span class="sxs-lookup"><span data-stu-id="91a9f-114">Type</span></span>|<span data-ttu-id="91a9f-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="91a9f-115">Runtime</span></span>|
