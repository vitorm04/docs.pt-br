---
title: Interface ICLRRuntimeHost
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeHost
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeHost
helpviewer_keywords: ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: cb0c5f65-3791-47bc-b833-2f84f4101ba5
topic_type: apiref
caps.latest.revision: "26"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 332db2680ca23f34893a6c50c5311d73838bc1e6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrruntimehost-interface"></a>Interface ICLRRuntimeHost
Fornece funcionalidade semelhante do [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interface fornecida no .NET Framework versão 1, com as seguintes alterações:  
  
-   A adição do [SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md) método para definir a interface de controle de host.  
  
-   A omissão de alguns métodos fornecidos pelo `ICorRuntimeHost`.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método ExecuteApplication](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md)|Usado em cenários de implantação de ClickOnce baseado no manifesto para especificar o aplicativo a ser ativado em um novo domínio.|  
|[Método ExecuteInAppDomain](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeinappdomain-method.md)|Especifica o <xref:System.AppDomain> no qual executar o código gerenciado especificado.|  
|[Método ExecuteInDefaultAppDomain](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeindefaultappdomain-method.md)|Invoca o método especificado do tipo especificado no assembly especificado.|  
|[Método GetCLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getclrcontrol-method.md)|Obtém um ponteiro de interface do tipo [ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) que os hosts podem usar para personalizar aspectos do common language runtime (CLR).|  
|[Método GetCurrentAppDomainId](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md)|Obtém o identificador numérico do <xref:System.AppDomain> que está em execução atualmente.|  
|[Método SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md)|Define a interface de controle de host. Você deve chamar `SetHostControl` antes de chamar `Start`.|  
|[Método Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)|Inicializa o CLR em um processo.|  
|[Método Stop](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-stop-method.md)|Interrompe a execução de código em tempo de execução.|  
|[Método UnloadAppDomain](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-unloadappdomain-method.md)|Descarrega o <xref:System.AppDomain> que corresponde ao identificador numérico especificado.|  
  
## <a name="remarks"></a>Comentários  
 Começando com o [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], use o [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md) interface para obter um ponteiro para o [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) de interface e, em seguida, chame o [Iclrruntimeinfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) método para obter um ponteiro para `ICLRRuntimeHost`. Em versões anteriores do .NET Framework, o host obtém um ponteiro para um `ICLRRuntimeHost` instância chamando [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) ou [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md). Para fornecer implementações de qualquer uma das tecnologias fornecidas no .NET Framework versão 2.0, você deve usar `ICLRRuntimeHost` em vez de `ICorRuntimeHost`.  
  
> [!IMPORTANT]
>  Não chame o [iniciar](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) método antes de chamar o [ExecuteApplication](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md) método para ativar um aplicativo baseado no manifesto. Se o `Start` método é chamado pela primeira vez, o `ExecuteApplication` haverá falha na chamada de método.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Função CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [Função CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [Interface ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [Interface ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [Interfaces de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Coclass CLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/clrruntimehost-coclass.md)
