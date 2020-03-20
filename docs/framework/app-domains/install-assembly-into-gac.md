---
title: Como instalar um assembly no cache de assembly global
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
- windows installer, global assembly cache
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
ms.openlocfilehash: 64878a795a7c5b790c8991064e32b82505685c0c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155557"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a><span data-ttu-id="d787d-102">Como instalar um assembly no cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="d787d-102">How to: Install an assembly into the global assembly cache</span></span>

<span data-ttu-id="d787d-103">O cache de assembly global armazena os assemblies que vários aplicativos compartilham.</span><span class="sxs-lookup"><span data-stu-id="d787d-103">The global assembly cache (GAC) stores assemblies that several applications share.</span></span> <span data-ttu-id="d787d-104">Instale um assembly no [cache de assembly global](gac.md) com um dos seguintes componentes:</span><span class="sxs-lookup"><span data-stu-id="d787d-104">Install an assembly into the [global assembly cache](gac.md) with one of the following components:</span></span>

- [<span data-ttu-id="d787d-105">Instalador do Windows</span><span class="sxs-lookup"><span data-stu-id="d787d-105">Windows Installer</span></span>](#windows-installer)
- [<span data-ttu-id="d787d-106">Ferramenta Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="d787d-106">Global Assembly Cache tool</span></span>](#global-assembly-cache-tool)

> [!IMPORTANT]
> <span data-ttu-id="d787d-107">Você pode instalar apenas conjuntos com nome forte no cache de montagem global.</span><span class="sxs-lookup"><span data-stu-id="d787d-107">You can install only strong-named assemblies into the global assembly cache.</span></span> <span data-ttu-id="d787d-108">Para obter informações sobre como criar um conjunto com nome forte, consulte [Como: Assinar uma montagem com um nome forte](../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="d787d-108">For information about how to create a strong-named assembly, see [How to: Sign an assembly with a strong name](../../standard/assembly/sign-strong-name.md).</span></span>

## <a name="windows-installer"></a><span data-ttu-id="d787d-109">Windows Installer</span><span class="sxs-lookup"><span data-stu-id="d787d-109">Windows Installer</span></span>

<span data-ttu-id="d787d-110">[Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), o mecanismo de instalação do Windows, é a maneira recomendada de adicionar assemblies ao cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="d787d-110">[Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), the Windows installation engine, is the recommended way to add assemblies to the global assembly cache.</span></span> <span data-ttu-id="d787d-111">O Windows Installer fornece uma contagem de referências de assemblies no cache de assembly global e outros benefícios.</span><span class="sxs-lookup"><span data-stu-id="d787d-111">Windows Installer provides reference counting of assemblies in the global assembly cache and other benefits.</span></span> <span data-ttu-id="d787d-112">Para criar um pacote do instalador do Windows Installer, use a [extensão de conjunto de ferramentas WiX do Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).</span><span class="sxs-lookup"><span data-stu-id="d787d-112">To create an installer package for Windows Installer, use the [WiX toolset extension for Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).</span></span>

## <a name="global-assembly-cache-tool"></a><span data-ttu-id="d787d-113">Ferramenta Cache de Assembly Global</span><span class="sxs-lookup"><span data-stu-id="d787d-113">Global Assembly Cache tool</span></span>

<span data-ttu-id="d787d-114">Você pode usar o [utilitário .NET Global Assembly Cache (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) para adicionar montagens ao cache de montagem global e visualizar o conteúdo do cache de montagem global.</span><span class="sxs-lookup"><span data-stu-id="d787d-114">You can use the [.NET Global Assembly Cache utility (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to add assemblies to the global assembly cache and to view the contents of the global assembly cache.</span></span>

   > [!NOTE]
   > <span data-ttu-id="d787d-115">O *gacutil.exe* é indicado apenas para fins de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="d787d-115">*Gacutil.exe* is for development purposes only.</span></span> <span data-ttu-id="d787d-116">Não o use para instalar assemblies de produção no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="d787d-116">Don't use it to install production assemblies into the global assembly cache.</span></span>

<span data-ttu-id="d787d-117">A sintaxe para usar o *gacutil.exe* para instalar um assembly no cache de assembly global é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="d787d-117">The syntax for using *gacutil.exe* to install an assembly in the GAC is as follows:</span></span>

```cmd
gacutil -i <assembly name>
```

<span data-ttu-id="d787d-118">Neste comando, \* \<o nome de montagem>\* é o nome do conjunto a ser instalado no cache de montagem global.</span><span class="sxs-lookup"><span data-stu-id="d787d-118">In this command, *\<assembly name>* is the name of the assembly to install in the global assembly cache.</span></span>

<span data-ttu-id="d787d-119">Se *gacutil.exe* não estiver no caminho do sistema, use o [prompt de comando do Desenvolvedor para>de \* \<versão \*VS ](../tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="d787d-119">If *gacutil.exe* isn't in your system path, use the [Developer command prompt for VS *\<version>*](../tools/developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="d787d-120">O exemplo a seguir instala um assembly com o nome do arquivo *hello.dll* no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="d787d-120">The following example installs an assembly with the file name *hello.dll* into the global assembly cache.</span></span>

```cmd
gacutil -i hello.dll
```

> [!NOTE]
> <span data-ttu-id="d787d-121">Nas versões anteriores do .NET Framework, a extensão do shell do Windows *Shfusion.dll* permitia a instalação de assemblies arrastando-os no Explorador de Arquivos.</span><span class="sxs-lookup"><span data-stu-id="d787d-121">In earlier versions of the .NET Framework, the *Shfusion.dll* Windows shell extension let you install assemblies by dragging them to File Explorer.</span></span> <span data-ttu-id="d787d-122">Começando no .NET Framework 4, a *Shfusion.dll* ficou obsoleta.</span><span class="sxs-lookup"><span data-stu-id="d787d-122">Beginning with .NET Framework 4, *Shfusion.dll* is obsolete.</span></span>

## <a name="see-also"></a><span data-ttu-id="d787d-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="d787d-123">See also</span></span>

- [<span data-ttu-id="d787d-124">Trabalhe com montagens e o cache de montagem global</span><span class="sxs-lookup"><span data-stu-id="d787d-124">Work with assemblies and the global assembly cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="d787d-125">Como: Remover uma montagem do cache de montagem global</span><span class="sxs-lookup"><span data-stu-id="d787d-125">How to: Remove an assembly from the global assembly cache</span></span>](how-to-remove-an-assembly-from-the-gac.md)
- [<span data-ttu-id="d787d-126">Gacutil.exe (ferramenta Global Assembly Cache)</span><span class="sxs-lookup"><span data-stu-id="d787d-126">Gacutil.exe (Global Assembly Cache tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
- [<span data-ttu-id="d787d-127">Como: Assinar uma assembléia com um nome forte</span><span class="sxs-lookup"><span data-stu-id="d787d-127">How to: Sign an assembly with a strong name</span></span>](../../standard/assembly/sign-strong-name.md)
