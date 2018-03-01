---
title: "Método IHostMemoryManager::VirtualAlloc"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostMemoryManager.VirtualAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualAlloc
helpviewer_keywords:
- VirtualAlloc method [.NET Framework hosting]
- IHostMemoryManager::VirtualAlloc method [.NET Framework hosting]
ms.assetid: 4dff3646-a050-4bd9-ac31-fe307e8637ec
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 761958c44ad374d522a52826929e320e65957ffa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmemorymanagervirtualalloc-method"></a>Método IHostMemoryManager::VirtualAlloc
Serve como um wrapper lógico para a função Win32 correspondente. A implementação do Win32 de `VirtualAlloc` reserva ou confirma uma região de páginas no espaço de endereço virtual do processo de chamada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT VirtualAlloc (  
    [in]  void*   pAddress,  
    [in]  SIZE_T  dwSize,  
    [in]  DWORD   flAllocationType,  
    [in]  DWORD   flProtect,  
    [in]  EMemoryCriticalLevel dwCriticalLevel,  
    [out] void**  ppMem  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pAddress`  
 [in] Um ponteiro para o endereço inicial da região para alocar.  
  
 `dwSize`  
 [in] O tamanho, em bytes, da região.  
  
 `flAllocationType`  
 [in] O tipo de alocação de memória.  
  
 `flProtect`  
 [in] Proteção de memória para a região de páginas a serem alocados.  
  
 `dwCriticalLevel`  
 [in] Um [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) valor que indica o impacto de uma falha de alocação.  
  
 `ppMem`  
 [out] Ponteiro para o endereço inicial da memória alocada, ou nulo se a solicitação não pôde ser atendida.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|`VirtualAlloc`retornou com êxito.|  
|HOST_E_CLRNOTAVAILABLE|O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.|  
|HOST_E_TIMEOUT|A chamada foi atingido.|  
|HOST_E_NOT_OWNER|O chamador não possui o bloqueio.|  
|HOST_E_ABANDONED|Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.|  
|E_FAIL|Ocorreu uma falha catastrófica desconhecida. Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo. As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Não havia memória suficiente disponível para concluir a solicitação de alocação|  
  
## <a name="remarks"></a>Comentários  
 Reservar uma região no espaço de endereço de seu processo chamando `VirtualAlloc`. O `pAddress` parâmetro contém o endereço de início do bloco de memória que você deseja. Este parâmetro normalmente é definido como null. O sistema operacional mantém um registro de intervalos de endereços livres disponíveis para o processo. Um `pAddress` valor NULL instrui o sistema para reservar a região onde desejar. Como alternativa, você pode fornecer um endereço inicial específico para o bloco de memória. Em ambos os casos, o parâmetro de saída `ppMem` é retornado como um ponteiro para a memória alocada. A função retorna um valor HRESULT.  
  
 O Win32 `VirtualAlloc` função não tem um `ppMem` parâmetro e retorna o ponteiro para a memória alocada em vez disso. Para obter mais informações, consulte a documentação da plataforma Windows.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
