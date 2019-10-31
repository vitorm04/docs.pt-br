---
ms.openlocfilehash: 9d09f598538b9d5ee3f995d6281b8eb4b2668050
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802517"
---
### <a name="objectdisposedexception-thrown-by-wpf-spellchecker"></a><span data-ttu-id="a8bd6-101">ObjectDisposedException gerada pelo verificador ortográfico do WPF</span><span class="sxs-lookup"><span data-stu-id="a8bd6-101">ObjectDisposedException thrown by WPF spellchecker</span></span>

|   |   |
|---|---|
|<span data-ttu-id="a8bd6-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="a8bd6-102">Details</span></span>|<span data-ttu-id="a8bd6-103">Ocasionalmente, os aplicativos WPF falham durante o desligamento com uma <xref:System.ObjectDisposedException?displayProperty=name> gerada pelo verificador ortográfico.</span><span class="sxs-lookup"><span data-stu-id="a8bd6-103">WPF applications occasionally crash during application shutdown with an <xref:System.ObjectDisposedException?displayProperty=name> thrown by the spellchecker.</span></span> <span data-ttu-id="a8bd6-104">Isso foi corrigido no WPF do .NET Framework 4.7 por meio do tratamento normal da exceção, garantindo que os aplicativos não sejam mais prejudicados.</span><span class="sxs-lookup"><span data-stu-id="a8bd6-104">This is fixed in .NET Framework 4.7 WPF by handling the exception gracefully, and thus ensuring that applications are no longer adversely affected.</span></span> <span data-ttu-id="a8bd6-105">Observe que exceções de primeira chance ocasionais continuariam a ser observadas em aplicativos em execução em um depurador.</span><span class="sxs-lookup"><span data-stu-id="a8bd6-105">It should be noted that occasional first-chance exceptions would continue to be observed in applications running under a debugger.</span></span>|
|<span data-ttu-id="a8bd6-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="a8bd6-106">Suggestion</span></span>|<span data-ttu-id="a8bd6-107">Atualizar para o .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="a8bd6-107">Upgrade to .NET Framework 4.7</span></span>|
|<span data-ttu-id="a8bd6-108">Escopo</span><span class="sxs-lookup"><span data-stu-id="a8bd6-108">Scope</span></span>|<span data-ttu-id="a8bd6-109">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="a8bd6-109">Edge</span></span>|
|<span data-ttu-id="a8bd6-110">Versão</span><span class="sxs-lookup"><span data-stu-id="a8bd6-110">Version</span></span>|<span data-ttu-id="a8bd6-111">4.6.1</span><span class="sxs-lookup"><span data-stu-id="a8bd6-111">4.6.1</span></span>|
|<span data-ttu-id="a8bd6-112">Tipo</span><span class="sxs-lookup"><span data-stu-id="a8bd6-112">Type</span></span>|<span data-ttu-id="a8bd6-113">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="a8bd6-113">Runtime</span></span>|

