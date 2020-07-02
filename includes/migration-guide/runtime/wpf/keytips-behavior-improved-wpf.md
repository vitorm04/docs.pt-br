---
ms.openlocfilehash: 9659068304eb208fd6a0a753273453bc669fbc56
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621027"
---
### <a name="keytips-behavior-improved-in-wpf"></a><span data-ttu-id="1b372-101">Melhoria no comportamento das dicas de tecla no WPF</span><span class="sxs-lookup"><span data-stu-id="1b372-101">Keytips behavior improved in WPF</span></span>

#### <a name="details"></a><span data-ttu-id="1b372-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="1b372-102">Details</span></span>

<span data-ttu-id="1b372-103">O comportamento das dicas de tecla foi modificado para manter a paridade com o comportamento no Microsoft Word e no Windows Explorer.</span><span class="sxs-lookup"><span data-stu-id="1b372-103">Keytips behavior has been modified to bring parity with behavior on Microsoft Word and Windows Explorer.</span></span> <span data-ttu-id="1b372-104">Ao verificar se o estado da dica de tecla está habilitado ou não no caso de uma <xref:System.Windows.Input.KeyEventArgs.SystemKey> (especificamente, <xref:System.Windows.Input.Key> ou <xref:System.Windows.Input.Key.F11>) que está sendo pressionada, o WPF trata corretamente as teclas de dica de tecla.</span><span class="sxs-lookup"><span data-stu-id="1b372-104">By checking whether keytip state is enabled or not in the case of a <xref:System.Windows.Input.KeyEventArgs.SystemKey> (in particular, <xref:System.Windows.Input.Key> or <xref:System.Windows.Input.Key.F11>) being pressed, WPF handles keytip keys appropriately.</span></span> <span data-ttu-id="1b372-105">As dicas de tecla agora descartam um menu, mesmo quando ele é aberto pelo mouse.</span><span class="sxs-lookup"><span data-stu-id="1b372-105">Keytips now dismiss a menu even when it is opened by mouse.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="1b372-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="1b372-106">Suggestion</span></span>

<span data-ttu-id="1b372-107">N/D</span><span class="sxs-lookup"><span data-stu-id="1b372-107">N/A</span></span>

| <span data-ttu-id="1b372-108">Name</span><span class="sxs-lookup"><span data-stu-id="1b372-108">Name</span></span>    | <span data-ttu-id="1b372-109">Valor</span><span class="sxs-lookup"><span data-stu-id="1b372-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="1b372-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="1b372-110">Scope</span></span>   |<span data-ttu-id="1b372-111">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="1b372-111">Edge</span></span>|
|<span data-ttu-id="1b372-112">Versão</span><span class="sxs-lookup"><span data-stu-id="1b372-112">Version</span></span>|<span data-ttu-id="1b372-113">4.7.2</span><span class="sxs-lookup"><span data-stu-id="1b372-113">4.7.2</span></span>|
|<span data-ttu-id="1b372-114">Type</span><span class="sxs-lookup"><span data-stu-id="1b372-114">Type</span></span>|<span data-ttu-id="1b372-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="1b372-115">Runtime</span></span>|
