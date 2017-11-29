---
title: Usando componentes atendidos com o cache de assemblies global
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- GAC (global assembly cache), serviced components
- serviced components, global assembly cache
- global assembly cache, serviced components
ms.assetid: 3423e5d9-234c-4571-8161-e35f6d130128
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 45fd02c4f87d33766741e6fd023f9b40b9964d63
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="using-serviced-components-with-the-global-assembly-cache"></a>Usando componentes atendidos com o cache de assemblies global
Componentes atendidos (componentes COM+ com código gerenciado) devem ser colocados no cache de assembly global. Em alguns cenários, o Common Language Runtime e serviços COM+ podem manipular componentes atendidos que não estão no cache de assembly global; em outros cenários, eles não podem. Os seguintes cenários ilustram isso:  
  
-   Para componentes atendidos em um aplicativo de COM+ Server, o assembly que contém os componentes deve estar no cache de assembly global, pois Dllhost.exe não é executado no mesmo diretório que contém os componentes atendidos.  
  
-   Para componentes atendidos em um aplicativo de COM+ Library, o tempo de execução e COM+ Services podem resolver as referências ao assembly que contém os componentes pesquisando o diretório atual. Nesse caso, o assembly não precisa estar no cache de assembly global.  
  
-   Para componentes atendidos em um aplicativo ASP.NET, a situação é diferente. Se você colocar o assembly que contém os componentes atendidos no diretório bin da base de aplicativo e usar o registro sob demanda, o assembly será copiado por sombra para o cache de download, pois o ASP.NET aproveita os recursos de sombra do tempo de execução.  
  
## <a name="see-also"></a>Consulte também  
 [Como trabalhar com assemblies e o cache de assembly global](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [Gacutil.exe (Ferramenta Cache de Assembly Global)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
