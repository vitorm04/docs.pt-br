---
title: Interface IAppDomainSetup
ms.date: 03/30/2017
api_name:
- IAppDomainSetup
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IAppDomainSetup
helpviewer_keywords:
- IAppDomainSetup interface [.NET Framework hosting]
ms.assetid: 1844da85-c031-40bf-bea4-1a3d12a36c8c
topic_type:
- apiref
ms.openlocfilehash: 0fab64c31d4a73995c16d21767f4569f21c7df9a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126867"
---
# <a name="iappdomainsetup-interface"></a>Interface IAppDomainSetup
Fornece propriedades que permitem ao host configurar um tipo de <xref:System.AppDomain?displayProperty=nameWithType> antes de chamar o método [ICorRuntimeHost:: CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) para criá-lo.  
  
## <a name="properties"></a>Propriedades  
  
|propriedade|Descrição|  
|--------------|-----------------|  
|<xref:System.AppDomainSetup.ApplicationBase%2A>|Obtém ou define o nome do diretório que contém o aplicativo.|  
|<xref:System.AppDomainSetup.ApplicationName%2A>|Obtém ou define o nome do aplicativo.|  
|<xref:System.AppDomainSetup.CachePath%2A>|Obtém ou define o nome de uma área específica para o aplicativo em que os arquivos são copiados por sombra.|  
|<xref:System.AppDomainSetup.ConfigurationFile%2A>|Obtém ou define o nome do arquivo de configuração para um aplicativo.|  
|<xref:System.AppDomainSetup.DynamicBase%2A>|Obtém ou define o nome do diretório onde os arquivos gerados dinamicamente são armazenados e acessados.|  
|<xref:System.AppDomainSetup.LicenseFile%2A>|Obtém ou define o caminho para o arquivo de licença que está associado a esse domínio.|  
|<xref:System.AppDomainSetup.PrivateBinPath%2A>|Obtém ou define a lista de diretórios combinados com o diretório de <xref:System.AppDomainSetup.ApplicationBase%2A> para investigação de assemblies privados.|  
|<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>|Obtém ou define um valor de cadeia de caracteres que inclui ou exclui <xref:System.AppDomainSetup.ApplicationBase%2A> do caminho de pesquisa para o aplicativo.|  
|<xref:System.AppDomainSetup.ShadowCopyDirectories%2A>|Obtém ou define os nomes dos diretórios que contêm assemblies a serem copiados por sombra.|  
|<xref:System.AppDomainSetup.ShadowCopyFiles%2A>|Obtém ou define uma cadeia de caracteres que indica se a cópia de sombra está ativada ou desativada. Os valores válidos são "true" ou "false".|  
  
## <a name="remarks"></a>Comentários  
 A interface `IAppDomainSetup` corresponde à interface <xref:System.IAppDomainSetup> gerenciada, que o tipo de <xref:System.AppDomainSetup> implementa. Consulte <xref:System.IAppDomainSetup?displayProperty=nameWithType> para obter descrições detalhadas de suas propriedades.  
  
 `IAppDomainSetup` representa informações de associação de assembly que podem ser adicionadas a uma instância de <xref:System.AppDomain> antes de sua criação. Por exemplo, um host pode definir a propriedade <xref:System.AppDomainSetup.ApplicationBase%2A> para estabelecer um diretório raiz, que as investigações de Common Language Runtime (CLR) para assemblies gerenciados.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE. h  
  
 **Biblioteca:** Incluído como um recurso em MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup>
- [Hospedagem de Interfaces](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
