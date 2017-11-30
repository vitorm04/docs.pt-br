---
title: "Método IHostMemoryManager::VirtualQuery"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMemoryManager.VirtualQuery
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMemoryManager::VirtualQuery
helpviewer_keywords:
- IHostMemoryManager::VirtualQuery method [.NET Framework hosting]
- VirtualQuery method [.NET Framework hosting]
ms.assetid: 757af1e6-b9e8-49e7-b5db-342be3aa205f
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 82c76ce908dd73fba0a2a0039894f51790b46583
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ihostmemorymanagervirtualquery-method"></a>Método IHostMemoryManager::VirtualQuery
Serve como um wrapper lógico para a função Win32 correspondente. A implementação do Win32 de `VirtualQuery` recupera informações sobre um intervalo de páginas no espaço de endereço virtual do processo de chamada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT VirtualQuery (  
    [in]  void*    lpAddress,  
    [out] void*    lpBuffer,  
    [in]  SIZE_T   dwLength,  
    [out] SIZE_T*  pResult  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `lpAddress`  
 [in] Um ponteiro para o endereço na memória virtual a ser consultado.  
  
 `lpBuffer`  
 [out] Um ponteiro para uma estrutura que contém informações sobre a região de memória especificada.  
  
 `dwLength`  
 [in] O tamanho, em bytes, do buffer que `lpBuffer` aponta para.  
  
 `pResult`  
 [out] Um ponteiro para o número de bytes retornados pelo buffer de informações.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|`VirtualQuery`retornou com êxito.|  
|HOST_E_CLRNOTAVAILABLE|O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.|  
|HOST_E_TIMEOUT|A chamada foi atingido.|  
|HOST_E_NOT_OWNER|O chamador não possui o bloqueio.|  
|HOST_E_ABANDONED|Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.|  
|E_FAIL|Ocorreu uma falha catastrófica desconhecida. Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo. As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Comentários  
 `VirtualQuery`Fornece informações sobre um intervalo de páginas no espaço de endereço virtual do processo de chamada. Esta implementação define o valor de `pResult` parâmetro para o número de bytes retornados no buffer de informações e retorna um valor HRESULT. Em Win32 `VirtualQuery` função, o valor de retorno é o tamanho do buffer. Para obter mais informações, consulte a documentação da plataforma Windows.  
  
> [!IMPORTANT]
>  A implementação do sistema operacional de `VirtualQuery` não incorrerá em deadlock e pode executar o preenchimento com aleatórios threads suspensos no código do usuário. Use muito cuidado ao implementar uma versão hospedada deste método.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
