---
ms.openlocfilehash: a007022bf32ffe76861f6f9016a7edace17b0f61
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619805"
---
### <a name="data-written-to-printsystemjobinfojobstream-must-be-in-xps-format"></a><span data-ttu-id="6213e-101">Dados gravados em PrintSystemJobInfo.JobStream devem estar no formato XPS</span><span class="sxs-lookup"><span data-stu-id="6213e-101">Data written to PrintSystemJobInfo.JobStream must be in XPS format</span></span>

#### <a name="details"></a><span data-ttu-id="6213e-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="6213e-102">Details</span></span>

<span data-ttu-id="6213e-103">A propriedade <xref:System.Printing.PrintSystemJobInfo.JobStream> expõe o fluxo de um trabalho de impressão.</span><span class="sxs-lookup"><span data-stu-id="6213e-103">The <xref:System.Printing.PrintSystemJobInfo.JobStream> property exposes the stream of a print job.</span></span> <span data-ttu-id="6213e-104">O usuário pode enviar dados brutos para o sistema operacional subjacente que imprime os componentes gravando-os neste fluxo. A partir do .NET Framework 4.5 no Windows 8 e em versões posteriores do sistema operacional Windows, os dados gravados nesse fluxo devem estar no formato XPS como um fluxo de pacote.</span><span class="sxs-lookup"><span data-stu-id="6213e-104">The user can send raw data to the underlying operating system printing components by writing to this stream.Starting with the .NET Framework 4.5 on Windows 8 and later versions of the Windows operating system, data written to this stream must be in XPS format as a package stream.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="6213e-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="6213e-105">Suggestion</span></span>

<span data-ttu-id="6213e-106">Para mostrar o conteúdo impresso, você tem duas opções:</span><span class="sxs-lookup"><span data-stu-id="6213e-106">To output print content, you can do either of the following:</span></span><ul><li><span data-ttu-id="6213e-107">Use a classe <xref:System.Windows.Xps.XpsDocumentWriter> para produzir conteúdo de impressão.</span><span class="sxs-lookup"><span data-stu-id="6213e-107">Use the <xref:System.Windows.Xps.XpsDocumentWriter> class to output print content.</span></span> <span data-ttu-id="6213e-108">Essa é a alternativa recomendada.</span><span class="sxs-lookup"><span data-stu-id="6213e-108">This is the recommended alternative.</span></span></li><li><span data-ttu-id="6213e-109">Garanta que os dados enviados ao fluxo retornado pela propriedade <xref:System.Printing.PrintSystemJobInfo.JobStream> estão no formato XPS como um fluxo de pacote.</span><span class="sxs-lookup"><span data-stu-id="6213e-109">Ensure that the data sent to the stream returned by the <xref:System.Printing.PrintSystemJobInfo.JobStream> property is in XPS format as a package stream.</span></span></li></ul>

| <span data-ttu-id="6213e-110">Name</span><span class="sxs-lookup"><span data-stu-id="6213e-110">Name</span></span>    | <span data-ttu-id="6213e-111">Valor</span><span class="sxs-lookup"><span data-stu-id="6213e-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="6213e-112">Escopo</span><span class="sxs-lookup"><span data-stu-id="6213e-112">Scope</span></span>   |<span data-ttu-id="6213e-113">Secundária</span><span class="sxs-lookup"><span data-stu-id="6213e-113">Minor</span></span>|
|<span data-ttu-id="6213e-114">Versão</span><span class="sxs-lookup"><span data-stu-id="6213e-114">Version</span></span>|<span data-ttu-id="6213e-115">4.5</span><span class="sxs-lookup"><span data-stu-id="6213e-115">4.5</span></span>|
|<span data-ttu-id="6213e-116">Type</span><span class="sxs-lookup"><span data-stu-id="6213e-116">Type</span></span>|<span data-ttu-id="6213e-117">Runtime</span><span class="sxs-lookup"><span data-stu-id="6213e-117">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6213e-118">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="6213e-118">Affected APIs</span></span>

-<xref:System.Printing.PrintSystemJobInfo.JobStream?displayProperty=nameWithType></li></ul>|
