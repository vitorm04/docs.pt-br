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
ms.openlocfilehash: 4390f379e5092cc59d123631f5e6d8da82e2bd7f
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703898"
---
# <a name="iclrruntimeinfobindaslegacyv2runtime-method"></a>Método ICLRRuntimeInfo::BindAsLegacyV2Runtime
Associa o tempo de execução atual a todas as decisões de política de ativação da versão 2 do Common Language Runtime herdado (CLR).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT BindAsLegacyV2Runtime ();  
```  
  
## <a name="return-value"></a>Valor retornado  
 Esse método retorna os HRESULTs específicos a seguir:  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|A associação foi bem-sucedida ou esse tempo de execução já estava associado ao tempo de execução da política de ativação do CLR versão 2 herdado.|  
|CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND|Um tempo de execução diferente já estava associado à política de ativação do CLR versão 2 herdada.|  
  
## <a name="remarks"></a>Comentários  
 Se o tempo de execução atual já estiver associado a todas as decisões da política de ativação do CLR versão 2 herdadas (por exemplo, usando o `useLegacyV2RuntimeActivationPolicy` atributo no [ \< elemento Startup>](../../configure-apps/file-schema/startup/startup-element.md) no arquivo de configuração), esse método não retornará um resultado de erro; em vez disso, o resultado será S_OK, assim como seria se o método tivesse associado com êxito a política de ativação herdada.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost. h  
  
 **Biblioteca:** Incluído como um recurso em MSCorEE. dll  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICLRRuntimeInfo](iclrruntimeinfo-interface.md)
- [Interfaces de hospedagem](hosting-interfaces.md)
- [Hospedagem](index.md)
- [\<Elemento de> de inicialização](../../configure-apps/file-schema/startup/startup-element.md)
