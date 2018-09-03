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
ms.openlocfilehash: 3650de934cb3d2940d0e8e971d03aff856bddfd7
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43394459"
---
# <a name="how-to-view-the-contents-of-the-global-assembly-cache"></a>Como exibir o conteúdo do cache de assemblies global
Use a [ferramenta Cache de Assembly Global (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) para exibir o conteúdo do cache de assembly global.  
  
### <a name="to-view-a-list-of-the-assemblies-in-the-global-assembly-cache"></a>Para exibir uma lista de assemblies no cache de assembly global  
  
1.  No [prompt de comando do Visual Studio](../../../docs/framework/tools/developer-command-prompt-for-vs.md), digite o seguinte comando:  
  
     **gacutil -l**   
     -ou-  
    **gacutil /l**  
  
 Nas versões anteriores do .NET Framework, a extensão do shell do Windows [Shfusion.dll](https://msdn.microsoft.com/library/0d9464cf-ddba-4ca9-bbec-f678fb58f380) permitia exibir o cache de assembly global no Explorador de Arquivos. A partir do [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], o Shfusion.dll tornou-se obsoleto.  
  
## <a name="see-also"></a>Consulte também  
 [Como trabalhar com assemblies e o cache de assembly global](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [Gacutil.exe (Ferramenta do Cache de Assemblies Global)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
