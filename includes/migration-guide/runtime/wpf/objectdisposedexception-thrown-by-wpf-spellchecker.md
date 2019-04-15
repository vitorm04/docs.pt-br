---
ms.openlocfilehash: a3f5f512fd17ab2b076f868be24e5c73d8698c49
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234086"
---
### <a name="objectdisposedexception-thrown-by-wpf-spellchecker"></a><span data-ttu-id="a5f29-101">ObjectDisposedException gerada pelo verificador ortográfico do WPF</span><span class="sxs-lookup"><span data-stu-id="a5f29-101">ObjectDisposedException thrown by WPF spellchecker</span></span>

|   |   |
|---|---|
|<span data-ttu-id="a5f29-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="a5f29-102">Details</span></span>|<span data-ttu-id="a5f29-103">Ocasionalmente, os aplicativos WPF falham durante o desligamento com uma <xref:System.ObjectDisposedException?displayProperty=name> gerada pelo verificador ortográfico.</span><span class="sxs-lookup"><span data-stu-id="a5f29-103">WPF applications occasionally crash during application shutdown with an <xref:System.ObjectDisposedException?displayProperty=name> thrown by the spellchecker.</span></span> <span data-ttu-id="a5f29-104">Isso foi corrigido no WPF do .NET Framework 4.7 por meio do tratamento normal da exceção, garantindo que os aplicativos não sejam mais prejudicados.</span><span class="sxs-lookup"><span data-stu-id="a5f29-104">This is fixed in .NET Framework 4.7 WPF by handling the exception gracefully, and thus ensuring that applications are no longer adversely affected.</span></span> <span data-ttu-id="a5f29-105">Observe que exceções de primeira chance ocasionais continuariam a ser observadas em aplicativos em execução em um depurador.</span><span class="sxs-lookup"><span data-stu-id="a5f29-105">It should be noted that occasional first-chance exceptions would continue to be observed in applications running under a debugger.</span></span>|
|<span data-ttu-id="a5f29-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="a5f29-106">Suggestion</span></span>|<span data-ttu-id="a5f29-107">Atualizar para o .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="a5f29-107">Upgrade to .NET Framework 4.7</span></span>|
|<span data-ttu-id="a5f29-108">Escopo</span><span class="sxs-lookup"><span data-stu-id="a5f29-108">Scope</span></span>|<span data-ttu-id="a5f29-109">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="a5f29-109">Edge</span></span>|
|<span data-ttu-id="a5f29-110">Versão</span><span class="sxs-lookup"><span data-stu-id="a5f29-110">Version</span></span>|<span data-ttu-id="a5f29-111">4.6.1</span><span class="sxs-lookup"><span data-stu-id="a5f29-111">4.6.1</span></span>|
|<span data-ttu-id="a5f29-112">Tipo</span><span class="sxs-lookup"><span data-stu-id="a5f29-112">Type</span></span>|<span data-ttu-id="a5f29-113">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="a5f29-113">Runtime</span></span>|
