---
title: 'Como: Exibir o conteúdo do cache de assembly global'
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8c7d197ea7178abf991247e5ecca02c2b8e94713
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634367"
---
# <a name="how-to-view-the-contents-of-the-global-assembly-cache"></a><span data-ttu-id="91fb1-102">Como: Exibir o conteúdo do cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="91fb1-102">How to: View the contents of the global assembly cache</span></span>

<span data-ttu-id="91fb1-103">Use a [Ferramenta de Cache de Assembly Global (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) para exibir o conteúdo do GAC (cache de assembly global).</span><span class="sxs-lookup"><span data-stu-id="91fb1-103">Use the [global assembly cache tool (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to view the contents of the global assembly cache (GAC).</span></span>

## <a name="view-the-assemblies-in-the-gac"></a><span data-ttu-id="91fb1-104">Exibir os assemblies no GAC</span><span class="sxs-lookup"><span data-stu-id="91fb1-104">View the assemblies in the GAC</span></span>

<span data-ttu-id="91fb1-105">Para exibir uma lista de assemblies no cache de assembly global, abra o [Prompt de Comando do Desenvolvedor para Visual Studio](../tools/developer-command-prompt-for-vs.md) e, em seguida, digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="91fb1-105">To view a list of the assemblies in the global assembly cache, open [Developer Command Prompt for Visual Studio](../tools/developer-command-prompt-for-vs.md), and then enter the following command:</span></span>

```shell
gacutil -l
```

<span data-ttu-id="91fb1-106">- ou -</span><span class="sxs-lookup"><span data-stu-id="91fb1-106">-or-</span></span>

```shell
gacutil /l
```

> [!NOTE]
> <span data-ttu-id="91fb1-107">Nas versões anteriores do .NET Framework, a extensão do shell do Windows [Shfusion.dll](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/34149zk3(v=vs.100)) permitia exibir o cache de assembly global no Explorador de Arquivos.</span><span class="sxs-lookup"><span data-stu-id="91fb1-107">In earlier versions of the .NET Framework, the [Shfusion.dll](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/34149zk3(v=vs.100)) Windows shell extension enabled you to view the global assembly cache in File Explorer.</span></span> <span data-ttu-id="91fb1-108">A partir do [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], o Shfusion.dll tornou-se obsoleto.</span><span class="sxs-lookup"><span data-stu-id="91fb1-108">Beginning with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Shfusion.dll is obsolete.</span></span>

## <a name="see-also"></a><span data-ttu-id="91fb1-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="91fb1-109">See also</span></span>

- [<span data-ttu-id="91fb1-110">Como trabalhar com assemblies e o cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="91fb1-110">Working with Assemblies and the Global Assembly Cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="91fb1-111">Gacutil.exe (Ferramenta do Cache de Assemblies Global)</span><span class="sxs-lookup"><span data-stu-id="91fb1-111">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
