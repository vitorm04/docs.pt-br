---
title: Local de um assembly
ms.date: 03/30/2017
helpviewer_keywords:
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 9f1f41a7-2954-49d3-a2c0-62b6ef4d40ab
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c638531bd54f14c7e4b04a093deaec729db404ba
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59129630"
---
# <a name="assembly-location"></a><span data-ttu-id="23a18-102">Local de um assembly</span><span class="sxs-lookup"><span data-stu-id="23a18-102">Assembly Location</span></span>
<span data-ttu-id="23a18-103">O local de um assembly determina se o Common Language Runtime pode localizá-lo quando referenciado, bem como pode determinar se o assembly pode ser compartilhado com outros assemblies.</span><span class="sxs-lookup"><span data-stu-id="23a18-103">An assembly's location determines whether the common language runtime can locate it when referenced, and can also determine whether the assembly can be shared with other assemblies.</span></span> <span data-ttu-id="23a18-104">Você pode implantar um assembly nos seguintes locais:</span><span class="sxs-lookup"><span data-stu-id="23a18-104">You can deploy an assembly in the following locations:</span></span>  
  
-   <span data-ttu-id="23a18-105">No diretório ou subdiretórios do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="23a18-105">The application's directory or subdirectories.</span></span>  
  
     <span data-ttu-id="23a18-106">Esse é o local mais comum para implantar um assembly.</span><span class="sxs-lookup"><span data-stu-id="23a18-106">This is the most common location for deploying an assembly.</span></span> <span data-ttu-id="23a18-107">Os subdiretórios do diretório raiz de um aplicativo podem ser baseados na linguagem ou cultura.</span><span class="sxs-lookup"><span data-stu-id="23a18-107">The subdirectories of an application's root directory can be based on language or culture.</span></span> <span data-ttu-id="23a18-108">Se um assembly tiver informações no atributo de cultura, ele deverá estar em um subdiretório no diretório do aplicativo com o nome dessa cultura.</span><span class="sxs-lookup"><span data-stu-id="23a18-108">If an assembly has information in the culture attribute, it must be in a subdirectory under the application directory with that culture's name.</span></span>  
  
-   <span data-ttu-id="23a18-109">O cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="23a18-109">The global assembly cache.</span></span>  
  
     <span data-ttu-id="23a18-110">Esse é um cache de código da máquina toda que é instalado sempre que o Common Language Runtime é instalado.</span><span class="sxs-lookup"><span data-stu-id="23a18-110">This is a machine-wide code cache that is installed wherever the common language runtime is installed.</span></span> <span data-ttu-id="23a18-111">Na maioria das vezes, se você pretende compartilhar um assembly com vários aplicativos, é preciso implantá-lo no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="23a18-111">In most cases, if you intend to share an assembly with multiple applications, you should deploy it into the global assembly cache.</span></span>  
  
-   <span data-ttu-id="23a18-112">Em um servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="23a18-112">On an HTTP server.</span></span>  
  
     <span data-ttu-id="23a18-113">Um assembly implantado em um servidor HTTP deve ter um nome forte; você aponta para o assembly na seção de base de código do arquivo de configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="23a18-113">An assembly deployed on an HTTP server must have a strong name; you point to the assembly in the codebase section of the application's configuration file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23a18-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="23a18-114">See also</span></span>

- [<span data-ttu-id="23a18-115">Criação de assemblies</span><span class="sxs-lookup"><span data-stu-id="23a18-115">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)
- [<span data-ttu-id="23a18-116">Cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="23a18-116">Global Assembly Cache</span></span>](../../../docs/framework/app-domains/gac.md)
- [<span data-ttu-id="23a18-117">Como o tempo de execução localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="23a18-117">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="23a18-118">Programação com assemblies</span><span class="sxs-lookup"><span data-stu-id="23a18-118">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
