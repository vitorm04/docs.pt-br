---
title: "Como exibir o conteúdo do cache de assembly global | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 15
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 9f51fbaddf7de524a0025e87aa598726fc6f1db4
ms.contentlocale: pt-br
ms.lasthandoff: 06/02/2017

---
# <a name="how-to-view-the-contents-of-the-global-assembly-cache"></a>Como exibir o conteúdo do cache de assemblies global
Use a [ferramenta Cache de Assembly Global (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) para exibir o conteúdo do cache de assembly global.  
  
### <a name="to-view-a-list-of-the-assemblies-in-the-global-assembly-cache"></a>Para exibir uma lista de assemblies no cache de assembly global  
  
1.  No [prompt de comando do Visual Studio](../../../docs/framework/tools/developer-command-prompt-for-vs.md), digite o seguinte comando:  
  
     **gacutil -l**   
     -ou-  
    **gacutil /l**  
  
 Nas versões anteriores do .NET Framework, a extensão do shell do Windows [Shfusion.dll](http://msdn.microsoft.com/en-us/0d9464cf-ddba-4ca9-bbec-f678fb58f380) permitia exibir o cache de assembly global no Explorador de Arquivos. A partir do [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], o Shfusion.dll tornou-se obsoleto.  
  
## <a name="see-also"></a>Consulte também  
 [Como trabalhar com assemblies e o cache de assembly global](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)   
 [Gacutil.exe (Ferramenta Cache de Assembly Global)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
