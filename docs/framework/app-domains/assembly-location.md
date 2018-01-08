---
title: Local de um assembly
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 9f1f41a7-2954-49d3-a2c0-62b6ef4d40ab
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 96b3105dcd1eaf6d95269d05518e6892b42a638f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="assembly-location"></a>Local de um assembly
O local de um assembly determina se o Common Language Runtime pode localizá-lo quando referenciado, bem como pode determinar se o assembly pode ser compartilhado com outros assemblies. Você pode implantar um assembly nos seguintes locais:  
  
-   No diretório ou subdiretórios do aplicativo.  
  
     Esse é o local mais comum para implantar um assembly. Os subdiretórios do diretório raiz de um aplicativo podem ser baseados na linguagem ou cultura. Se um assembly tiver informações no atributo de cultura, ele deverá estar em um subdiretório no diretório do aplicativo com o nome dessa cultura.  
  
-   O cache de assembly global.  
  
     Esse é um cache de código da máquina toda que é instalado sempre que o Common Language Runtime é instalado. Na maioria das vezes, se você pretende compartilhar um assembly com vários aplicativos, é preciso implantá-lo no cache de assembly global.  
  
-   Em um servidor HTTP.  
  
     Um assembly implantado em um servidor HTTP deve ter um nome forte; você aponta para o assembly na seção de base de código do arquivo de configuração de aplicativo.  
  
## <a name="see-also"></a>Consulte também  
 [Criação de assemblies](../../../docs/framework/app-domains/create-assemblies.md)  
 [Cache de assembly global](../../../docs/framework/app-domains/gac.md)  
 [Como o tempo de execução localiza assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [Programação com assemblies](../../../docs/framework/app-domains/programming-with-assemblies.md)
