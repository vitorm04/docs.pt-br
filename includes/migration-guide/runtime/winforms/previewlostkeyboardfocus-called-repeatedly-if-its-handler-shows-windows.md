---
ms.openlocfilehash: c4a3d903894027a01d32ca132d1233da9d9c3ee5
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497050"
---
### <a name="previewlostkeyboardfocus-is-called-repeatedly-if-its-handler-shows-a-windows-forms-message-box"></a><span data-ttu-id="588c0-101">PreviewLostKeyboardFocus será chamado repetidamente se seu manipulador mostrar uma caixa de mensagem do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="588c0-101">PreviewLostKeyboardFocus is called repeatedly if its handler shows a Windows Forms message box</span></span>

#### <a name="details"></a><span data-ttu-id="588c0-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="588c0-102">Details</span></span>

<span data-ttu-id="588c0-103">A partir do .NET Framework 4.5, chamar <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> de um manipulador <xref:System.Windows.UIElement.PreviewLostKeyboardFocus> fará com que o manipulador seja acionado novamente quando a caixa de mensagem for fechada, possivelmente resultando em um loop infinito de caixas de mensagem.</span><span class="sxs-lookup"><span data-stu-id="588c0-103">Beginning in the .NET Framework 4.5, calling <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> from a <xref:System.Windows.UIElement.PreviewLostKeyboardFocus> handler will cause the handler to re-fire when the message box is closed, potentially resulting in an infinite loop of message boxes.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="588c0-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="588c0-104">Suggestion</span></span>

<span data-ttu-id="588c0-105">Há duas opções para contornar esse problema:</span><span class="sxs-lookup"><span data-stu-id="588c0-105">There are two options to work around this issue:</span></span><ol><li><span data-ttu-id="588c0-106">Ele pode ser evitado chamando <xref:System.Windows.MessageBox.Show%2A?displayProperty=nameWithType> em vez de <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="588c0-106">It may be avoided by calling <xref:System.Windows.MessageBox.Show%2A?displayProperty=nameWithType> instead of <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType>.</span></span></li><li><span data-ttu-id="588c0-107">Ele pode ser evitado mostrando a caixa de mensagem de um manipulador de eventos <xref:System.Windows.UIElement.LostKeyboardFocus> (em oposição a um manipulador de eventos <xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=fullName>).</span><span class="sxs-lookup"><span data-stu-id="588c0-107">It may be avoided by showing the message box from a <xref:System.Windows.UIElement.LostKeyboardFocus> event handler (as opposed to a <xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=fullName> event handler).</span></span></li></ol>

| <span data-ttu-id="588c0-108">Nome</span><span class="sxs-lookup"><span data-stu-id="588c0-108">Name</span></span>    | <span data-ttu-id="588c0-109">Valor</span><span class="sxs-lookup"><span data-stu-id="588c0-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="588c0-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="588c0-110">Scope</span></span>   |<span data-ttu-id="588c0-111">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="588c0-111">Edge</span></span>|
|<span data-ttu-id="588c0-112">Versão</span><span class="sxs-lookup"><span data-stu-id="588c0-112">Version</span></span>|<span data-ttu-id="588c0-113">4.5</span><span class="sxs-lookup"><span data-stu-id="588c0-113">4.5</span></span>|
|<span data-ttu-id="588c0-114">Tipo</span><span class="sxs-lookup"><span data-stu-id="588c0-114">Type</span></span>|<span data-ttu-id="588c0-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="588c0-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="588c0-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="588c0-116">Affected APIs</span></span>

- <xref:System.Windows.ContentElement.PreviewLostKeyboardFocus?displayProperty=nameWithType>
- <xref:System.Windows.IInputElement.PreviewLostKeyboardFocus?displayProperty=nameWithType>
- <xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=nameWithType>
- <xref:System.Windows.UIElement3D.PreviewLostKeyboardFocus?displayProperty=nameWithType>

<!--

#### Affected APIs

- `E:System.Windows.ContentElement.PreviewLostKeyboardFocus`
- `E:System.Windows.IInputElement.PreviewLostKeyboardFocus`
- `E:System.Windows.UIElement.PreviewLostKeyboardFocus`
- `E:System.Windows.UIElement3D.PreviewLostKeyboardFocus`

-->
