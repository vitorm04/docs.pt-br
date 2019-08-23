---
title: Método IHostMemoryManager::VirtualQuery
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualQuery
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualQuery
helpviewer_keywords:
- IHostMemoryManager::VirtualQuery method [.NET Framework hosting]
- VirtualQuery method [.NET Framework hosting]
ms.assetid: 757af1e6-b9e8-49e7-b5db-342be3aa205f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 16d146766786f129d6da38bde1126ce8afe5e70f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963692"
---
# <a name="ihostmemorymanagervirtualquery-method"></a>Método IHostMemoryManager::VirtualQuery
Serve como um wrapper lógico para a função Win32 correspondente. A implementação do Win32 `VirtualQuery` de recupera informações sobre um intervalo de páginas no espaço de endereço virtual do processo de chamada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT VirtualQuery (  
    [in]  void*    lpAddress,  
    [out] void*    lpBuffer,  
    [in]  SIZE_T   dwLength,  
    [out] SIZE_T*  pResult  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `lpAddress`  
 no Um ponteiro para o endereço na memória virtual a ser consultada.  
  
 `lpBuffer`  
 fora Um ponteiro para uma estrutura que contém informações sobre a região de memória especificada.  
  
 `dwLength`  
 no O tamanho, em bytes, do buffer que `lpBuffer` aponta para.  
  
 `pResult`  
 fora Um ponteiro para o número de bytes retornados pelo buffer de informações.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|`VirtualQuery`retornado com êxito.|  
|HOST_E_CLRNOTAVAILABLE|O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.|  
|HOST_E_TIMEOUT|A chamada atingiu o tempo limite.|  
|HOST_E_NOT_OWNER|O chamador não possui o bloqueio.|  
|HOST_E_ABANDONED|Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.|  
|E_FAIL|Ocorreu uma falha catastrófica desconhecida. Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo. As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Comentários  
 `VirtualQuery`fornece informações sobre um intervalo de páginas no espaço de endereço virtual do processo de chamada. Essa implementação define o valor do `pResult` parâmetro como o número de bytes retornados no buffer de informações e retorna um valor HRESULT. Na função do `VirtualQuery` Win32, o valor de retorno é o tamanho do buffer. Para obter mais informações, consulte a documentação da plataforma Windows.  
  
> [!IMPORTANT]
> A implementação do sistema operacional do `VirtualQuery` não incorre em deadlock e pode ser executada até a conclusão com threads aleatórios suspensos no código do usuário. Tenha muito cuidado ao implementar uma versão hospedada desse método.  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca** Incluído como um recurso em MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
