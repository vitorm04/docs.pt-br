---
ms.openlocfilehash: 891c29b731214fb0028e960256b79cfc267d86b9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235039"
---
### <a name="deserialization-of-objects-across-appdomains-can-fail"></a><span data-ttu-id="8959b-101">Desserialização de objetos em domínios de aplicativo podem falhar</span><span class="sxs-lookup"><span data-stu-id="8959b-101">Deserialization of objects across appdomains can fail</span></span>

|   |   |
|---|---|
|<span data-ttu-id="8959b-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="8959b-102">Details</span></span>|<span data-ttu-id="8959b-103">Em alguns casos, quando um aplicativo usa dois ou mais domínios de aplicativo com bases de aplicativo diferentes, a tentativa de desserializar objetos no contexto da chamada lógica nos domínios de aplicativo aciona uma exceção.</span><span class="sxs-lookup"><span data-stu-id="8959b-103">In some cases, when an app uses two or more app domains with different application bases, trying to deserialize objects in the logical call context across app domains throws an exception.</span></span>|
|<span data-ttu-id="8959b-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="8959b-104">Suggestion</span></span>|<span data-ttu-id="8959b-105">Confira [Mitigação: Desserialização de objetos em domínios do aplicativo](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)</span><span class="sxs-lookup"><span data-stu-id="8959b-105">See [Mitigation: Deserialization of Objects Across App Domains](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)</span></span>|
|<span data-ttu-id="8959b-106">Escopo</span><span class="sxs-lookup"><span data-stu-id="8959b-106">Scope</span></span>|<span data-ttu-id="8959b-107">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="8959b-107">Edge</span></span>|
|<span data-ttu-id="8959b-108">Versão</span><span class="sxs-lookup"><span data-stu-id="8959b-108">Version</span></span>|<span data-ttu-id="8959b-109">4.5.1</span><span class="sxs-lookup"><span data-stu-id="8959b-109">4.5.1</span></span>|
|<span data-ttu-id="8959b-110">Tipo</span><span class="sxs-lookup"><span data-stu-id="8959b-110">Type</span></span>|<span data-ttu-id="8959b-111">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="8959b-111">Runtime</span></span>|
