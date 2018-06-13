---
title: Método ICLRRuntimeInfo::BindAsLegacyV2Runtime
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.BindAsLegacyV2Runtime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::BindAsLegacyV2Runtime
helpviewer_keywords:
- ICLRRuntimeInfo::BindAsLegacyV2Runtime method [.NET Framework hosting]
- BindAsLegacyV2Runtime method [.NET Framework hosting]
ms.assetid: 65fd55ac-4a24-4479-9384-a2e8013bfb2b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 690287bf54f98c19298504ee3058a59ef88a87f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433155"
---
# <a name="iclrruntimeinfobindaslegacyv2runtime-method"></a>Método ICLRRuntimeInfo::BindAsLegacyV2Runtime
Associa o tempo de execução atual para todos os herdado common language runtime (CLR) versão 2 ativação decisões de política.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT BindAsLegacyV2Runtime ();  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Esse método retorna os seguintes HRESULTs específicos:  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|Ou a associação foi bem-sucedida ou esse tempo de execução já foi vinculado como o herdados CLR versão 2 ativação diretiva em tempo de execução.|  
|CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND|Um tempo de execução diferente já foi associado à política de ativação 2 de versão do CLR herdada.|  
  
## <a name="remarks"></a>Comentários  
 Se o tempo de execução atual já está associado para todos os herdados CLR versão 2 ativação política decisões (por exemplo, usando o `useLegacyV2RuntimeActivationPolicy` atributo no [ \<inicialização > elemento](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) no arquivo de configuração), esse método não retorna um resultado de erro; em vez disso, o resultado é S_OK, exatamente como seria se o método tinha associada com êxito a política de ativação herdadas.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [Hospedagem de Interfaces](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Hospedagem](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 [Elemento \<startup>](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)
