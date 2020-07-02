---
ms.openlocfilehash: b836b26f3f52e9d0cc78feb764629bd2fa306657
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621767"
---
### <a name="objectdisposedexception-thrown-by-wpf-spellchecker"></a><span data-ttu-id="e28a1-101">ObjectDisposedException gerada pelo verificador ortográfico do WPF</span><span class="sxs-lookup"><span data-stu-id="e28a1-101">ObjectDisposedException thrown by WPF spellchecker</span></span>

#### <a name="details"></a><span data-ttu-id="e28a1-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="e28a1-102">Details</span></span>

<span data-ttu-id="e28a1-103">Ocasionalmente, os aplicativos WPF falham durante o desligamento com uma <xref:System.ObjectDisposedException?displayProperty=fullName> gerada pelo verificador ortográfico.</span><span class="sxs-lookup"><span data-stu-id="e28a1-103">WPF applications occasionally crash during application shutdown with an <xref:System.ObjectDisposedException?displayProperty=fullName> thrown by the spellchecker.</span></span> <span data-ttu-id="e28a1-104">Isso foi corrigido no WPF do .NET Framework 4.7 por meio do tratamento normal da exceção, garantindo que os aplicativos não sejam mais prejudicados.</span><span class="sxs-lookup"><span data-stu-id="e28a1-104">This is fixed in .NET Framework 4.7 WPF by handling the exception gracefully, and thus ensuring that applications are no longer adversely affected.</span></span> <span data-ttu-id="e28a1-105">Observe que exceções de primeira chance ocasionais continuariam a ser observadas em aplicativos em execução em um depurador.</span><span class="sxs-lookup"><span data-stu-id="e28a1-105">It should be noted that occasional first-chance exceptions would continue to be observed in applications running under a debugger.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e28a1-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="e28a1-106">Suggestion</span></span>

<span data-ttu-id="e28a1-107">Atualizar para o .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="e28a1-107">Upgrade to .NET Framework 4.7</span></span>

| <span data-ttu-id="e28a1-108">Name</span><span class="sxs-lookup"><span data-stu-id="e28a1-108">Name</span></span>    | <span data-ttu-id="e28a1-109">Valor</span><span class="sxs-lookup"><span data-stu-id="e28a1-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e28a1-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="e28a1-110">Scope</span></span>   |<span data-ttu-id="e28a1-111">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="e28a1-111">Edge</span></span>|
|<span data-ttu-id="e28a1-112">Versão</span><span class="sxs-lookup"><span data-stu-id="e28a1-112">Version</span></span>|<span data-ttu-id="e28a1-113">4.6.1</span><span class="sxs-lookup"><span data-stu-id="e28a1-113">4.6.1</span></span>|
|<span data-ttu-id="e28a1-114">Type</span><span class="sxs-lookup"><span data-stu-id="e28a1-114">Type</span></span>|<span data-ttu-id="e28a1-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="e28a1-115">Runtime</span></span>|
