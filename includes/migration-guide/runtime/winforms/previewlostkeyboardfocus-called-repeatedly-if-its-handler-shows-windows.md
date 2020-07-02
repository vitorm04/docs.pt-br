---
ms.openlocfilehash: 2aa6603e2ed77ffa94fbc6325cd5db50985bda6a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619876"
---
### <a name="previewlostkeyboardfocus-is-called-repeatedly-if-its-handler-shows-a-windows-forms-message-box"></a><span data-ttu-id="e7174-101">PreviewLostKeyboardFocus será chamado repetidamente se seu manipulador mostrar uma caixa de mensagem do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e7174-101">PreviewLostKeyboardFocus is called repeatedly if its handler shows a Windows Forms message box</span></span>

#### <a name="details"></a><span data-ttu-id="e7174-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="e7174-102">Details</span></span>

<span data-ttu-id="e7174-103">A partir do .NET Framework 4.5, chamar <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> de um manipulador <xref:System.Windows.UIElement.PreviewLostKeyboardFocus> fará com que o manipulador seja acionado novamente quando a caixa de mensagem for fechada, possivelmente resultando em um loop infinito de caixas de mensagem.</span><span class="sxs-lookup"><span data-stu-id="e7174-103">Beginning in the .NET Framework 4.5, calling <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> from a <xref:System.Windows.UIElement.PreviewLostKeyboardFocus> handler will cause the handler to re-fire when the message box is closed, potentially resulting in an infinite loop of message boxes.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e7174-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="e7174-104">Suggestion</span></span>

<span data-ttu-id="e7174-105">Há duas opções para contornar esse problema:</span><span class="sxs-lookup"><span data-stu-id="e7174-105">There are two options to work around this issue:</span></span><ol><li><span data-ttu-id="e7174-106">Ele pode ser evitado chamando <xref:System.Windows.MessageBox.Show%2A?displayProperty=nameWithType> em vez de <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e7174-106">It may be avoided by calling <xref:System.Windows.MessageBox.Show%2A?displayProperty=nameWithType> instead of <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType>.</span></span></li><li><span data-ttu-id="e7174-107">Ele pode ser evitado mostrando a caixa de mensagem de um manipulador de eventos <xref:System.Windows.UIElement.LostKeyboardFocus> (em oposição a um manipulador de eventos <xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=fullName>).</span><span class="sxs-lookup"><span data-stu-id="e7174-107">It may be avoided by showing the message box from a <xref:System.Windows.UIElement.LostKeyboardFocus> event handler (as opposed to a <xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=fullName> event handler).</span></span></li></ol>

| <span data-ttu-id="e7174-108">Name</span><span class="sxs-lookup"><span data-stu-id="e7174-108">Name</span></span>    | <span data-ttu-id="e7174-109">Valor</span><span class="sxs-lookup"><span data-stu-id="e7174-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e7174-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="e7174-110">Scope</span></span>   |<span data-ttu-id="e7174-111">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="e7174-111">Edge</span></span>|
|<span data-ttu-id="e7174-112">Versão</span><span class="sxs-lookup"><span data-stu-id="e7174-112">Version</span></span>|<span data-ttu-id="e7174-113">4.5</span><span class="sxs-lookup"><span data-stu-id="e7174-113">4.5</span></span>|
|<span data-ttu-id="e7174-114">Type</span><span class="sxs-lookup"><span data-stu-id="e7174-114">Type</span></span>|<span data-ttu-id="e7174-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="e7174-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e7174-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="e7174-116">Affected APIs</span></span>

-<xref:System.Windows.ContentElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.IInputElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.UIElement3D.PreviewLostKeyboardFocus?displayProperty=nameWithType></li></ul>|
