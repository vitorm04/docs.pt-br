---
title: Interface ICoreClrDebugTarget
ms.date: 03/30/2017
api_name:
- ICoreClrDebugTarget
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget
helpviewer_keywords:
- remote debugging API [Silverlight]
- ICorClrDebugTarget interface
- Silverlight, remote debugging
ms.assetid: 7cfaee76-e284-4a66-a431-8e33f0f60038
topic_type:
- apiref
ms.openlocfilehash: 190671b4f690f8c2cad43cf446a1196985ec5a42
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790747"
---
# <a name="icoreclrdebugtarget-interface"></a>Interface ICoreClrDebugTarget
Fornece métodos que controlam contagens de referência, enumeram processos e liberam a memória associada a um depurador que é anexado a um destino do Silverlight do Macintosh remoto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
class ICoreClrDebugTarget {  
      HRESULT EnumProcesses (  
          [out] DWORD*                    pcProcs,  
          [out] CoreClrDebugProcInfo**    ppProcs  
      );  
  
      HRESULT EnumRuntimes (  
      [in]  DWORD                      dwInternalProcessID,  
      [out] DWORD*                     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**  ppRuntimes  
      );  
  
      void FreeMemory (  
      [in] void*      pMemory  
    );  
};  
```  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método ICoreClrDebugTarget::EnumProcesses](icoreclrdebugtarget-enumprocesses-method.md)|Enumera os processos que estão sendo executados em um computador remoto.|  
|[Método ICoreClrDebugTarget::EnumRuntimes](icoreclrdebugtarget-enumruntimes-method.md)|Enumera os Common Language runtimes (CLRs) no processo especificado em um computador remoto.|  
|[Método ICoreClrDebugTarget::FreeMemory](icoreclrdebugtarget-freememory-method.md)|Libera a memória alocada pelos métodos de enumeração nesta classe.|  
  
## <a name="remarks"></a>Comentários  
 Atualmente, essa funcionalidade tem suporte apenas para a depuração de um destino de aplicativo baseado no Silverlight que está sendo executado em um computador Macintosh remoto.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CoreClrRemoteDebuggingInterfaces. h  
  
 **Biblioteca:** mscordbi_macx86. dll  
  
 **Versões do .NET Framework:** 3,5 SP1  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugRemoteTarget](icordebugremotetarget-interface.md)
- [Interface ICorDebug](icordebug-interface.md)

- [Depurando interfaces](debugging-interfaces.md)
