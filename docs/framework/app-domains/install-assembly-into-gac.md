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
ms.openlocfilehash: e670f5dba47393b7df047fb4e6f7d92df8cb187c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119803"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a><span data-ttu-id="8e35e-102">Como instalar um assembly no cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="8e35e-102">How to: Install an assembly into the global assembly cache</span></span>

<span data-ttu-id="8e35e-103">O cache de assembly global armazena os assemblies que vários aplicativos compartilham.</span><span class="sxs-lookup"><span data-stu-id="8e35e-103">The global assembly cache (GAC) stores assemblies that several applications share.</span></span> <span data-ttu-id="8e35e-104">Instale um assembly no [cache de assembly global](gac.md) com um dos seguintes componentes:</span><span class="sxs-lookup"><span data-stu-id="8e35e-104">Install an assembly into the [global assembly cache](gac.md) with one of the following components:</span></span> 

- [<span data-ttu-id="8e35e-105">Windows Installer</span><span class="sxs-lookup"><span data-stu-id="8e35e-105">Windows Installer</span></span>](#windows-installer)
- [<span data-ttu-id="8e35e-106">Ferramenta cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="8e35e-106">Global Assembly Cache tool</span></span>](#global-assembly-cache-tool)

> [!IMPORTANT]
> <span data-ttu-id="8e35e-107">Você pode instalar somente assemblies de nome forte no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="8e35e-107">You can install only strong-named assemblies into the global assembly cache.</span></span> <span data-ttu-id="8e35e-108">Para obter informações sobre como criar um assembly de nome forte, consulte [como assinar um assembly com um nome forte](../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="8e35e-108">For information about how to create a strong-named assembly, see [How to: Sign an assembly with a strong name](../../standard/assembly/sign-strong-name.md).</span></span>

## <a name="windows-installer"></a><span data-ttu-id="8e35e-109">Windows Installer</span><span class="sxs-lookup"><span data-stu-id="8e35e-109">Windows Installer</span></span>

<span data-ttu-id="8e35e-110">[Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), o mecanismo de instalação do Windows, é a maneira recomendada de adicionar assemblies ao cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="8e35e-110">[Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), the Windows installation engine, is the recommended way to add assemblies to the global assembly cache.</span></span> <span data-ttu-id="8e35e-111">O Windows Installer fornece uma contagem de referências de assemblies no cache de assembly global e outros benefícios.</span><span class="sxs-lookup"><span data-stu-id="8e35e-111">Windows Installer provides reference counting of assemblies in the global assembly cache and other benefits.</span></span> <span data-ttu-id="8e35e-112">Para criar um pacote do instalador do Windows Installer, use a [extensão de conjunto de ferramentas WiX do Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).</span><span class="sxs-lookup"><span data-stu-id="8e35e-112">To create an installer package for Windows Installer, use the [WiX toolset extension for Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).</span></span>

## <a name="global-assembly-cache-tool"></a><span data-ttu-id="8e35e-113">Ferramenta Cache de Assembly Global</span><span class="sxs-lookup"><span data-stu-id="8e35e-113">Global Assembly Cache tool</span></span>

<span data-ttu-id="8e35e-114">Você pode usar o [Utilitário de cache de assembly global do .net (Gacutil. exe)](../tools/gacutil-exe-gac-tool.md) para adicionar assemblies ao cache de assembly global e para exibir o conteúdo do cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="8e35e-114">You can use the [.NET Global Assembly Cache utility (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to add assemblies to the global assembly cache and to view the contents of the global assembly cache.</span></span>

   > [!NOTE]
   > <span data-ttu-id="8e35e-115">O *gacutil.exe* é indicado apenas para fins de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="8e35e-115">*Gacutil.exe* is for development purposes only.</span></span> <span data-ttu-id="8e35e-116">Não o use para instalar assemblies de produção no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="8e35e-116">Don't use it to install production assemblies into the global assembly cache.</span></span>

<span data-ttu-id="8e35e-117">A sintaxe para usar o *gacutil.exe* para instalar um assembly no cache de assembly global é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="8e35e-117">The syntax for using *gacutil.exe* to install an assembly in the GAC is as follows:</span></span>

```cmd
gacutil -i <assembly name>
```

<span data-ttu-id="8e35e-118">Nesse comando, *\<assembly name>* é o nome do assembly a ser instalado no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="8e35e-118">In this command, *\<assembly name>* is the name of the assembly to install in the global assembly cache.</span></span>

<span data-ttu-id="8e35e-119">Se o *Gacutil. exe* não estiver no caminho do sistema, use o [prompt de comando do desenvolvedor para o VS *\<versão >* ](../tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="8e35e-119">If *gacutil.exe* isn't in your system path, use the [Developer command prompt for VS *\<version>*](../tools/developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="8e35e-120">O exemplo a seguir instala um assembly com o nome do arquivo *hello.dll* no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="8e35e-120">The following example installs an assembly with the file name *hello.dll* into the global assembly cache.</span></span>

```cmd
gacutil -i hello.dll
```

> [!NOTE]
> <span data-ttu-id="8e35e-121">Nas versões anteriores do .NET Framework, a extensão do shell do Windows *Shfusion.dll* permitia a instalação de assemblies arrastando-os no Explorador de Arquivos.</span><span class="sxs-lookup"><span data-stu-id="8e35e-121">In earlier versions of the .NET Framework, the *Shfusion.dll* Windows shell extension let you install assemblies by dragging them to File Explorer.</span></span> <span data-ttu-id="8e35e-122">Começando no .NET Framework 4, a *Shfusion.dll* ficou obsoleta.</span><span class="sxs-lookup"><span data-stu-id="8e35e-122">Beginning with .NET Framework 4, *Shfusion.dll* is obsolete.</span></span>

## <a name="see-also"></a><span data-ttu-id="8e35e-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8e35e-123">See also</span></span>

- [<span data-ttu-id="8e35e-124">Trabalhar com assemblies e o cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="8e35e-124">Work with assemblies and the global assembly cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="8e35e-125">Como: remover um assembly do cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="8e35e-125">How to: Remove an assembly from the global assembly cache</span></span>](how-to-remove-an-assembly-from-the-gac.md)
- [<span data-ttu-id="8e35e-126">Gacutil. exe (ferramenta global assembly cache)</span><span class="sxs-lookup"><span data-stu-id="8e35e-126">Gacutil.exe (Global Assembly Cache tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
- [<span data-ttu-id="8e35e-127">Como assinar um assembly com um nome forte</span><span class="sxs-lookup"><span data-stu-id="8e35e-127">How to: Sign an assembly with a strong name</span></span>](../../standard/assembly/sign-strong-name.md)
