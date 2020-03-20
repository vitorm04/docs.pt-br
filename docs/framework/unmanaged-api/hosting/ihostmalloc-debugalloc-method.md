---
title: Método IHostMAlloc::DebugAlloc
ms.date: 03/30/2017
api_name:
- IHostMAlloc.DebugAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc::DebugAlloc
helpviewer_keywords:
- DebugAlloc method [.NET Framework hosting]
- IHostMAlloc::DebugAlloc method [.NET Framework hosting]
ms.assetid: 0bfbc527-bea2-43ce-b041-69186f4440dd
topic_type:
- apiref
ms.openlocfilehash: 20ad5485b8603cc7de1c27c00d53c8939871d525
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178033"
---
# <a name="ihostmallocdebugalloc-method"></a>Método IHostMAlloc::DebugAlloc
Solicita que o host aloque a quantidade especificada de memória do heap e, adicionalmente, rastreie onde a memória foi alocada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT DebugAlloc (  
    [in]  SIZE_T  cbSize,
    [in]  EMemoryCriticalLevel dwCriticalLevel,
    [in]  char*   pszFileName,
    [in]  int     iLineNo,
    [out] void**  ppMem  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `cbSize`  
 [em] O tamanho, em bytes, da solicitação de alocação de memória atual.  
  
 `dwCriticalLevel`  
 [em] Um dos valores [eMemoryCriticalLevel,](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) indicando o impacto de uma falha de alocação.  
  
 `pszFileName`  
 [em] O arquivo de código do executável sendo depurado.  
  
 `iLineNo`  
 [em] O número `pszFileName` da linha em que a alocação foi solicitada.  
  
 `ppMem`  
 [fora] Um ponteiro para a memória alocada ou nulo se a solicitação não puder ser concluída.  
  
## <a name="return-value"></a>Valor retornado  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|`DebugAlloc`retornou com sucesso.|  
|Host_e_clrnotavailable|A CLR não foi carregada em um processo, ou a CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com sucesso.|  
|HOST_E_TIMEOUT|A chamada acabou.|  
|HOST_E_NOT_OWNER|O interlocutor não é dono da fechadura.|  
|HOST_E_ABANDONED|Um evento foi cancelado enquanto um fio ou fibra bloqueado estava esperando por ele.|  
|E_FAIL|Uma falha catastrófica desconhecida ocorreu. Quando um método retorna E_FAIL, a CLR não é mais utilizável dentro do processo. Chamadas subseqüentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Não havia memória suficiente para concluir a solicitação de alocação.|  
  
## <a name="remarks"></a>Comentários  
 O CLR obtém um ponteiro de interface para uma instância [iHostMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) chamando o método [IHostMemoryManager::CreateMalloc.](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) `DebugAlloc`permite que o tempo de execução obtenha informações de arquivo de código para uso durante a depuração.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** Incluído como um recurso em MSCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [Interface IHostMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
