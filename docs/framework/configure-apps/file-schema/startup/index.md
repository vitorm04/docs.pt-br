---
title: Esquema de configurações de inicialização
ms.date: 03/30/2017
helpviewer_keywords:
- startup settings schema
- schema startup settings
- configuration schema [.NET Framework], startup settings
ms.assetid: 03de6972-442a-4648-9f3e-efa654e3b949
ms.openlocfilehash: e5f9c9af64ff38e7c0f1f26ccab039261b052e30
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/26/2019
ms.locfileid: "55083412"
---
# <a name="startup-settings-schema"></a>Esquema de configurações de inicialização

As configurações de inicialização especificam a versão do Common Language Runtime que deve executar o aplicativo.  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<requiredRuntime>](requiredruntime-element.md)|Especifica que o aplicativo dá suporte apenas à versão 1.0 do Common Language Runtime. Os aplicativos criados com a versão 1.1 do tempo de execução devem usar o elemento **\<supportedRuntime>**.|  
|[\<supportedRuntime>](supportedruntime-element.md)|Especifica a quais versões do Common Language Runtime o aplicativo oferece suporte.|  
|[\<startup>](startup-element.md)|Contém os elementos **\<requiredRuntime>** e **\<supportedRuntime>**.|  
  
## <a name="see-also"></a>Consulte também

- [Esquema de arquivos de configuração](../index.md)
- [Como: configurar um aplicativo para dar suporte ao .NET Framework 4 ou a versões posteriores](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
