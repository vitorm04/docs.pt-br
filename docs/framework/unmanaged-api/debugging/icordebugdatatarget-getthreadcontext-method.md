---
title: Método ICorDebugDataTarget::GetThreadContext
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.GetThreadContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::GetThreadContext
helpviewer_keywords:
- ICorDebugDataTarget::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: c8954268-1821-4b23-b665-dbb55f2af31b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ab2fbf6bb08a33158ea450f0f19eca50e280d8c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugdatatargetgetthreadcontext-method"></a>Método ICorDebugDataTarget::GetThreadContext
Retorna o contexto do thread atual para o segmento especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetThreadContext(  
       [in] DWORD dwThreadID,  
       [in] ULONG32 contextFlags,  
       [in] ULONG32 contextSize,  
       [out, size_is(contextSize)] BYTE * pContext);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwThreadID`  
 [in] O identificador do segmento é cujo contexto a ser recuperado. O identificador é definido pelo sistema operacional.  
  
 `contextFlags`  
 [in] Uma combinação bit a bit dos sinalizadores de dependente de plataforma que indicam quais partes do contexto deve ser lidos.  
  
 `contextSize`  
 [in] O tamanho do `pContext`.  
  
 `pContext`  
 [out] O buffer onde o contexto do thread será armazenado.  
  
## <a name="remarks"></a>Comentários  
 Em plataformas Windows, `pContext` deve ser um `CONTEXT` estrutura (definida em Winnt. H) que é apropriada para o tipo de máquina especificado o [Icordebugdatatarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) método. `contextFlags` deve ter os mesmos valores que o `ContextFlags` campo o `CONTEXT` estrutura. O `CONTEXT` estrutura específicos de processador; consulte o arquivo Winnt. H para obter detalhes.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
