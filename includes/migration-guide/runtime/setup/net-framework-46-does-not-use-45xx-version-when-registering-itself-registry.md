---
ms.openlocfilehash: ee5070a1a4c58d6c1282ba47c921436ca22722ff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858386"
---
### <a name="the-net-framework-46-does-not-use-a-45xx-version-when-registering-itself-in-the-registry"></a><span data-ttu-id="0708f-101">.NET Framework 4.6 não usa uma versão 4.5.x.x ao se registrar no registro</span><span class="sxs-lookup"><span data-stu-id="0708f-101">The .NET Framework 4.6 does not use a 4.5.x.x version when registering itself in the registry</span></span>

|   |   |
|---|---|
|<span data-ttu-id="0708f-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="0708f-102">Details</span></span>|<span data-ttu-id="0708f-103">Como é de se esperar, a chave de versão definida no registro (em <code>HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4\Full</code>) do .NET Framework 4.6 começa com "4.6", e não "4.5".</span><span class="sxs-lookup"><span data-stu-id="0708f-103">As one might expect, the version key set in the registry (at <code>HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4\Full</code>) for the .NET Framework 4.6 begins with '4.6', not '4.5'.</span></span> <span data-ttu-id="0708f-104">Os aplicativos que dependem dessas chaves do Registro para saber quais versões do .NET Framework estão instaladas em um computador precisam ser atualizados para compreenderem que 4.6 é uma nova versão possível, compatível com as versões 4.5.x anteriores.</span><span class="sxs-lookup"><span data-stu-id="0708f-104">Apps that depend on these registry keys to know which .NET Framework versions are installed on a machine should be updated to understand that 4.6 is a new possible version, and one that is compatible with previous 4.5.x releases.</span></span>|
|<span data-ttu-id="0708f-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="0708f-105">Suggestion</span></span>|<span data-ttu-id="0708f-106">Atualize os aplicativos que estão investigando uma instalação do .NET Framework 4.5 procurando por chaves do Registro 4.5 que também aceitam 4.6.</span><span class="sxs-lookup"><span data-stu-id="0708f-106">Update apps probing for a .NET Framework 4.5 install by looking for 4.5 registry keys to also accept 4.6.</span></span>|
|<span data-ttu-id="0708f-107">Escopo</span><span class="sxs-lookup"><span data-stu-id="0708f-107">Scope</span></span>|<span data-ttu-id="0708f-108">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="0708f-108">Edge</span></span>|
|<span data-ttu-id="0708f-109">Versão</span><span class="sxs-lookup"><span data-stu-id="0708f-109">Version</span></span>|<span data-ttu-id="0708f-110">4.6</span><span class="sxs-lookup"><span data-stu-id="0708f-110">4.6</span></span>|
|<span data-ttu-id="0708f-111">Type</span><span class="sxs-lookup"><span data-stu-id="0708f-111">Type</span></span>|<span data-ttu-id="0708f-112">Runtime</span><span class="sxs-lookup"><span data-stu-id="0708f-112">Runtime</span></span>|
