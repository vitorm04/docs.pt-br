---
title: Método ICoreClrDebugTarget::EnumProcesses
ms.date: 03/30/2017
api_name:
- ICoreClrDebugTarget.EnumProcesses
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget::EnumProcesses
helpviewer_keywords:
- remote debugging API [Silverlight]
- EnumProcesses method, ICorClrDebugTarget interface [Silverlight debugging]
- ICorClrDebugTarget::EnumProcesses method [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: e00fd477-4f49-43d3-bd0e-3094824b1136
topic_type:
- apiref
ms.openlocfilehash: 6484832e8e737b9a0d0b3eaf3ede4078729f7a4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178432"
---
# <a name="icoreclrdebugtargetenumprocesses-method"></a>Método ICoreClrDebugTarget::EnumProcesses
Enumera os processos que estão sendo executados em um computador remoto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT EnumProcesses (  
       [out]  DWORD*                  pcProcs,
       [out]  CoreClrDebugProcInfo**  ppProcs  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `pcProcs`  
 [fora] O número de processos `ppProcs`retornados em . Este valor pode ser 0 (zero).  
  
 `ppProcs`  
 [fora] Um conjunto de estruturas [CoreClrDebugProcInfo](coreclrdebugprocinfo-structure.md) que representam os processos em execução no computador remoto.  
  
## <a name="return-value"></a>Valor retornado  
 S_OK  
 Sucesso.  
  
 E_OUTOFMEMORY  
 Não é possível `ppProcs`alocar memória suficiente para .  
  
 E_FAIL (ou outros códigos de retorno E_)  
 Outras falhas.  
  
## <a name="remarks"></a>Comentários  
 Para liberar a memória alocada por este método, ligue para o [método ICoreClrDebugTarget:::FreeMemory](icoreclrdebugtarget-freememory-method.md) method.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CoreClrRemoteDebuggingInterfaces.h  
  
 **Biblioteca:** mscordbi_macx86.dll  
  
 **.NET Framework Versões:** 3.5 SP1  
  
## <a name="see-also"></a>Confira também

- [Interface ICoreClrDebugTarget](icoreclrdebugtarget-interface.md)
