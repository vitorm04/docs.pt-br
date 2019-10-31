---
title: Como exibir o conteúdo do cache de assemblies global
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- global assembly cache, viewing contents
- viewing assemblies in global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- GAC (global assembly cache), viewing contents
- list of assemblies in global assembly cache
- Global Assembly Cache tool
ms.assetid: c5f786a0-969b-4f14-9f02-e77c3384d9af
ms.openlocfilehash: b5d8b31e7eb23789878da620f3a4517056a1ee3e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119832"
---
# <a name="how-to-view-the-contents-of-the-global-assembly-cache"></a><span data-ttu-id="b76c7-102">Como exibir o conteúdo do cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="b76c7-102">How to: View the contents of the global assembly cache</span></span>

<span data-ttu-id="b76c7-103">Use a [Ferramenta de Cache de Assembly Global (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) para exibir o conteúdo do GAC (cache de assembly global).</span><span class="sxs-lookup"><span data-stu-id="b76c7-103">Use the [global assembly cache tool (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to view the contents of the global assembly cache (GAC).</span></span>

## <a name="view-the-assemblies-in-the-gac"></a><span data-ttu-id="b76c7-104">Exibir os assemblies no GAC</span><span class="sxs-lookup"><span data-stu-id="b76c7-104">View the assemblies in the GAC</span></span>

<span data-ttu-id="b76c7-105">Para exibir uma lista de assemblies no cache de assembly global, abra o [Prompt de Comando do Desenvolvedor para Visual Studio](../tools/developer-command-prompt-for-vs.md) e, em seguida, digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="b76c7-105">To view a list of the assemblies in the global assembly cache, open [Developer Command Prompt for Visual Studio](../tools/developer-command-prompt-for-vs.md), and then enter the following command:</span></span>

```shell
gacutil -l
```

<span data-ttu-id="b76c7-106">\- ou -</span><span class="sxs-lookup"><span data-stu-id="b76c7-106">-or-</span></span>

```shell
gacutil /l
```

> [!NOTE]
> <span data-ttu-id="b76c7-107">Nas versões anteriores do .NET Framework, a extensão do shell do Windows [Shfusion.dll](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/34149zk3(v=vs.100)) permitia exibir o cache de assembly global no Explorador de Arquivos.</span><span class="sxs-lookup"><span data-stu-id="b76c7-107">In earlier versions of the .NET Framework, the [Shfusion.dll](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/34149zk3(v=vs.100)) Windows shell extension enabled you to view the global assembly cache in File Explorer.</span></span> <span data-ttu-id="b76c7-108">Do .NET Framework 4 em diante, a Shfusion.dll tornou-se obsoleta.</span><span class="sxs-lookup"><span data-stu-id="b76c7-108">Beginning with the .NET Framework 4, Shfusion.dll is obsolete.</span></span>

## <a name="see-also"></a><span data-ttu-id="b76c7-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b76c7-109">See also</span></span>

- [<span data-ttu-id="b76c7-110">Como trabalhar com assemblies e o cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="b76c7-110">Working with Assemblies and the Global Assembly Cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="b76c7-111">Gacutil.exe (Ferramenta Cache de Assembly Global)</span><span class="sxs-lookup"><span data-stu-id="b76c7-111">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
