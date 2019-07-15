---
ms.openlocfilehash: 64d540278544e74c46d46b77c97bccd26d4116dd
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67803245"
---
### <a name="opt-in-break-to-revert-from-different-45-sql-generation-to-simpler-40-sql-generation"></a><span data-ttu-id="4e6d1-101">Interrupção de aceitação será revertida de geração de SQL 4.5 diferente para geração de SQL 4.0 mais simples</span><span class="sxs-lookup"><span data-stu-id="4e6d1-101">Opt-in break to revert from different 4.5 SQL generation to simpler 4.0 SQL generation</span></span>

|   |   |
|---|---|
|<span data-ttu-id="4e6d1-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="4e6d1-102">Details</span></span>|<span data-ttu-id="4e6d1-103">As consultas que produzem instruções JOIN e contêm uma chamada para uma operação de limitação sem usar primeiro o OrderBy agora produzem um SQL mais simples.</span><span class="sxs-lookup"><span data-stu-id="4e6d1-103">Queries that produce JOIN statements and contain a call to a limiting operation without first using OrderBy now produce simpler SQL.</span></span> <span data-ttu-id="4e6d1-104">Após a atualização para o .NET Framework 4.5, essas consultas produziram SQLs mais complicados do que as versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="4e6d1-104">After upgrading to .NET Framework 4.5, these queries produced more complicated SQL than previous versions.</span></span>|
|<span data-ttu-id="4e6d1-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="4e6d1-105">Suggestion</span></span>|<span data-ttu-id="4e6d1-106">Esse recurso está desabilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="4e6d1-106">This feature is disabled by default.</span></span> <span data-ttu-id="4e6d1-107">Se Entity Framework gera instruções JOIN adicionais que causam a degradação do desempenho, pode-se habilitar esse recurso adicionando a seguinte entrada à seção <code>&lt;appSettings&gt;</code> do arquivo (app.config) de configuração da aplicação:</span><span class="sxs-lookup"><span data-stu-id="4e6d1-107">If Entity Framework generates extra JOIN statements that cause performance degradation, you can enable this feature by adding the following entry to the <code>&lt;appSettings&gt;</code> section of the application configuration (app.config) file:</span></span><pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyLimitOperations&quot; value=&quot;true&quot; /&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="4e6d1-108">Escopo</span><span class="sxs-lookup"><span data-stu-id="4e6d1-108">Scope</span></span>|<span data-ttu-id="4e6d1-109">Transparente</span><span class="sxs-lookup"><span data-stu-id="4e6d1-109">Transparent</span></span>|
|<span data-ttu-id="4e6d1-110">Versão</span><span class="sxs-lookup"><span data-stu-id="4e6d1-110">Version</span></span>|<span data-ttu-id="4e6d1-111">4.5.2</span><span class="sxs-lookup"><span data-stu-id="4e6d1-111">4.5.2</span></span>|
|<span data-ttu-id="4e6d1-112">Tipo</span><span class="sxs-lookup"><span data-stu-id="4e6d1-112">Type</span></span>|<span data-ttu-id="4e6d1-113">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="4e6d1-113">Runtime</span></span>|

