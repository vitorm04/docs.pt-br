---
title: Interface ICLRRuntimeHost
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost
helpviewer_keywords:
- ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: cb0c5f65-3791-47bc-b833-2f84f4101ba5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da22cbfe06245d915bed6db9cba220fc32b38942
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64627135"
---
# <a name="iclrruntimehost-interface"></a>Interface ICLRRuntimeHost
Fornece uma funcionalidade semelhante do [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interface fornecida no .NET Framework versão 1, com as seguintes alterações:  
  
- A adição do [SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md) método para definir a interface de controle de host.  
  
- A omissão de alguns métodos fornecidos pelo `ICorRuntimeHost`.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método ExecuteApplication](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md)|Usado em cenários de implantação de ClickOnce baseado em manifesto para especificar o aplicativo a ser ativado em um novo domínio.|  
|[Método ExecuteInAppDomain](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeinappdomain-method.md)|Especifica o <xref:System.AppDomain> no qual executar o código gerenciado especificado.|  
|[Método ExecuteInDefaultAppDomain](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeindefaultappdomain-method.md)|Invoca o método especificado do tipo especificado no assembly especificado.|  
|[Método GetCLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getclrcontrol-method.md)|Obtém um ponteiro de interface do tipo [ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) que os hosts podem usar para personalizar os aspectos do common language runtime (CLR).|  
|[Método GetCurrentAppDomainId](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md)|Obtém o identificador numérico do <xref:System.AppDomain> que está sendo executado.|  
|[Método SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md)|Define a interface de controle de host. Você deve chamar `SetHostControl` antes de chamar `Start`.|  
|[Método Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)|Inicializa o CLR em um processo.|  
|[Método Stop](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-stop-method.md)|Interrompe a execução de código, o tempo de execução.|  
|[Método UnloadAppDomain](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-unloadappdomain-method.md)|Descarrega o <xref:System.AppDomain> que corresponde ao identificador numérico especificado.|  
  
## <a name="remarks"></a>Comentários  
 Começando com o [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], use o [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md) interface para obter um ponteiro para o [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) de interface e, em seguida, chame o [iclrruntimeinfo:: Getinterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) método para obter um ponteiro para `ICLRRuntimeHost`. Em versões anteriores do .NET Framework, o host obtém um ponteiro para um `ICLRRuntimeHost` instância chamando [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) ou [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md). Para fornecer implementações de qualquer uma das tecnologias fornecidas no .NET Framework versão 2.0, você deve usar `ICLRRuntimeHost` em vez de `ICorRuntimeHost`.  
  
> [!IMPORTANT]
>  Não chame o [inicie](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) método antes de chamar o [ExecuteApplication](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md) método para ativar um aplicativo baseado em manifesto. Se o `Start` método é chamado pela primeira vez, o `ExecuteApplication` chamada de método falhará.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Função CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [Função CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [Interface ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [Interface ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [Hospedagem de Interfaces](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Coclass CLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/clrruntimehost-coclass.md)
