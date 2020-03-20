---
title: Método IHostMemoryManager::GetMemoryLoad
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.GetMemoryLoad
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::GetMemoryLoad
helpviewer_keywords:
- IHostMemoryManager::GetMemoryLoad method [.NET Framework hosting]
- GetMemoryLoad method [.NET Framework hosting]
ms.assetid: e8138f6e-a0a4-48d4-8dae-9466b4dc6180
topic_type:
- apiref
ms.openlocfilehash: 88acd50c83eb1ff4d59aa50d677db2383912659a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176273"
---
# <a name="ihostmemorymanagergetmemoryload-method"></a>Método IHostMemoryManager::GetMemoryLoad
Obtém a quantidade de memória física que está atualmente em uso e, portanto, indisponível, conforme relatado pelo host.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetMemoryLoad (  
    [out] DWORD*  pMemoryLoad,
    [out] SIZE_T  *pAvailableBytes  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `pMemoryLoad`  
 [fora] Um ponteiro para a porcentagem aproximada da memória física total que está atualmente em uso.  
  
 `pAvailableBytes`  
 [fora] Um ponteiro para o número de bytes disponíveis para o tempo de execução do idioma comum (CLR).  
  
## <a name="return-value"></a>Valor retornado  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|`GetMemoryLoad`retornou com sucesso.|  
|Host_e_clrnotavailable|A CLR não foi carregada em um processo, ou a CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com sucesso.|  
|HOST_E_TIMEOUT|A chamada acabou.|  
|HOST_E_NOT_OWNER|O interlocutor não é dono da fechadura.|  
|HOST_E_ABANDONED|Um evento foi cancelado enquanto um fio ou fibra bloqueado estava esperando por ele.|  
|E_FAIL|Uma falha catastrófica desconhecida ocorreu. Quando um método retorna E_FAIL, a CLR não é mais utilizável dentro do processo. Chamadas subseqüentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Comentários  
 `GetMemoryLoad`envolve a função `GlobalMemoryStatus` Win32. O valor `pMemoryLoad` é o `dwMemoryLoad` equivalente ao `MEMORYSTATUS` campo na `GlobalMemoryStatus`estrutura devolvida de .  
  
 O tempo de execução usa o valor de retorno como uma heurística para o coletor de lixo. Por exemplo, se o host relatar que a maioria da memória está em uso, o coletor de lixo pode optar por coletar de várias gerações para aumentar a quantidade de memória que pode potencialmente ficar disponível.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** Incluído como um recurso em MSCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- <xref:System.GC?displayProperty=nameWithType>
- [Interface IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
