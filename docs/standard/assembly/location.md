---
title: Localização do assembly
ms.date: 08/20/2019
helpviewer_keywords:
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 9f1f41a7-2954-49d3-a2c0-62b6ef4d40ab
ms.openlocfilehash: d44fb44db35b60f99583c20432c5998573298044
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107210"
---
# <a name="assembly-location"></a><span data-ttu-id="6bb05-102">Localização do assembly</span><span class="sxs-lookup"><span data-stu-id="6bb05-102">Assembly location</span></span>
<span data-ttu-id="6bb05-103">O local de um assembly determina se o Common Language Runtime pode localizá-lo quando referenciado, bem como pode determinar se o assembly pode ser compartilhado com outros assemblies.</span><span class="sxs-lookup"><span data-stu-id="6bb05-103">An assembly's location determines whether the common language runtime can locate it when referenced, and can also determine whether the assembly can be shared with other assemblies.</span></span> <span data-ttu-id="6bb05-104">Você pode implantar um assembly nos seguintes locais:</span><span class="sxs-lookup"><span data-stu-id="6bb05-104">You can deploy an assembly in the following locations:</span></span>  
  
- <span data-ttu-id="6bb05-105">No diretório ou subdiretórios do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6bb05-105">The application's directory or subdirectories.</span></span>  
  
     <span data-ttu-id="6bb05-106">Esse é o local mais comum para implantar um assembly.</span><span class="sxs-lookup"><span data-stu-id="6bb05-106">This is the most common location for deploying an assembly.</span></span> <span data-ttu-id="6bb05-107">Os subdiretórios do diretório raiz de um aplicativo podem ser baseados na linguagem ou cultura.</span><span class="sxs-lookup"><span data-stu-id="6bb05-107">The subdirectories of an application's root directory can be based on language or culture.</span></span> <span data-ttu-id="6bb05-108">Se um assembly tiver informações no atributo de cultura, ele deverá estar em um subdiretório no diretório do aplicativo com o nome dessa cultura.</span><span class="sxs-lookup"><span data-stu-id="6bb05-108">If an assembly has information in the culture attribute, it must be in a subdirectory under the application directory with that culture's name.</span></span>  
  
- <span data-ttu-id="6bb05-109">O cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="6bb05-109">The global assembly cache.</span></span>  
  
     <span data-ttu-id="6bb05-110">Esse é um cache de código da máquina toda que é instalado sempre que o Common Language Runtime é instalado.</span><span class="sxs-lookup"><span data-stu-id="6bb05-110">This is a machine-wide code cache that is installed wherever the common language runtime is installed.</span></span> <span data-ttu-id="6bb05-111">Na maioria das vezes, se você pretende compartilhar um assembly com vários aplicativos, é preciso implantá-lo no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="6bb05-111">In most cases, if you intend to share an assembly with multiple applications, you should deploy it into the global assembly cache.</span></span>  
  
- <span data-ttu-id="6bb05-112">Em um servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="6bb05-112">On an HTTP server.</span></span>  
  
     <span data-ttu-id="6bb05-113">Um assembly implantado em um servidor HTTP deve ter um nome forte; você aponta para o assembly na seção de base de código do arquivo de configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6bb05-113">An assembly deployed on an HTTP server must have a strong name; you point to the assembly in the codebase section of the application's configuration file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bb05-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6bb05-114">See also</span></span>

- [<span data-ttu-id="6bb05-115">Criar assemblies</span><span class="sxs-lookup"><span data-stu-id="6bb05-115">Create assemblies</span></span>](create.md)
- [<span data-ttu-id="6bb05-116">Cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="6bb05-116">Global assembly cache</span></span>](../../framework/app-domains/gac.md)
- [<span data-ttu-id="6bb05-117">Como o tempo de execução localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="6bb05-117">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="6bb05-118">Programa com assemblies</span><span class="sxs-lookup"><span data-stu-id="6bb05-118">Program with assemblies</span></span>](program.md)
