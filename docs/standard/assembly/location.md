---
title: Localização do assembly
description: O local de um assembly .NET determina como o CLR o encontra e se ele pode ser compartilhado com outros assemblies.
ms.date: 08/20/2019
helpviewer_keywords:
- locating assemblies
- assemblies [.NET], location
ms.assetid: 9f1f41a7-2954-49d3-a2c0-62b6ef4d40ab
ms.openlocfilehash: 1fa1c486c0cddce4ddcfae7f2df27e2e85c88e66
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92687605"
---
# <a name="assembly-location"></a><span data-ttu-id="2d7e7-103">Localização do assembly</span><span class="sxs-lookup"><span data-stu-id="2d7e7-103">Assembly location</span></span>

<span data-ttu-id="2d7e7-104">O local de um assembly determina se o Common Language Runtime pode localizá-lo quando referenciado, bem como pode determinar se o assembly pode ser compartilhado com outros assemblies.</span><span class="sxs-lookup"><span data-stu-id="2d7e7-104">An assembly's location determines whether the common language runtime can locate it when referenced, and can also determine whether the assembly can be shared with other assemblies.</span></span> <span data-ttu-id="2d7e7-105">Você pode implantar um assembly nos seguintes locais:</span><span class="sxs-lookup"><span data-stu-id="2d7e7-105">You can deploy an assembly in the following locations:</span></span>

- <span data-ttu-id="2d7e7-106">No diretório ou subdiretórios do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2d7e7-106">The application's directory or subdirectories.</span></span>

     <span data-ttu-id="2d7e7-107">Esse é o local mais comum para implantar um assembly.</span><span class="sxs-lookup"><span data-stu-id="2d7e7-107">This is the most common location for deploying an assembly.</span></span> <span data-ttu-id="2d7e7-108">Os subdiretórios do diretório raiz de um aplicativo podem ser baseados na linguagem ou cultura.</span><span class="sxs-lookup"><span data-stu-id="2d7e7-108">The subdirectories of an application's root directory can be based on language or culture.</span></span> <span data-ttu-id="2d7e7-109">Se um assembly tiver informações no atributo de cultura, ele deverá estar em um subdiretório no diretório do aplicativo com o nome dessa cultura.</span><span class="sxs-lookup"><span data-stu-id="2d7e7-109">If an assembly has information in the culture attribute, it must be in a subdirectory under the application directory with that culture's name.</span></span>

- <span data-ttu-id="2d7e7-110">O cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="2d7e7-110">The global assembly cache.</span></span>

     <span data-ttu-id="2d7e7-111">Esse é um cache de código da máquina toda que é instalado sempre que o Common Language Runtime é instalado.</span><span class="sxs-lookup"><span data-stu-id="2d7e7-111">This is a machine-wide code cache that is installed wherever the common language runtime is installed.</span></span> <span data-ttu-id="2d7e7-112">Na maioria das vezes, se você pretende compartilhar um assembly com vários aplicativos, é preciso implantá-lo no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="2d7e7-112">In most cases, if you intend to share an assembly with multiple applications, you should deploy it into the global assembly cache.</span></span>

- <span data-ttu-id="2d7e7-113">Em um servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="2d7e7-113">On an HTTP server.</span></span>

     <span data-ttu-id="2d7e7-114">Um assembly implantado em um servidor HTTP deve ter um nome forte; você aponta para o assembly na seção de base de código do arquivo de configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2d7e7-114">An assembly deployed on an HTTP server must have a strong name; you point to the assembly in the codebase section of the application's configuration file.</span></span>

## <a name="see-also"></a><span data-ttu-id="2d7e7-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="2d7e7-115">See also</span></span>

- [<span data-ttu-id="2d7e7-116">Criar assemblies</span><span class="sxs-lookup"><span data-stu-id="2d7e7-116">Create assemblies</span></span>](create.md)
- [<span data-ttu-id="2d7e7-117">Cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="2d7e7-117">Global assembly cache</span></span>](../../framework/app-domains/gac.md)
- [<span data-ttu-id="2d7e7-118">Como o tempo de execução localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="2d7e7-118">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
