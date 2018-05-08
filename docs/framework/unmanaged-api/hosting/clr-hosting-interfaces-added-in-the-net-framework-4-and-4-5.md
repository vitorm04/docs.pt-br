---
title: Interfaces de hospedagem CLR adicionadas no .NET Framework 4 e 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- hosting interfaces [.NET Framework], version 4
- .NET Framework 4, hosting interfaces
- interfaces [.NET Framework hosting], version 4
ms.assetid: f6af6116-f5b0-4bda-a276-fffdba70893d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 982f5780a40dd8cbce02ec33f7e6f77589cd3717
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="clr-hosting-interfaces-added-in-the-net-framework-4-and-45"></a>Interfaces de hospedagem CLR adicionadas no .NET Framework 4 e 4.5
Esta seção descreve as interfaces não gerenciadas hosts podem usar para integrar o common language runtime (CLR) a [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]e em versões posteriores em seus aplicativos. Essas interfaces fornecem métodos para um host configurar e carregar o tempo de execução em um processo.  
  
 Começando com o [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], hospedagem de todas as interfaces têm as seguintes características:  
  
-   Eles usam o gerenciamento de vida útil (`AddRef` e `Release`), encapsulamento (contexto implícito) e `QueryInterface` de COM.  
  
-   Há não usa tipos COM como `BSTR`, `SAFEARRAY`, ou `VARIANT`.  
  
-   Não existem modelos apartment, agregação ou a ativação do registro que usam o [função CoCreateInstance](http://go.microsoft.com/fwlink/?LinkId=142894).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Interface ICLRAppDomainResourceMonitor](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 Fornece métodos que Inspecione a memória e a utilização da CPU de um domínio de aplicativo.  
  
 [Interface ICLRDomainManager](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)  
 Permite que o host especificar o Gerenciador de domínio de aplicativo que será usado para inicializar o domínio de aplicativo padrão e para especificar propriedades de inicialização.  
  
 [Interface ICLRGCManager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)  
 Fornece o [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) método, o que permite que um host definir o tamanho do segmento de coleta de lixo e o tamanho máximo da geração do sistema de coleta de lixo 0 como valores maior `DWORD`.  
  
 [Interface ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 Fornece métodos que retornam uma versão específica do CLR, listam todos os CLRs instalados, listam de todos os tempos de execução no processo, retornam a interface de ativação e descobrir a versão CLR usada para compilar um assembly.  
  
 [Interface ICLRMetaHostPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)  
 Fornece o [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) método que fornece uma interface CLR com base em critérios de política, assembly gerenciado, versão e arquivo de configuração.  
  
 [Interface ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 Fornece métodos que retornam informações sobre um tempo de execução específica, incluindo a versão, o diretório e o status de carga.  
  
 [Interface ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)  
 Fornece funções estáticas globais de básicas para assinar assemblies com nomes fortes. Todos os [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) métodos retornam os HRESULTs COM padrão.  
  
 [Interface ICLRStrongName2](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname2-interface.md)  
 Fornece a capacidade de criar nomes de alta segurança usando o grupo de SHA-2 de algoritmos de Hash seguro (SHA-256, SHA-384 e SHA-512).  
  
 [Interface ICLRTask2](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)  
 Fornece toda a funcionalidade do [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md); Além disso, fornece métodos que permitem cancelamentos do thread para ser atrasado no thread atual.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Interfaces e coclasses de hospedagem CLR preteridas](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 Descreve as interfaces de hospedagem fornecidas com as versões do .NET Framework 1.0 e 1.1.  
  
 [Interfaces de hospedagem CLR](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 Descreve as interfaces de hospedagem fornecidas com as versões do .NET Framework 2.0, 3.0 e 3.5.  
  
 [Hospedagem](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 Apresenta a hospedagem do .NET Framework.
