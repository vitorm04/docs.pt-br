---
title: Posicionamento dos assemblies
ms.date: 03/30/2017
helpviewer_keywords:
- <codeBase> element
- locating assemblies
- assemblies [.NET Framework], placement
- assemblies [.NET Framework], location
ms.assetid: ff8d48bc-f606-484f-9fe1-d0af264269fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e2168c167c89f989f70a10d5832e70c93a8f90f9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54529889"
---
# <a name="assembly-placement"></a><span data-ttu-id="b0f04-102">Posicionamento dos assemblies</span><span class="sxs-lookup"><span data-stu-id="b0f04-102">Assembly Placement</span></span>
<span data-ttu-id="b0f04-103">Para a maioria dos aplicativos .NET Framework, você localiza assemblies que compõem um aplicativo no diretório do aplicativo, em um subdiretório do diretório do aplicativo ou no cache de assembly global (se o assembly for compartilhado).</span><span class="sxs-lookup"><span data-stu-id="b0f04-103">For most .NET Framework applications, you locate assemblies that make up an application in the application's directory, in a subdirectory of the application's directory, or in the global assembly cache (if the assembly is shared).</span></span> <span data-ttu-id="b0f04-104">Você pode substituir onde o Common Language Runtime procura um assembly usando o [\<elemento codeBase>](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="b0f04-104">You can override where the common language runtime looks for an assembly by using the [\<codeBase> Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) in a configuration file.</span></span> <span data-ttu-id="b0f04-105">Se o assembly não tiver um nome forte, o local especificado usando o [\<elemento codeBase>](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) estará restrito ao diretório ou ao subdiretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b0f04-105">If the assembly does not have a strong name, the location specified using the [\<codeBase> Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) is restricted to the application directory or a subdirectory.</span></span> <span data-ttu-id="b0f04-106">Se o assembly tiver um nome forte, o [\<elemento codeBase>](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) poderá especificar qualquer local no computador ou em uma rede.</span><span class="sxs-lookup"><span data-stu-id="b0f04-106">If the assembly has a strong name, the [\<codeBase> Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) can specify any location on the computer or on a network.</span></span>  
  
 <span data-ttu-id="b0f04-107">Regras similares se aplicam à localização de assemblies durante o trabalho com código não gerenciado ou aplicativos interop COM: se o assembly for compartilhado por vários aplicativos, ele deverá ser instalado no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="b0f04-107">Similar rules apply to locating assemblies when working with unmanaged code or COM interop applications: if the assembly will be shared by multiple applications, it should be installed into the global assembly cache.</span></span> <span data-ttu-id="b0f04-108">Assemblies usados com códigos não gerenciados devem ser exportados como uma biblioteca de tipos e registrados.</span><span class="sxs-lookup"><span data-stu-id="b0f04-108">Assemblies used with unmanaged code must be exported as a type library and registered.</span></span> <span data-ttu-id="b0f04-109">Assemblies usados pelo interop COM devem ser registrados no catálogo, embora em alguns casos, esse registro ocorra automaticamente.</span><span class="sxs-lookup"><span data-stu-id="b0f04-109">Assemblies used by COM interop must be registered in the catalog, although in some cases this registration occurs automatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0f04-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b0f04-110">See also</span></span>
- [<span data-ttu-id="b0f04-111">Como o tempo de execução localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="b0f04-111">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="b0f04-112">Configurando aplicativos</span><span class="sxs-lookup"><span data-stu-id="b0f04-112">Configuring Apps</span></span>](../../../docs/framework/configure-apps/index.md)
- [<span data-ttu-id="b0f04-113">Interoperando com código não gerenciado</span><span class="sxs-lookup"><span data-stu-id="b0f04-113">Interoperating with unmanaged code</span></span>](../../../docs/framework/interop/index.md)
- [<span data-ttu-id="b0f04-114">Assemblies no Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="b0f04-114">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
