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
ms.openlocfilehash: 2579bed9ae432a2b9460c421c6ee5bdc40d1e149
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121831"
---
# <a name="icoreclrdebugtargetenumruntimes-method"></a>Método ICoreClrDebugTarget::EnumRuntimes
Enumera os Common Language runtimes (CLRs) no processo especificado que está sendo executado em um computador remoto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT EnumRuntimes (  
      [in] DWORD       dwInternalProcessID,  
      [out] DWORD*     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**    ppRuntimes  
    );  
```  
  
## <a name="parameters"></a>Parâmetros  
 `dwInternalProcessID`  
 no A ID do processo interno do processo para o qual você deseja enumerar os tempos de execução. Isso será `m_dwInternalID` do [CoreClrDebugProcInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md)correspondente.  
  
 `pcRuntimes`  
 fora O número de tempos de execução retornados em `ppRuntimes`. Esse valor pode ser 0 (zero).  
  
 `ppRuntimes`  
 fora Uma matriz de estruturas [CoreClrDebugRuntimeInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md) que representam os tempos de execução carregados no processo de destino remoto.  
  
## <a name="return-value"></a>Valor retornado  
 S_OK  
 Êxito.  
  
 S_FALSE  
 `dwInternalProcessID` não corresponde a nenhum processo em execução no computador, provavelmente porque o processo foi encerrado. `pcRuntimes` e `ppRuntimes` serão nulas.  
  
 E_OUTOFMEMORY  
 Não é possível alocar memória suficiente para `ppRuntimes`.  
  
 E_FAIL (ou outros códigos de retorno de E_)  
 Outras falhas.  
  
## <a name="remarks"></a>Comentários  
 Para liberar a memória que foi alocada por esse método, chame o método [ICoreClrDebugTarget:: freememory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) .  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CoreClrRemoteDebuggingInterfaces. h  
  
 **Biblioteca:** mscordbi_macx86. dll  
  
 **Versões do .NET Framework:** 3,5 SP1  
  
## <a name="see-also"></a>Consulte também

- [Interface ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)
