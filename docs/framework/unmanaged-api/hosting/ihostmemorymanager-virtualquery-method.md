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
ms.openlocfilehash: 684d5e41e1d7cee2775aa0988d33a974315eac4e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772745"
---
# <a name="ihostmemorymanagervirtualquery-method"></a>Método IHostMemoryManager::VirtualQuery
Serve como um wrapper lógico para a função Win32 correspondente. A implementação do Win32 de `VirtualQuery` recupera informações sobre um intervalo de páginas no espaço de endereço virtual do processo de chamada.  
  
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
 [in] Um ponteiro para o endereço na memória virtual a ser consultado.  
  
 `lpBuffer`  
 [out] Um ponteiro para uma estrutura que contém informações sobre a região de memória especificado.  
  
 `dwLength`  
 [in] O tamanho, em bytes, do buffer que `lpBuffer` aponta.  
  
 `pResult`  
 [out] Um ponteiro para o número de bytes retornados pelo buffer de informações.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|`VirtualQuery` retornado com êxito.|  
|HOST_E_CLRNOTAVAILABLE|O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.|  
|HOST_E_TIMEOUT|A chamada atingiu o tempo limite.|  
|HOST_E_NOT_OWNER|O chamador não é proprietário do bloqueio.|  
|HOST_E_ABANDONED|Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.|  
|E_FAIL|Ocorreu uma falha catastrófica desconhecida. Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo. As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Comentários  
 `VirtualQuery` Fornece informações sobre um intervalo de páginas no espaço de endereço virtual do processo de chamada. Esta implementação define o valor da `pResult` parâmetro para o número de bytes retornados no buffer de informações e retorna um valor HRESULT. No Win32 `VirtualQuery` função, o valor de retorno é o tamanho do buffer. Para obter mais informações, consulte a documentação da plataforma Windows.  
  
> [!IMPORTANT]
>  A implementação do sistema operacional de `VirtualQuery` não incorrerá em deadlock e pode executar até a conclusão com aleatórios threads suspensos no código do usuário. Use muito cuidado ao implementar uma versão hospedada desse método.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
