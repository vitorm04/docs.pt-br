---
title: Instalar um assembly no GAC
ms.date: 09/20/2018
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
- windows installer, global assembly cache
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d365ac77fe6cd7fc4fca36705729ec12b06d6830
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2018
ms.locfileid: "46584575"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a><span data-ttu-id="08eeb-102">Como instalar um assembly no cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="08eeb-102">How to: Install an assembly into the global assembly cache</span></span>

<span data-ttu-id="08eeb-103">Há duas maneiras de instalar um assembly com nome forte no GAC (Cache de Assembly Global).</span><span class="sxs-lookup"><span data-stu-id="08eeb-103">There are two ways to install a strong-named assembly into the global assembly cache (GAC).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="08eeb-104">Apenas os assemblies com nome forte podem ser instalados no GAC.</span><span class="sxs-lookup"><span data-stu-id="08eeb-104">Only strong-named assemblies can be installed into the GAC.</span></span> <span data-ttu-id="08eeb-105">Para obter informações sobre como criar um assembly de nome forte, consulte [Como assinar um assembly com um nome forte](how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="08eeb-105">For information about how to create a strong-named assembly, see [How to: Sign an Assembly with a Strong Name](how-to-sign-an-assembly-with-a-strong-name.md).</span></span>

## <a name="windows-installer"></a><span data-ttu-id="08eeb-106">Windows Installer</span><span class="sxs-lookup"><span data-stu-id="08eeb-106">Windows Installer</span></span>

<span data-ttu-id="08eeb-107">[Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), o mecanismo de instalação do Windows, é a maneira recomendada de adicionar assemblies ao cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="08eeb-107">[Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), the Windows installation engine, is the recommended way to add assemblies to the global assembly cache.</span></span> <span data-ttu-id="08eeb-108">O Windows Installer fornece uma contagem de referências de assemblies no cache de assembly global e outros benefícios.</span><span class="sxs-lookup"><span data-stu-id="08eeb-108">Windows Installer provides reference counting of assemblies in the global assembly cache and other benefits.</span></span> <span data-ttu-id="08eeb-109">É possível usar a extensão do [WiX Toolset para Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension) para criar um pacote de instalador para o Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="08eeb-109">You can use the [WiX Toolset extension for Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension) to create an installer package for Windows Installer.</span></span>

## <a name="global-assembly-cache-tool"></a><span data-ttu-id="08eeb-110">Ferramenta de Cache de Assembly Global</span><span class="sxs-lookup"><span data-stu-id="08eeb-110">Global assembly cache tool</span></span>

<span data-ttu-id="08eeb-111">É possível usar a [Ferramenta de Cache de Assembly Global (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) para adicionar assemblies com nome forte ao cache de assembly global e para exibir o conteúdo desse cache.</span><span class="sxs-lookup"><span data-stu-id="08eeb-111">You can use the [Global assembly cache tool (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to add strong-named assemblies to the global assembly cache and to view the contents of the global assembly cache.</span></span>

   > [!NOTE]
   > <span data-ttu-id="08eeb-112">Gacutil.exe destina-se a fins de desenvolvimento e não deve ser usado para instalar assemblies de produção no Cache de Assembly Global.</span><span class="sxs-lookup"><span data-stu-id="08eeb-112">Gacutil.exe is only for development purposes and should not be used to install production assemblies into the global assembly cache.</span></span>

<span data-ttu-id="08eeb-113">A sintaxe de gacutil é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="08eeb-113">The syntax for gacutil is as follows:</span></span>

```shell
gacutil -i <assembly name>
```

<span data-ttu-id="08eeb-114">Neste comando, *nome do assembly* é o nome do assembly a ser instalado no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="08eeb-114">In this command, *assembly name* is the name of the assembly to install in the global assembly cache.</span></span>

<span data-ttu-id="08eeb-115">O exemplo a seguir instala um assembly com nome de arquivo `hello.dll` no Cache de Assembly Global.</span><span class="sxs-lookup"><span data-stu-id="08eeb-115">The following example installs an assembly with the file name `hello.dll` into the global assembly cache.</span></span>

```shell
gacutil -i hello.dll
```

> [!NOTE]
> <span data-ttu-id="08eeb-116">Nas versões anteriores do .NET Framework, a extensão do shell do Windows Shfusion.dll permitia instalar assemblies arrastando-os no **Explorador de Arquivos**.</span><span class="sxs-lookup"><span data-stu-id="08eeb-116">In earlier versions of the .NET Framework, the Shfusion.dll Windows shell extension enabled you to install assemblies by dragging them in **File Explorer**.</span></span> <span data-ttu-id="08eeb-117">Do .NET Framework 4 em diante, a Shfusion.dll tornou-se obsoleta.</span><span class="sxs-lookup"><span data-stu-id="08eeb-117">Beginning with the .NET Framework 4, Shfusion.dll is obsolete.</span></span>

## <a name="see-also"></a><span data-ttu-id="08eeb-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="08eeb-118">See also</span></span>

- [<span data-ttu-id="08eeb-119">Como trabalhar com assemblies e o cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="08eeb-119">Working with Assemblies and the Global Assembly Cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="08eeb-120">Como remover um assembly do cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="08eeb-120">How to: Remove an Assembly from the Global Assembly Cache</span></span>](how-to-remove-an-assembly-from-the-gac.md)
- [<span data-ttu-id="08eeb-121">Gacutil.exe (Ferramenta do Cache de Assemblies Global)</span><span class="sxs-lookup"><span data-stu-id="08eeb-121">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
- [<span data-ttu-id="08eeb-122">Como assinar um assembly com um nome forte</span><span class="sxs-lookup"><span data-stu-id="08eeb-122">How to: Sign an Assembly with a Strong Name</span></span>](how-to-sign-an-assembly-with-a-strong-name.md)