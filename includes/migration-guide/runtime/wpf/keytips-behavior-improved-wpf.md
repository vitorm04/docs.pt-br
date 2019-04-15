---
ms.openlocfilehash: 946096cb9510ca12bbd2cecd00099142308b072a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236108"
---
### <a name="keytips-behavior-improved-in-wpf"></a><span data-ttu-id="94331-101">Melhoria no comportamento das dicas de tecla no WPF</span><span class="sxs-lookup"><span data-stu-id="94331-101">Keytips behavior improved in WPF</span></span>

|   |   |
|---|---|
|<span data-ttu-id="94331-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="94331-102">Details</span></span>|<span data-ttu-id="94331-103">O comportamento das dicas de tecla foi modificado para manter a paridade com o comportamento no Microsoft Word e no Windows Explorer.</span><span class="sxs-lookup"><span data-stu-id="94331-103">Keytips behavior has been modified to bring parity with behavior on Microsoft Word and Windows Explorer.</span></span> <span data-ttu-id="94331-104">Ao verificar se o estado da dica de tecla está habilitado ou não no caso de uma <xref:System.Windows.Input.KeyEventArgs.SystemKey> (especificamente, <xref:System.Windows.Input.Key> ou <xref:System.Windows.Input.Key.F11>) que está sendo pressionada, o WPF trata corretamente as teclas de dica de tecla.</span><span class="sxs-lookup"><span data-stu-id="94331-104">By checking whether keytip state is enabled or not in the case of a <xref:System.Windows.Input.KeyEventArgs.SystemKey> (in particular, <xref:System.Windows.Input.Key> or <xref:System.Windows.Input.Key.F11>) being pressed, WPF handles keytip keys appropriately.</span></span> <span data-ttu-id="94331-105">As dicas de tecla agora descartam um menu, mesmo quando ele é aberto pelo mouse.</span><span class="sxs-lookup"><span data-stu-id="94331-105">Keytips now dismiss a menu even when it is opened by mouse.</span></span>|
|<span data-ttu-id="94331-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="94331-106">Suggestion</span></span>|<span data-ttu-id="94331-107">N/D</span><span class="sxs-lookup"><span data-stu-id="94331-107">N/A</span></span>|
|<span data-ttu-id="94331-108">Escopo</span><span class="sxs-lookup"><span data-stu-id="94331-108">Scope</span></span>|<span data-ttu-id="94331-109">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="94331-109">Edge</span></span>|
|<span data-ttu-id="94331-110">Versão</span><span class="sxs-lookup"><span data-stu-id="94331-110">Version</span></span>|<span data-ttu-id="94331-111">4.7.2</span><span class="sxs-lookup"><span data-stu-id="94331-111">4.7.2</span></span>|
|<span data-ttu-id="94331-112">Tipo</span><span class="sxs-lookup"><span data-stu-id="94331-112">Type</span></span>|<span data-ttu-id="94331-113">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="94331-113">Runtime</span></span>|
