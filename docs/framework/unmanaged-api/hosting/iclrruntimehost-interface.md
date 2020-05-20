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
ms.openlocfilehash: dd1aa4089a981d82ae1403189343694a065a701d
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703658"
---
# <a name="iclrruntimehost-interface"></a>Interface ICLRRuntimeHost
Fornece uma funcionalidade semelhante à da interface [ICorRuntimeHost](icorruntimehost-interface.md) fornecida no .NET Framework versão 1, com as seguintes alterações:  
  
- A adição do método [SetHostControl](iclrruntimehost-sethostcontrol-method.md) para definir a interface de controle de host.  
  
- A omissão de alguns métodos fornecidos pelo `ICorRuntimeHost` .  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método ExecuteApplication](iclrruntimehost-executeapplication-method.md)|Usado em cenários de implantação ClickOnce baseados em manifesto para especificar o aplicativo a ser ativado em um novo domínio.|  
|[Método ExecuteInAppDomain](iclrruntimehost-executeinappdomain-method.md)|Especifica o <xref:System.AppDomain> no qual executar o código gerenciado especificado.|  
|[Método ExecuteInDefaultAppDomain](iclrruntimehost-executeindefaultappdomain-method.md)|Invoca o método especificado do tipo especificado no assembly especificado.|  
|[Método GetCLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getclrcontrol-method.md)|Obtém um ponteiro de interface do tipo [ICLRControl](iclrcontrol-interface.md) que os hosts podem usar para personalizar aspectos do Common Language Runtime (CLR).|  
|[Método GetCurrentAppDomainId](iclrruntimehost-getcurrentappdomainid-method.md)|Obtém o identificador numérico do <xref:System.AppDomain> que está sendo executado no momento.|  
|[Método SetHostControl](iclrruntimehost-sethostcontrol-method.md)|Define a interface de controle de host. Você deve chamar `SetHostControl` antes de chamar `Start` .|  
|[Método de início](iclrruntimehost-start-method.md)|Inicializa o CLR em um processo.|  
|[Método Stop](iclrruntimehost-stop-method.md)|Interrompe a execução do código pelo tempo de execução.|  
|[Método UnloadAppDomain](iclrruntimehost-unloadappdomain-method.md)|Descarrega o <xref:System.AppDomain> que corresponde ao identificador numérico especificado.|  
  
## <a name="remarks"></a>Comentários  
 Começando com o .NET Framework 4, use a interface [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md) para obter um ponteiro para a interface [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) e, em seguida, chame o método [ICLRRuntimeInfo:: GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) para obter um ponteiro `ICLRRuntimeHost` . Em versões anteriores do .NET Framework, o host obtém um ponteiro para uma `ICLRRuntimeHost` instância chamando [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) ou [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md). Para fornecer implementações de qualquer uma das tecnologias fornecidas no .NET Framework versão 2,0, você deve usar `ICLRRuntimeHost` em vez de `ICorRuntimeHost` .  
  
> [!IMPORTANT]
> Não chame o método [Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) antes de chamar o método [ExecuteApplication](iclrruntimehost-executeapplication-method.md) para ativar um aplicativo baseado em manifesto. Se o `Start` método for chamado primeiro, a `ExecuteApplication` chamada do método falhará.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE. h  
  
 **Biblioteca:** Incluído como um recurso em MSCorEE. dll  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Função CorBindToCurrentRuntime](corbindtocurrentruntime-function.md)
- [Função CorBindToRuntimeEx](corbindtoruntimeex-function.md)
- [Interface ICLRControl](iclrcontrol-interface.md)
- [Interface ICorRuntimeHost](icorruntimehost-interface.md)
- [Interfaces de hospedagem](hosting-interfaces.md)
- [Coclass CLRRuntimeHost](clrruntimehost-coclass.md)
