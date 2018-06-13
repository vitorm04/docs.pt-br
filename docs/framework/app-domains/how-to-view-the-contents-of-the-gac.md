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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d6e582f86eac03a51437b965f87f1bc7f29294eb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32743700"
---
# <a name="how-to-view-the-contents-of-the-global-assembly-cache"></a><span data-ttu-id="aacb2-102">Como exibir o conteúdo do cache de assemblies global</span><span class="sxs-lookup"><span data-stu-id="aacb2-102">How to: View the Contents of the Global Assembly Cache</span></span>
<span data-ttu-id="aacb2-103">Use a [ferramenta Cache de Assembly Global (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) para exibir o conteúdo do cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="aacb2-103">Use the [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) to view the contents of the global assembly cache.</span></span>  
  
### <a name="to-view-a-list-of-the-assemblies-in-the-global-assembly-cache"></a><span data-ttu-id="aacb2-104">Para exibir uma lista de assemblies no cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="aacb2-104">To view a list of the assemblies in the global assembly cache</span></span>  
  
1.  <span data-ttu-id="aacb2-105">No [prompt de comando do Visual Studio](../../../docs/framework/tools/developer-command-prompt-for-vs.md), digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="aacb2-105">At the [Visual Studio command prompt](../../../docs/framework/tools/developer-command-prompt-for-vs.md), type the following command:</span></span>  
  
     <span data-ttu-id="aacb2-106">**gacutil -l** </span><span class="sxs-lookup"><span data-stu-id="aacb2-106">**gacutil -l** </span></span>  
     <span data-ttu-id="aacb2-107">-ou-</span><span class="sxs-lookup"><span data-stu-id="aacb2-107">-or-</span></span>  
    <span data-ttu-id="aacb2-108">**gacutil /l**</span><span class="sxs-lookup"><span data-stu-id="aacb2-108">**gacutil /l**</span></span>  
  
 <span data-ttu-id="aacb2-109">Nas versões anteriores do .NET Framework, a extensão do shell do Windows [Shfusion.dll](http://msdn.microsoft.com/library/0d9464cf-ddba-4ca9-bbec-f678fb58f380) permitia exibir o cache de assembly global no Explorador de Arquivos.</span><span class="sxs-lookup"><span data-stu-id="aacb2-109">In earlier versions of the .NET Framework, the [Shfusion.dll](http://msdn.microsoft.com/library/0d9464cf-ddba-4ca9-bbec-f678fb58f380) Windows shell extension enabled you to view the global assembly cache in File Explorer.</span></span> <span data-ttu-id="aacb2-110">A partir do [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], o Shfusion.dll tornou-se obsoleto.</span><span class="sxs-lookup"><span data-stu-id="aacb2-110">Beginning with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Shfusion.dll is obsolete.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aacb2-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aacb2-111">See Also</span></span>  
 [<span data-ttu-id="aacb2-112">Como trabalhar com assemblies e o cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="aacb2-112">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [<span data-ttu-id="aacb2-113">Gacutil.exe (Ferramenta do Cache de Assemblies Global)</span><span class="sxs-lookup"><span data-stu-id="aacb2-113">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
