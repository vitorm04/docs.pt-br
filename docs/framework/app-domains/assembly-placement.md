---
title: Posicionamento dos assemblies
description: Examine as diretrizes para o posicionamento do assembly .NET nos diretórios (por exemplo, no cache de assembly global ou no diretório ou subdiretório do aplicativo).
ms.date: 03/30/2017
helpviewer_keywords:
- <codeBase> element
- locating assemblies
- assemblies [.NET Framework], placement
- assemblies [.NET Framework], location
ms.assetid: ff8d48bc-f606-484f-9fe1-d0af264269fb
ms.openlocfilehash: 3106f6f01229057725cbc2e8e689a4e2247f95e6
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104959"
---
# <a name="assembly-placement"></a><span data-ttu-id="d0ef3-103">Posicionamento dos assemblies</span><span class="sxs-lookup"><span data-stu-id="d0ef3-103">Assembly Placement</span></span>
<span data-ttu-id="d0ef3-104">Para a maioria dos aplicativos .NET Framework, você localiza assemblies que compõem um aplicativo no diretório do aplicativo, em um subdiretório do diretório do aplicativo ou no cache de assembly global (se o assembly for compartilhado).</span><span class="sxs-lookup"><span data-stu-id="d0ef3-104">For most .NET Framework applications, you locate assemblies that make up an application in the application's directory, in a subdirectory of the application's directory, or in the global assembly cache (if the assembly is shared).</span></span> <span data-ttu-id="d0ef3-105">Você pode substituir onde o Common Language Runtime procura um assembly usando o [ \<codeBase> elemento](../configure-apps/file-schema/runtime/codebase-element.md) em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="d0ef3-105">You can override where the common language runtime looks for an assembly by using the [\<codeBase> Element](../configure-apps/file-schema/runtime/codebase-element.md) in a configuration file.</span></span> <span data-ttu-id="d0ef3-106">Se o assembly não tiver um nome forte, o local especificado usando o [ \<codeBase> elemento](../configure-apps/file-schema/runtime/codebase-element.md) será restrito ao diretório do aplicativo ou a um subdiretório.</span><span class="sxs-lookup"><span data-stu-id="d0ef3-106">If the assembly does not have a strong name, the location specified using the [\<codeBase> Element](../configure-apps/file-schema/runtime/codebase-element.md) is restricted to the application directory or a subdirectory.</span></span> <span data-ttu-id="d0ef3-107">Se o assembly tiver um nome forte, o [ \<codeBase> elemento](../configure-apps/file-schema/runtime/codebase-element.md) poderá especificar qualquer local no computador ou em uma rede.</span><span class="sxs-lookup"><span data-stu-id="d0ef3-107">If the assembly has a strong name, the [\<codeBase> Element](../configure-apps/file-schema/runtime/codebase-element.md) can specify any location on the computer or on a network.</span></span>  
  
 <span data-ttu-id="d0ef3-108">Regras similares se aplicam à localização de assemblies durante o trabalho com código não gerenciado ou aplicativos interop COM: se o assembly for compartilhado por vários aplicativos, ele deverá ser instalado no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="d0ef3-108">Similar rules apply to locating assemblies when working with unmanaged code or COM interop applications: if the assembly will be shared by multiple applications, it should be installed into the global assembly cache.</span></span> <span data-ttu-id="d0ef3-109">Assemblies usados com códigos não gerenciados devem ser exportados como uma biblioteca de tipos e registrados.</span><span class="sxs-lookup"><span data-stu-id="d0ef3-109">Assemblies used with unmanaged code must be exported as a type library and registered.</span></span> <span data-ttu-id="d0ef3-110">Assemblies usados pelo interop COM devem ser registrados no catálogo, embora em alguns casos, esse registro ocorra automaticamente.</span><span class="sxs-lookup"><span data-stu-id="d0ef3-110">Assemblies used by COM interop must be registered in the catalog, although in some cases this registration occurs automatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0ef3-111">Veja também</span><span class="sxs-lookup"><span data-stu-id="d0ef3-111">See also</span></span>

- [<span data-ttu-id="d0ef3-112">Como o runtime localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="d0ef3-112">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="d0ef3-113">Configuração de aplicativos</span><span class="sxs-lookup"><span data-stu-id="d0ef3-113">Configuring Apps</span></span>](../configure-apps/index.md)
- [<span data-ttu-id="d0ef3-114">Interoperação com código não gerenciado</span><span class="sxs-lookup"><span data-stu-id="d0ef3-114">Interoperating with unmanaged code</span></span>](../interop/index.md)
- [<span data-ttu-id="d0ef3-115">Assemblies no .NET</span><span class="sxs-lookup"><span data-stu-id="d0ef3-115">Assemblies in .NET</span></span>](index.md)
