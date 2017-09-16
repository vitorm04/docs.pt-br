---
title: "Esquema de configurações de inicialização"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- startup settings schema
- schema startup settings
- configuration schema [.NET Framework], startup settings
ms.assetid: 03de6972-442a-4648-9f3e-efa654e3b949
caps.latest.revision: 10
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: cc014f65cec23f9ab1794d73e0f5d4f7cd5844da
ms.contentlocale: pt-br
ms.lasthandoff: 09/05/2017

---
# <a name="startup-settings-schema"></a>Esquema de configurações de inicialização
As configurações de inicialização especificam a versão do Common Language Runtime que deve executar o aplicativo.  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<requiredRuntime>](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)|Especifica que o aplicativo dá suporte apenas à versão 1.0 do Common Language Runtime. Os aplicativos criados com a versão 1.1 do tempo de execução devem usar o elemento **\<supportedRuntime>**.|  
|[\<supportedRuntime>](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)|Especifica a quais versões do Common Language Runtime o aplicativo oferece suporte.|  
|[\<startup>](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)|Contém os elementos **\<requiredRuntime>** e **\<supportedRuntime>**.|  
  
## <a name="see-also"></a>Consulte também  
 [Esquema de arquivo de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [\<PaveOver> Specifying Which Runtime Version to Use](http://msdn.microsoft.com/en-us/c376208d-980d-42b4-865b-fbe0d9cc97c2) (PaveOver> Especificando a versão do tempo de execução a ser usada)

