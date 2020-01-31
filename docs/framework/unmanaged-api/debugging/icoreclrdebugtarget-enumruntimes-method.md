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
ms.openlocfilehash: 4b55ac1d895bfecbe74be447bd06f4aa22b9d04f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790787"
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
 no A ID do processo interno do processo para o qual você deseja enumerar os tempos de execução. Isso será `m_dwInternalID` do [CoreClrDebugProcInfo](coreclrdebugprocinfo-structure.md)correspondente.  
  
 `pcRuntimes`  
 fora O número de tempos de execução retornados em `ppRuntimes`. Esse valor pode ser 0 (zero).  
  
 `ppRuntimes`  
 fora Uma matriz de estruturas [CoreClrDebugRuntimeInfo](coreclrdebugruntimeinfo-structure.md) que representam os tempos de execução carregados no processo de destino remoto.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK  
 Êxito.  
  
 S_FALSE  
 `dwInternalProcessID` não corresponde a nenhum processo em execução no computador, provavelmente porque o processo foi encerrado. `pcRuntimes` e `ppRuntimes` serão nulas.  
  
 {1&gt;E_OUTOFMEMORY&lt;1}  
 Não é possível alocar memória suficiente para `ppRuntimes`.  
  
 E_FAIL (ou outros códigos de retorno de E_)  
 Outras falhas.  
  
## <a name="remarks"></a>Comentários  
 Para liberar a memória que foi alocada por esse método, chame o método [ICoreClrDebugTarget:: freememory](icoreclrdebugtarget-freememory-method.md) .  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CoreClrRemoteDebuggingInterfaces. h  
  
 **Biblioteca:** mscordbi_macx86. dll  
  
 **Versões do .NET Framework:** 3,5 SP1  
  
## <a name="see-also"></a>Veja também

- [Interface ICoreClrDebugTarget](icoreclrdebugtarget-interface.md)
