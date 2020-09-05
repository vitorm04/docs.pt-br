---
ms.openlocfilehash: 8dc1b4d94d01813a8124d1340b50fa78a9b157f8
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497415"
---
### <a name="resizing-a-grid-can-hang"></a><span data-ttu-id="27593-101">Redimensionar uma grade pode causar travamento</span><span class="sxs-lookup"><span data-stu-id="27593-101">Resizing a Grid can hang</span></span>

#### <a name="details"></a><span data-ttu-id="27593-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="27593-102">Details</span></span>

<span data-ttu-id="27593-103">Um loop infinito pode ocorrer durante o layout de um <code>T:System.Windows.Controls.Grid</code> nas seguintes circunstâncias:</span><span class="sxs-lookup"><span data-stu-id="27593-103">An infinite loop can occur during layout of a <code>T:System.Windows.Controls.Grid</code> under the following circumstances:</span></span><ul><li><span data-ttu-id="27593-104">As definições de linha contêm duas \* linhas, declarando um MinHeight e um MaxHeight.</span><span class="sxs-lookup"><span data-stu-id="27593-104">Row definitions contain two \*-rows, both declaring a MinHeight and a MaxHeight.</span></span></li><li><span data-ttu-id="27593-105">O conteúdo das \* -Rows não excede o MaxHeight correspondente</span><span class="sxs-lookup"><span data-stu-id="27593-105">Content of the \*-rows doesn't exceed the corresponding MaxHeight</span></span></li><li><span data-ttu-id="27593-106">A altura disponível da grade é ultrapassada pelo primeiro MinHeight (além de qualquer outra linha fixa ou automática)</span><span class="sxs-lookup"><span data-stu-id="27593-106">The Grid's available height is exceeded by the first MinHeight (plus any other fixed or Auto rows)</span></span></li><li><span data-ttu-id="27593-107">O aplicativo é direcionado ao .NET Framework 4.7 ou aceita o algoritmo de alocação do 4.7 definindo <code>Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=false</code></span><span class="sxs-lookup"><span data-stu-id="27593-107">The app targets .NET Framework 4.7, or opts in to the 4.7 allocation algorithm by setting <code>Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=false</code></span></span></li></ul><span data-ttu-id="27593-108">O loop também aconteceria com mais de duas linhas, ou no caso análogo para colunas.</span><span class="sxs-lookup"><span data-stu-id="27593-108">The loop would also happen with more than two rows, or in the analogous case for columns.</span></span> <span data-ttu-id="27593-109">O problema foi corrigido no .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="27593-109">The issue is fixed in .NET Framework 4.7.1.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="27593-110">Sugestão</span><span class="sxs-lookup"><span data-stu-id="27593-110">Suggestion</span></span>

<span data-ttu-id="27593-111">Atualizar para o .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="27593-111">Upgrade to .NET Framework 4.7.1.</span></span>  <span data-ttu-id="27593-112">Como alternativa, se não precisar do algoritmo de alocação do 4.7, você poderá usar a seguinte configuração:</span><span class="sxs-lookup"><span data-stu-id="27593-112">Alternatively, if you don't need the 4.7 allocation algorithm you can use the following configuration setting:</span></span><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="27593-113">Nome</span><span class="sxs-lookup"><span data-stu-id="27593-113">Name</span></span>    | <span data-ttu-id="27593-114">Valor</span><span class="sxs-lookup"><span data-stu-id="27593-114">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="27593-115">Escopo</span><span class="sxs-lookup"><span data-stu-id="27593-115">Scope</span></span>   |<span data-ttu-id="27593-116">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="27593-116">Edge</span></span>|
|<span data-ttu-id="27593-117">Versão</span><span class="sxs-lookup"><span data-stu-id="27593-117">Version</span></span>|<span data-ttu-id="27593-118">4.7</span><span class="sxs-lookup"><span data-stu-id="27593-118">4.7</span></span>|
|<span data-ttu-id="27593-119">Tipo</span><span class="sxs-lookup"><span data-stu-id="27593-119">Type</span></span>|<span data-ttu-id="27593-120">Runtime</span><span class="sxs-lookup"><span data-stu-id="27593-120">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="27593-121">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="27593-121">Affected APIs</span></span>

<span data-ttu-id="27593-122">Não detectável via análise de API.</span><span class="sxs-lookup"><span data-stu-id="27593-122">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
