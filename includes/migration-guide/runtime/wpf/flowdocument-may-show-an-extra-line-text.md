---
ms.openlocfilehash: a61005e317020c47a283dae292236624ec6057ce
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497379"
---
### <a name="flowdocument-may-show-an-extra-line-of-text"></a><span data-ttu-id="75aa4-101">FlowDocument pode mostrar uma linha extra de texto</span><span class="sxs-lookup"><span data-stu-id="75aa4-101">FlowDocument may show an extra line of text</span></span>

#### <a name="details"></a><span data-ttu-id="75aa4-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="75aa4-102">Details</span></span>

<span data-ttu-id="75aa4-103">Em alguns casos, um elemento <xref:System.Windows.Documents.FlowDocument> exibirá uma linha de texto extra ao ser executado no .NET Framework 4.5, em comparação a como ele foi exibido quando executado no .NET Framework 4.0.</span><span class="sxs-lookup"><span data-stu-id="75aa4-103">In some cases, a <xref:System.Windows.Documents.FlowDocument> element will display an extra line of text when running on the .NET Framework 4.5 compared to how it displayed when run on the .NET Framework 4.0.</span></span> <span data-ttu-id="75aa4-104">Não conhecemos casos em que a alteração fez com que qualquer texto fosse exibido de forma inadequada ou ilegível, mas textos omitidos de uma exibição de <xref:System.Windows.Documents.FlowDocument> podem aparecer.</span><span class="sxs-lookup"><span data-stu-id="75aa4-104">There are no known cases of the change causing any text to be displayed poorly or illegibly, but it could cause text to appear that previously was omitted from a <xref:System.Windows.Documents.FlowDocument>'s view.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="75aa4-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="75aa4-105">Suggestion</span></span>

<span data-ttu-id="75aa4-106">Em alguns casos, diminuir a propriedade PageHeight do elemento de exibição em 1 pode restaurar o número anterior de linhas exibidas.</span><span class="sxs-lookup"><span data-stu-id="75aa4-106">In some cases, decreasing the display element's PageHeight property by one can restore the previous number of displayed lines.</span></span>

| <span data-ttu-id="75aa4-107">Nome</span><span class="sxs-lookup"><span data-stu-id="75aa4-107">Name</span></span>    | <span data-ttu-id="75aa4-108">Valor</span><span class="sxs-lookup"><span data-stu-id="75aa4-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="75aa4-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="75aa4-109">Scope</span></span>   |<span data-ttu-id="75aa4-110">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="75aa4-110">Edge</span></span>|
|<span data-ttu-id="75aa4-111">Versão</span><span class="sxs-lookup"><span data-stu-id="75aa4-111">Version</span></span>|<span data-ttu-id="75aa4-112">4.5</span><span class="sxs-lookup"><span data-stu-id="75aa4-112">4.5</span></span>|
|<span data-ttu-id="75aa4-113">Tipo</span><span class="sxs-lookup"><span data-stu-id="75aa4-113">Type</span></span>|<span data-ttu-id="75aa4-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="75aa4-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="75aa4-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="75aa4-115">Affected APIs</span></span>

- <xref:System.Windows.Documents.FlowDocument.%23ctor>
- <xref:System.Windows.Documents.FlowDocument.%23ctor(System.Windows.Documents.Block)>
- <xref:System.Windows.Controls.FlowDocumentReader.%23ctor>
- <xref:System.Windows.Controls.FlowDocumentPageViewer.%23ctor>
- <xref:System.Windows.Controls.Primitives.DocumentPageView.%23ctor>

<!--

#### Affected APIs

- `M:System.Windows.Documents.FlowDocument.#ctor`
- `M:System.Windows.Documents.FlowDocument.#ctor(System.Windows.Documents.Block)`
- `M:System.Windows.Controls.FlowDocumentReader.#ctor`
- `M:System.Windows.Controls.FlowDocumentPageViewer.#ctor`
- `M:System.Windows.Controls.Primitives.DocumentPageView.#ctor`

-->
