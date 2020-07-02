---
ms.openlocfilehash: 5c949b79eefa68ea6f8d4ad27c716c438e24f170
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619777"
---
### <a name="deserialization-of-objects-across-appdomains-can-fail"></a><span data-ttu-id="f996d-101">Desserialização de objetos em domínios de aplicativo podem falhar</span><span class="sxs-lookup"><span data-stu-id="f996d-101">Deserialization of objects across appdomains can fail</span></span>

#### <a name="details"></a><span data-ttu-id="f996d-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="f996d-102">Details</span></span>

<span data-ttu-id="f996d-103">Em alguns casos, quando um aplicativo usa dois ou mais domínios de aplicativo com bases de aplicativo diferentes, a tentativa de desserializar objetos no contexto da chamada lógica nos domínios de aplicativo aciona uma exceção.</span><span class="sxs-lookup"><span data-stu-id="f996d-103">In some cases, when an app uses two or more app domains with different application bases, trying to deserialize objects in the logical call context across app domains throws an exception.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f996d-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="f996d-104">Suggestion</span></span>

<span data-ttu-id="f996d-105">Consulte [Mitigação: desserialização de objetos em domínios de aplicativos](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md).</span><span class="sxs-lookup"><span data-stu-id="f996d-105">See [Mitigation: Deserialization of Objects Across App Domains](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)</span></span>

| <span data-ttu-id="f996d-106">Name</span><span class="sxs-lookup"><span data-stu-id="f996d-106">Name</span></span>    | <span data-ttu-id="f996d-107">Valor</span><span class="sxs-lookup"><span data-stu-id="f996d-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f996d-108">Escopo</span><span class="sxs-lookup"><span data-stu-id="f996d-108">Scope</span></span>   |<span data-ttu-id="f996d-109">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="f996d-109">Edge</span></span>|
|<span data-ttu-id="f996d-110">Versão</span><span class="sxs-lookup"><span data-stu-id="f996d-110">Version</span></span>|<span data-ttu-id="f996d-111">4.5.1</span><span class="sxs-lookup"><span data-stu-id="f996d-111">4.5.1</span></span>|
|<span data-ttu-id="f996d-112">Type</span><span class="sxs-lookup"><span data-stu-id="f996d-112">Type</span></span>|<span data-ttu-id="f996d-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="f996d-113">Runtime</span></span>|
