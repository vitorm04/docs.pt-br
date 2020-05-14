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
ms.openlocfilehash: 0c1b18f24fd30b5f6d5e85633fc0c25839aba6df
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396416"
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
 fora O número de processos retornados em `ppProcs` . Esse valor pode ser 0 (zero).  
  
 `ppProcs`  
 fora Uma matriz de estruturas [CoreClrDebugProcInfo](coreclrdebugprocinfo-structure.md) que representam os processos em execução no computador remoto.  
  
## <a name="return-value"></a>Valor retornado  
 S_OK  
 Êxito.  
  
 E_OUTOFMEMORY  
 Não é possível alocar memória suficiente para `ppProcs` .  
  
 E_FAIL (ou outros códigos de retorno de E_)  
 Outras falhas.  
  
## <a name="remarks"></a>Comentários  
 Para liberar a memória que foi alocada por esse método, chame o método [ICoreClrDebugTarget:: freememory](icoreclrdebugtarget-freememory-method.md) .  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CoreClrRemoteDebuggingInterfaces. h  
  
 **Biblioteca:** mscordbi_macx86. dll  
  
 **Versões do .NET Framework:** 3,5 SP1  
  
## <a name="see-also"></a>Veja também

- [Interface ICoreClrDebugTarget](icoreclrdebugtarget-interface.md)
