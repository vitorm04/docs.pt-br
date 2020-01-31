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
ms.openlocfilehash: 11b1072b3467f7d0a3f223fbc2151ec9ccf461ad
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790799"
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
  
## <a name="parameters"></a>Parâmetros  
 `pcProcs`  
 fora O número de processos retornados em `ppProcs`. Esse valor pode ser 0 (zero).  
  
 `ppProcs`  
 fora Uma matriz de estruturas [CoreClrDebugProcInfo](coreclrdebugprocinfo-structure.md) que representam os processos em execução no computador remoto.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK  
 Êxito.  
  
 {1&gt;E_OUTOFMEMORY&lt;1}  
 Não é possível alocar memória suficiente para `ppProcs`.  
  
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
