---
title: Conteúdo de um assembly
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- assemblies [.NET Framework], single-file
- single-file assemblies
- multifile assemblies
ms.assetid: 28116714-da77-45f7-826d-fa035d121948
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 27bbc1b382d962379a50fba4557e3f2a408d9bc4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54649161"
---
# <a name="assembly-contents"></a><span data-ttu-id="25b4b-102">Conteúdo de um assembly</span><span class="sxs-lookup"><span data-stu-id="25b4b-102">Assembly Contents</span></span>
<span data-ttu-id="25b4b-103">Em geral, um assembly estático pode consistir em quatro elementos:</span><span class="sxs-lookup"><span data-stu-id="25b4b-103">In general, a static assembly can consist of four elements:</span></span>  
  
-   <span data-ttu-id="25b4b-104">O [manifesto do assembly](../../../docs/framework/app-domains/assembly-manifest.md), que contém metadados do assembly.</span><span class="sxs-lookup"><span data-stu-id="25b4b-104">The [assembly manifest](../../../docs/framework/app-domains/assembly-manifest.md), which contains assembly metadata.</span></span>  
  
-   <span data-ttu-id="25b4b-105">Metadados de tipo.</span><span class="sxs-lookup"><span data-stu-id="25b4b-105">Type metadata.</span></span>  
  
-   <span data-ttu-id="25b4b-106">Código MSIL (Microsoft Intermediate Language) que implementa os tipos.</span><span class="sxs-lookup"><span data-stu-id="25b4b-106">Microsoft intermediate language (MSIL) code that implements the types.</span></span>  
  
-   <span data-ttu-id="25b4b-107">Um conjunto de recursos.</span><span class="sxs-lookup"><span data-stu-id="25b4b-107">A set of resources.</span></span>  
  
 <span data-ttu-id="25b4b-108">Somente o manifesto do assembly é obrigatório, mas tipos e recursos são necessários para atribuir ao assembly uma funcionalidade significativa.</span><span class="sxs-lookup"><span data-stu-id="25b4b-108">Only the assembly manifest is required, but either types or resources are needed to give the assembly any meaningful functionality.</span></span>  
  
 <span data-ttu-id="25b4b-109">Há várias maneiras de se agrupar esses elementos em um assembly.</span><span class="sxs-lookup"><span data-stu-id="25b4b-109">There are several ways to group these elements in an assembly.</span></span> <span data-ttu-id="25b4b-110">Você pode agrupar todos os elementos em um único arquivo físico, mostrado na ilustração a seguir.</span><span class="sxs-lookup"><span data-stu-id="25b4b-110">You can group all elements in a single physical file, which is shown in the following illustration.</span></span>  
  
 <span data-ttu-id="25b4b-111">![MyAssembly.dll](../../../docs/framework/app-domains/media/assemblyover1.gif "assemblyover1")</span><span class="sxs-lookup"><span data-stu-id="25b4b-111">![MyAssembly.dll](../../../docs/framework/app-domains/media/assemblyover1.gif "assemblyover1")</span></span>  
<span data-ttu-id="25b4b-112">Assembly de arquivo único</span><span class="sxs-lookup"><span data-stu-id="25b4b-112">Single-file assembly</span></span>  
  
 <span data-ttu-id="25b4b-113">Como alternativa, os elementos de um assembly podem estar contidos em vários arquivos.</span><span class="sxs-lookup"><span data-stu-id="25b4b-113">Alternatively, the elements of an assembly can be contained in several files.</span></span> <span data-ttu-id="25b4b-114">Esses arquivos podem ser módulos de código compilado (.netmodule), recursos (como arquivos .bmp ou .jpg) ou outros arquivos exigidos pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="25b4b-114">These files can be modules of compiled code (.netmodule), resources (such as .bmp or .jpg files), or other files required by the application.</span></span> <span data-ttu-id="25b4b-115">Crie um assembly de vários arquivos quando quiser combinar módulos escritos em diferentes linguagens e otimizar o download de um aplicativo colocando tipos pouco usados em um módulo baixado apenas quando necessário.</span><span class="sxs-lookup"><span data-stu-id="25b4b-115">Create a multifile assembly when you want to combine modules written in different languages and to optimize downloading an application by putting seldom used types in a module that is downloaded only when needed.</span></span>  
  
 <span data-ttu-id="25b4b-116">Na ilustração a seguir, o desenvolvedor de um aplicativo hipotético optou por separar alguns códigos de utilitários em um módulo diferente e manter um arquivo de recurso grande (neste caso, uma imagem .bmp) em seu arquivo original.</span><span class="sxs-lookup"><span data-stu-id="25b4b-116">In the following illustration, the developer of a hypothetical application has chosen to separate some utility code into a different module and to keep a large resource file (in this case a .bmp image) in its original file.</span></span> <span data-ttu-id="25b4b-117">O .NET Framework só baixa um arquivo quando ele é referenciado; manter códigos pouco referenciados em um arquivo separado do aplicativo otimiza o download do código.</span><span class="sxs-lookup"><span data-stu-id="25b4b-117">The .NET Framework downloads a file only when it is referenced; keeping infrequently referenced code in a separate file from the application optimizes code download.</span></span>  
  
 <span data-ttu-id="25b4b-118">![MyAssembly.dll](../../../docs/framework/app-domains/media/assemblyover2.gif "assemblyover2")</span><span class="sxs-lookup"><span data-stu-id="25b4b-118">![MyAssembly.dll](../../../docs/framework/app-domains/media/assemblyover2.gif "assemblyover2")</span></span>  
