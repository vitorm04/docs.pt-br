---
title: Método ICoreClrDebugTarget::EnumRuntimes
ms.date: 03/30/2017
api_name:
- ICoreClrDebugTarget.EnumRuntimes
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget::EnumRuntimes
helpviewer_keywords:
- remote debugging API [Silverlight]
- ICorClrDebugTarget::EnumRuntimes method [Silverlight debugging]
- EnumRuntimes method, ICoreClrDebugTarget interface [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: 316df866-442d-40cc-b049-45e8adcb65d1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: afb31646d21ec7e15f79601f5fe83ea6ce44fa90
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59134665"
---
# <a name="icoreclrdebugtargetenumruntimes-method"></a>Método ICoreClrDebugTarget::EnumRuntimes
Enumera os tempos de execução de linguagem comum (CLRs) no processo especificado que está em execução em um computador remoto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT EnumRuntimes (  
      [in] DWORD       dwInternalProcessID,  
      [out] DWORD*     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**    ppRuntimes  
    );  
```  
  
## <a name="parameters"></a>Parâmetros  
 `dwInternalProcessID`  
 [in] A ID de processo interno do processo para o qual você deseja enumerar tempos de execução. Isso será `m_dwInternalID` de correspondente [CoreClrDebugProcInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md).  
  
 `pcRuntimes`  
 [out] O número de tempos de execução retornados em `ppRuntimes`. Esse valor pode ser 0 (zero).  
  
 `ppRuntimes`  
 [out] Uma matriz de [CoreClrDebugRuntimeInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md) estruturas que representam os tempos de execução carregado no processo de destino remoto.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK  
 Êxito.  
  
 S_FALSE  
 `dwInternalProcessID` não corresponde qualquer processo que está em execução no computador, provavelmente porque o processo foi encerrado. `pcRuntimes` e `ppRuntimes` será nulo.  
  
 E_OUTOFMEMORY  
 Não é possível alocar memória suficiente para `ppRuntimes`.  
  
 E_FAIL (ou outros códigos de retorno e _)  
 Outras falhas.  
  
## <a name="remarks"></a>Comentários  
 Para liberar a memória alocada por esse método, chame o [icoreclrdebugtarget:: freeMemory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) método.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CoreClrRemoteDebuggingInterfaces.h  
  
 **Biblioteca:** mscordbi_macx86.dll  
  
 **Versões do .NET framework:** 3,5 SP1  
  
## <a name="see-also"></a>Consulte também

- [Interface ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)
