---
ms.openlocfilehash: a9011514c7c4393ec44de2c7fae88768cdccf435
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496429"
---
### <a name="the-net-framework-46-does-not-use-a-45xx-version-when-registering-itself-in-the-registry"></a><span data-ttu-id="05523-101">.NET Framework 4.6 não usa uma versão 4.5.x.x ao se registrar no registro</span><span class="sxs-lookup"><span data-stu-id="05523-101">The .NET Framework 4.6 does not use a 4.5.x.x version when registering itself in the registry</span></span>

#### <a name="details"></a><span data-ttu-id="05523-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="05523-102">Details</span></span>

<span data-ttu-id="05523-103">Como é de se esperar, a chave de versão definida no registro (em <code>HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4\Full</code>) do .NET Framework 4.6 começa com "4.6", e não "4.5".</span><span class="sxs-lookup"><span data-stu-id="05523-103">As one might expect, the version key set in the registry (at <code>HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4\Full</code>) for the .NET Framework 4.6 begins with '4.6', not '4.5'.</span></span> <span data-ttu-id="05523-104">Os aplicativos que dependem dessas chaves do Registro para saber quais versões do .NET Framework estão instaladas em um computador precisam ser atualizados para compreenderem que 4.6 é uma nova versão possível, compatível com as versões 4.5.x anteriores.</span><span class="sxs-lookup"><span data-stu-id="05523-104">Apps that depend on these registry keys to know which .NET Framework versions are installed on a machine should be updated to understand that 4.6 is a new possible version, and one that is compatible with previous 4.5.x releases.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="05523-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="05523-105">Suggestion</span></span>

<span data-ttu-id="05523-106">Atualize os aplicativos que estão investigando uma instalação do .NET Framework 4.5 procurando por chaves do Registro 4.5 que também aceitam 4.6.</span><span class="sxs-lookup"><span data-stu-id="05523-106">Update apps probing for a .NET Framework 4.5 install by looking for 4.5 registry keys to also accept 4.6.</span></span>

| <span data-ttu-id="05523-107">Nome</span><span class="sxs-lookup"><span data-stu-id="05523-107">Name</span></span>    | <span data-ttu-id="05523-108">Valor</span><span class="sxs-lookup"><span data-stu-id="05523-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="05523-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="05523-109">Scope</span></span>   |<span data-ttu-id="05523-110">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="05523-110">Edge</span></span>|
|<span data-ttu-id="05523-111">Versão</span><span class="sxs-lookup"><span data-stu-id="05523-111">Version</span></span>|<span data-ttu-id="05523-112">4.6</span><span class="sxs-lookup"><span data-stu-id="05523-112">4.6</span></span>|
|<span data-ttu-id="05523-113">Tipo</span><span class="sxs-lookup"><span data-stu-id="05523-113">Type</span></span>|<span data-ttu-id="05523-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="05523-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="05523-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="05523-115">Affected APIs</span></span>

<span data-ttu-id="05523-116">Não detectável via análise de API.</span><span class="sxs-lookup"><span data-stu-id="05523-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
