---
title: Método ICoreClrDebugTarget::FreeMemory
ms.date: 03/30/2017
api_name:
- ICoreDebugTarget.FreeMemory
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget::FreeMemory
helpviewer_keywords:
- remote debugging API [Silverlight]
- FreeMemory method, ICoreClrDebugTarget interface [Silverlight debugging]
- ICorClrDebugTarget::FreeMemory method [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: 98f2a0db-a6ec-4f9b-861d-f82485237d08
topic_type:
- apiref
ms.openlocfilehash: cfa313d286d0decad82f51bcedc582470549c8e1
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790780"
---
# <a name="icoreclrdebugtargetfreememory-method"></a>Método ICoreClrDebugTarget::FreeMemory
Libera a memória alocada pelos métodos [ICoreClrDebugTarget:: EnumProcesses](icoreclrdebugtarget-enumprocesses-method.md) e [ICoreClrDebugTarget:: EnumRuntimes](icoreclrdebugtarget-enumruntimes-method.md) .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
void FreeMemory (  
     [in] void*pMemory);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pMemory`  
 no Um ponteiro para a matriz que é retornado pelo método [ICoreClrDebugTarget:: EnumProcesses](icoreclrdebugtarget-enumprocesses-method.md) ou [ICoreClrDebugTarget:: EnumRuntimes](icoreclrdebugtarget-enumruntimes-method.md) .  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CoreClrRemoteDebuggingInterfaces. h  
  
 **Biblioteca:** mscordbi_macx86. dll  
  
 **Versões do .NET Framework:** 3,5 SP1  
  
## <a name="see-also"></a>Veja também

- [Interface ICoreClrDebugTarget](icoreclrdebugtarget-interface.md)
