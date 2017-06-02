---
title: Posicionamento do assembly | Microsoft Docs
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
- <codeBase> element
- locating assemblies
- assemblies [.NET Framework], placement
- assemblies [.NET Framework], location
ms.assetid: ff8d48bc-f606-484f-9fe1-d0af264269fb
caps.latest.revision: 9
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 5152d639c34a128c1c0625d9ae2ba12bc4fa7f9d
ms.contentlocale: pt-br
ms.lasthandoff: 06/02/2017

---
# <a name="assembly-placement"></a>Posicionamento dos assemblies
Para a maioria dos aplicativos .NET Framework, você localiza assemblies que compõem um aplicativo no diretório do aplicativo, em um subdiretório do diretório do aplicativo ou no cache de assembly global (se o assembly for compartilhado). Você pode substituir onde o Common Language Runtime procura um assembly usando o [\<elemento codeBase>](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) em um arquivo de configuração. Se o assembly não tiver um nome forte, o local especificado usando o [\<elemento codeBase>](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) estará restrito ao diretório ou ao subdiretório do aplicativo. Se o assembly tiver um nome forte, o [\<elemento codeBase>](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) poderá especificar qualquer local no computador ou em uma rede.  
  
 Regras similares se aplicam à localização de assemblies durante o trabalho com código não gerenciado ou aplicativos interop COM: se o assembly for compartilhado por vários aplicativos, ele deverá ser instalado no cache de assembly global. Assemblies usados com códigos não gerenciados devem ser exportados como uma biblioteca de tipos e registrados. Assemblies usados pelo interop COM devem ser registrados no catálogo, embora em alguns casos, esse registro ocorra automaticamente.  
  
## <a name="see-also"></a>Consulte também  
 [Como o tempo de execução localiza assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)   
 [Configuração de aplicativos](../../../docs/framework/configure-apps/index.md)   
 [Interoperabilidade COM avançada](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)   
 [Assemblies no Common Language Runtime](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
