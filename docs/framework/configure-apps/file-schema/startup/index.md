---
title: Esquema de configurações de inicialização
ms.date: 03/30/2017
helpviewer_keywords:
- startup settings schema
- schema startup settings
- configuration schema [.NET Framework], startup settings
ms.assetid: 03de6972-442a-4648-9f3e-efa654e3b949
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 4cdf6a051552ab1effd9c4d9c783297a62602f7a
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47204918"
---
# <a name="startup-settings-schema"></a>Esquema de configurações de inicialização
As configurações de inicialização especificam a versão do Common Language Runtime que deve executar o aplicativo.  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<requiredRuntime>](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)|Especifica que o aplicativo dá suporte apenas à versão 1.0 do Common Language Runtime. Os aplicativos criados com a versão 1.1 do tempo de execução devem usar o elemento **\<supportedRuntime>**.|  
|[\<supportedRuntime>](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)|Especifica a quais versões do Common Language Runtime o aplicativo oferece suporte.|  
|[\<startup>](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)|Contém os elementos **\<requiredRuntime>** e **\<supportedRuntime>**.|  
  
## <a name="see-also"></a>Consulte também  
 [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<PaveOver> Specifying Which Runtime Version to Use](https://msdn.microsoft.com/library/c376208d-980d-42b4-865b-fbe0d9cc97c2) (PaveOver> Especificando a versão do tempo de execução a ser usada)
