---
ms.openlocfilehash: af10716fe5f4c07091e8605cdf620e4a499fb1e8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619771"
---
### <a name="ipad-should-not-be-used-in-custom-capabilities-file-because-it-is-now-a-browser-capability"></a><span data-ttu-id="5b6f3-101">IPad não deve ser usado no arquivo de funcionalidades personalizadas, pois agora é uma funcionalidade do navegador</span><span class="sxs-lookup"><span data-stu-id="5b6f3-101">IPad should not be used in custom capabilities file because it is now a browser capability</span></span>

#### <a name="details"></a><span data-ttu-id="5b6f3-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="5b6f3-102">Details</span></span>

<span data-ttu-id="5b6f3-103">Começando com o .NET Framework 4.5, o iPad é um identificador no arquivo de funcionalidades padrão do navegador ASP.NET, portanto ele não deve ser usado em um arquivo de funcionalidades personalizados</span><span class="sxs-lookup"><span data-stu-id="5b6f3-103">Beginning in .NET Framework 4.5, iPad is an identifier in the default ASP.NET browser capabilities file, so it should not be used in a custom capabilities file</span></span>

#### <a name="suggestion"></a><span data-ttu-id="5b6f3-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="5b6f3-104">Suggestion</span></span>

<span data-ttu-id="5b6f3-105">Se funcionalidades específicas do iPad forem exigidas, será necessário modificar o comportamento dele configurando funcionalidades na refID do gateway predefinido &quot;IPad&quot; em vez de gerar uma nova ID &quot;IPad&quot; pela correspondência do agente do usuário.</span><span class="sxs-lookup"><span data-stu-id="5b6f3-105">If iPad-specific capabilities are required, it is necessary to modify iPad behavior by setting capabilities on the pre-defined gateway refID &quot;IPad&quot; instead of by generating a new &quot;IPad&quot; ID by user agent matching.</span></span>

| <span data-ttu-id="5b6f3-106">Name</span><span class="sxs-lookup"><span data-stu-id="5b6f3-106">Name</span></span>    | <span data-ttu-id="5b6f3-107">Valor</span><span class="sxs-lookup"><span data-stu-id="5b6f3-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="5b6f3-108">Escopo</span><span class="sxs-lookup"><span data-stu-id="5b6f3-108">Scope</span></span>   |<span data-ttu-id="5b6f3-109">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="5b6f3-109">Edge</span></span>|
|<span data-ttu-id="5b6f3-110">Versão</span><span class="sxs-lookup"><span data-stu-id="5b6f3-110">Version</span></span>|<span data-ttu-id="5b6f3-111">4.5</span><span class="sxs-lookup"><span data-stu-id="5b6f3-111">4.5</span></span>|
|<span data-ttu-id="5b6f3-112">Type</span><span class="sxs-lookup"><span data-stu-id="5b6f3-112">Type</span></span>|<span data-ttu-id="5b6f3-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="5b6f3-113">Runtime</span></span>|
