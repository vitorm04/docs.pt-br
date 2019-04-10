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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bbde873481aea9de94862117a99079301965f33c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59220065"
---
# <a name="iappdomainsetup-interface"></a>Interface IAppDomainSetup
Fornece propriedades que permitem que o host configurar uma <xref:System.AppDomain?displayProperty=nameWithType> tipo antes de chamar o [icorruntimehost:: Createdomainex](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) método para criá-lo.  
  
## <a name="properties"></a>Propriedades  
  
|Propriedade|Descrição|  
|--------------|-----------------|  
|<xref:System.AppDomainSetup.ApplicationBase%2A>|Obtém ou define o nome do diretório que contém o aplicativo.|  
|<xref:System.AppDomainSetup.ApplicationName%2A>|Obtém ou define o nome do aplicativo.|  
|<xref:System.AppDomainSetup.CachePath%2A>|Obtém ou define o nome de uma área específica para o aplicativo em que arquivos são copiados em sombra.|  
|<xref:System.AppDomainSetup.ConfigurationFile%2A>|Obtém ou define o nome do arquivo de configuração para um aplicativo.|  
|<xref:System.AppDomainSetup.DynamicBase%2A>|Obtém ou define o nome do diretório onde os arquivos gerados dinamicamente são armazenados e acessados.|  
|<xref:System.AppDomainSetup.LicenseFile%2A>|Obtém ou define o caminho para o arquivo de licença que está associado esse domínio.|  
|<xref:System.AppDomainSetup.PrivateBinPath%2A>|Obtém ou define a lista de diretórios, combinado com o <xref:System.AppDomainSetup.ApplicationBase%2A> diretório para investigar assemblies particulares.|  
|<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>|Obtém ou define um valor de cadeia de caracteres que inclui ou exclui <xref:System.AppDomainSetup.ApplicationBase%2A> do caminho de pesquisa para o aplicativo.|  
|<xref:System.AppDomainSetup.ShadowCopyDirectories%2A>|Obtém ou define os nomes dos diretórios que contêm assemblies a serem copiados em sombra.|  
|<xref:System.AppDomainSetup.ShadowCopyFiles%2A>|Obtém ou define uma cadeia de caracteres que indica se a cópia de sombra é ativada ou desativada. Valores válidos são "true" ou "false".|  
  
## <a name="remarks"></a>Comentários  
 O `IAppDomainSetup` interface corresponde à gerenciado <xref:System.IAppDomainSetup> interface, que o <xref:System.AppDomainSetup> tipo implementa. Consulte <xref:System.IAppDomainSetup?displayProperty=nameWithType> para obter descrições detalhadas de suas propriedades.  
  
 `IAppDomainSetup` representa as informações de associação de assembly que podem ser adicionadas a um <xref:System.AppDomain> instância antes de sua criação. Por exemplo, um host pode definir o <xref:System.AppDomainSetup.ApplicationBase%2A> assemblies gerenciados de propriedade para estabelecer um diretório raiz, que investiga o common language runtime (CLR).  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup>
- [Interfaces de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