<span data-ttu-id="25b4b-119">Assembly de vários arquivos</span><span class="sxs-lookup"><span data-stu-id="25b4b-119">Multifile assembly</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="25b4b-120">Os arquivos que compõem um assembly de vários arquivos não estão fisicamente vinculados pelo sistema de arquivos.</span><span class="sxs-lookup"><span data-stu-id="25b4b-120">The files that make up a multifile assembly are not physically linked by the file system.</span></span> <span data-ttu-id="25b4b-121">Em vez disso, eles estão vinculados por meio do manifesto de assembly, e o Common Language Runtime os gerencia como uma unidade.</span><span class="sxs-lookup"><span data-stu-id="25b4b-121">Rather, they are linked through the assembly manifest and the common language runtime manages them as a unit.</span></span>  
  
 <span data-ttu-id="25b4b-122">Nesta ilustração, todos os três arquivos pertencem a um assembly, conforme descrito no manifesto de assembly contido em MyAssembly.dll.</span><span class="sxs-lookup"><span data-stu-id="25b4b-122">In this illustration, all three files belong to an assembly, as described in the assembly manifest contained in MyAssembly.dll.</span></span> <span data-ttu-id="25b4b-123">No sistema de arquivos, eles são três arquivos separados.</span><span class="sxs-lookup"><span data-stu-id="25b4b-123">To the file system, they are three separate files.</span></span> <span data-ttu-id="25b4b-124">Observe que o arquivo Util.netmodule foi compilado como um módulo porque não contém informações de assembly.</span><span class="sxs-lookup"><span data-stu-id="25b4b-124">Note that the file Util.netmodule was compiled as a module because it contains no assembly information.</span></span> <span data-ttu-id="25b4b-125">Quando o assembly foi criado, o manifesto do assembly foi adicionado a MyAssembly.dll, indicando seu relacionamento com Util.netmodule e Graphic.bmp.</span><span class="sxs-lookup"><span data-stu-id="25b4b-125">When the assembly was created, the assembly manifest was added to MyAssembly.dll, indicating its relationship with Util.netmodule and Graphic.bmp.</span></span>  
  
 <span data-ttu-id="25b4b-126">À medida que cria seu código-fonte, você toma decisões sobre como particionar a funcionalidade do seu aplicativo em um ou mais arquivos.</span><span class="sxs-lookup"><span data-stu-id="25b4b-126">As you currently design your source code, you make explicit decisions about how to partition the functionality of your application into one or more files.</span></span> <span data-ttu-id="25b4b-127">Ao criar código do .NET Framework, você tomará decisões semelhantes sobre como particionar a funcionalidade em um ou mais assemblies.</span><span class="sxs-lookup"><span data-stu-id="25b4b-127">When designing .NET Framework code, you will make similar decisions about how to partition the functionality into one or more assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25b4b-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="25b4b-128">See also</span></span>
- [<span data-ttu-id="25b4b-129">Assemblies no Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="25b4b-129">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
- [<span data-ttu-id="25b4b-130">Manifesto do assembly</span><span class="sxs-lookup"><span data-stu-id="25b4b-130">Assembly Manifest</span></span>](../../../docs/framework/app-domains/assembly-manifest.md)
- [<span data-ttu-id="25b4b-131">Considerações sobre segurança de assembly</span><span class="sxs-lookup"><span data-stu-id="25b4b-131">Assembly Security Considerations</span></span>](../../../docs/framework/app-domains/assembly-security-considerations.md)
