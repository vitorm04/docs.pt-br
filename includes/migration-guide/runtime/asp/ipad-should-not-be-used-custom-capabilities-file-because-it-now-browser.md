---
ms.openlocfilehash: 84f570cbbd97be79426e117d4c97ec182a397fd4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235052"
---
### <a name="ipad-should-not-be-used-in-custom-capabilities-file-because-it-is-now-a-browser-capability"></a><span data-ttu-id="f70a3-101">IPad não deve ser usado no arquivo de funcionalidades personalizadas, pois agora é uma funcionalidade do navegador</span><span class="sxs-lookup"><span data-stu-id="f70a3-101">IPad should not be used in custom capabilities file because it is now a browser capability</span></span>

|   |   |
|---|---|
|<span data-ttu-id="f70a3-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="f70a3-102">Details</span></span>|<span data-ttu-id="f70a3-103">Começando com o .NET Framework 4.5, o iPad é um identificador no arquivo de funcionalidades padrão do navegador ASP.NET, portanto ele não deve ser usado em um arquivo de funcionalidades personalizados</span><span class="sxs-lookup"><span data-stu-id="f70a3-103">Beginning in .NET Framework 4.5, iPad is an identifier in the default ASP.NET browser capabilities file, so it should not be used in a custom capabilities file</span></span>|
|<span data-ttu-id="f70a3-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="f70a3-104">Suggestion</span></span>|<span data-ttu-id="f70a3-105">Se funcionalidades específicas do iPad forem exigidas, será necessário modificar o comportamento dele configurando funcionalidades na refID do gateway predefinido &quot;IPad&quot; em vez de gerar uma nova ID &quot;IPad&quot; pela correspondência do agente do usuário.</span><span class="sxs-lookup"><span data-stu-id="f70a3-105">If iPad-specific capabilities are required, it is necessary to modify iPad behavior by setting capabilities on the pre-defined gateway refID &quot;IPad&quot; instead of by generating a new &quot;IPad&quot; ID by user agent matching.</span></span>|
|<span data-ttu-id="f70a3-106">Escopo</span><span class="sxs-lookup"><span data-stu-id="f70a3-106">Scope</span></span>|<span data-ttu-id="f70a3-107">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="f70a3-107">Edge</span></span>|
|<span data-ttu-id="f70a3-108">Versão</span><span class="sxs-lookup"><span data-stu-id="f70a3-108">Version</span></span>|<span data-ttu-id="f70a3-109">4.5</span><span class="sxs-lookup"><span data-stu-id="f70a3-109">4.5</span></span>|
|<span data-ttu-id="f70a3-110">Tipo</span><span class="sxs-lookup"><span data-stu-id="f70a3-110">Type</span></span>|<span data-ttu-id="f70a3-111">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="f70a3-111">Runtime</span></span>|
