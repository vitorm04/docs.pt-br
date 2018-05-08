---
title: Método ICLRProbingAssemblyEnum::Get
ms.date: 03/30/2017
api_name:
- ICLRProbingAssemblyEnum.Get
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRProbingAssemblyEnum::Get
helpviewer_keywords:
- Get method, ICLRProbingAssemblyEnum interface [.NET Framework hosting]
- ICLRProbingAssemblyEnum::Get method [.NET Framework hosting]
ms.assetid: fdb67a77-782f-44cf-a8a1-b75999b0f3c8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1f5ddd352d027365e02366e9aa779053da3bdc2f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="iclrprobingassemblyenumget-method"></a>Método ICLRProbingAssemblyEnum::Get
Obtém a identidade do assembly no índice especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwIndex`  
 [in] O índice baseado em zero da identidade do assembly para retornar.  
  
 `pwzBuffer`  
 [out] Um buffer que contém os dados de identidade do assembly.  
  
 `pcchBufferSize`  
 [out no] O tamanho do `pwzBuffer` buffer.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|`Get` retornou com êxito.|  
|ERROR_INSUFFICIENT_BUFFER|`pwzBuffer` é pequeno demais.|  
|ERROR_NO_MORE_ITEMS|A enumeração não contém mais itens.|  
|HOST_E_CLRNOTAVAILABLE|O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.|  
|HOST_E_TIMEOUT|A chamada foi atingido.|  
|HOST_E_NOT_OWNER|O chamador não possui o bloqueio.|  
|HOST_E_ABANDONED|Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.|  
|E_FAIL|Ocorreu uma falha catastrófica desconhecida. Se um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo. As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Comentários  
 A identidade no índice 0 é a identidade específica da arquitetura do processador. A identidade no índice 1 é o assembly de arquitetura neutra para Microsoft intermediate language (MSIL). A identidade no índice 2 não contém nenhuma informação de arquitetura.  
  
 `Get` geralmente é chamado duas vezes. A primeira chamada fornece um valor nulo para `pwzBuffer`e define `pcchBufferSize` para o tamanho apropriado para `pwzBuffer`. A segunda chamada fornece um tamanho apropriado `pwzBuffer`e contém os dados de identidade de assembly canônico após a conclusão.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICLRProbingAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)  
 [Interface ICLRAssemblyIdentityManager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
