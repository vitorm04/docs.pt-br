---
title: Método ICLRRuntimeHost::ExecuteInAppDomain
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.ExecuteInAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteInAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteInAppDomain method [.NET Framework hosting]
- ExecuteInAppDomain method [.NET Framework hosting]
ms.assetid: e2b0e2db-3fae-4b56-844e-d30a125a660c
topic_type:
- apiref
ms.openlocfilehash: c012e4e2b5e41737f7bbe6a0fb887693b0ba22c8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176416"
---
# <a name="iclrruntimehostexecuteinappdomain-method"></a>Método ICLRRuntimeHost::ExecuteInAppDomain
Especifica o <xref:System.AppDomain> em que executar o código gerenciado especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT ExecuteInAppDomain(  
    [in] DWORD AppDomainId,
    [in] FExecuteInDomainCallback pCallback,
    [in] void* cookie  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `AppDomainId`  
 [em] O ID numérico do <xref:System.AppDomain> em que executar o método especificado.  
  
 `pCallback`  
 [em] Um ponteiro para a função para <xref:System.AppDomain>executar dentro do especificado .  
  
 `cookie`  
 [em] Um ponteiro para memória opaca alocada por chamadores. Esse parâmetro é passado pelo tempo de execução do idioma comum (CLR) para o retorno de chamada de domínio. Não é memória de pilha gerenciada por tempo de execução; tanto a alocação quanto a vida útil desta memória são controladas pelo chamador.  
  
## <a name="return-value"></a>Valor retornado  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|`ExecuteInAppDomain`retornou com sucesso.|  
|Host_e_clrnotavailable|A CLR não foi carregada em um processo, ou a CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com sucesso.|  
|HOST_E_TIMEOUT|A chamada acabou.|  
|HOST_E_NOT_OWNER|O interlocutor não é dono da fechadura.|  
|HOST_E_ABANDONED|Um evento foi cancelado enquanto um fio ou fibra bloqueado estava esperando por ele.|  
|E_FAIL|Uma falha catastrófica desconhecida ocorreu. Se um método retornar E_FAIL, a CLR não poderá mais ser utilizável dentro do processo. Chamadas subseqüentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Comentários  
 `ExecuteInAppDomain`permite que o host exercite o controle sobre <xref:System.AppDomain> o qual o método gerenciado especificado deve ser executado. Você pode obter o valor do identificador de um domínio de <xref:System.AppDomain.Id%2A> aplicativo, que corresponde ao valor da propriedade, chamando-o de [Método GetCurrentAppDomainId](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** Incluído como um recurso em MSCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
