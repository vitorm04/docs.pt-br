---
title: Método ICorDebugRegisterSet::SetThreadContext
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.SetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::SetThreadContext
helpviewer_keywords:
- ICorDebugRegisterSet::SetThreadContext method [.NET Framework debugging]
- SetThreadContext method, ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: 73afa930-32cb-4c40-81f8-83e8e6fbe213
topic_type:
- apiref
ms.openlocfilehash: 63ddce2f299133fcfe0da17897eaf0c6a9509a55
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378238"
---
# <a name="icordebugregistersetsetthreadcontext-method"></a>Método ICorDebugRegisterSet::SetThreadContext
`SetThreadContext`Não está implementado na versão .NET Framework 2,0. Não chame esse método.  
  
> [!NOTE]
> Use a operação de nível superior [ICorDebugNativeFrame:: SetIP](icordebugnativeframe-setip-method.md) para definir o contexto de um thread.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetThreadContext (  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize),  
         size_is(contextSize)] BYTE context[]  
);  
```  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** 1,1, 1,0  
  
## <a name="see-also"></a>Confira também

- [Interface ICorDebugRegisterSet](icordebugregisterset-interface.md)
- [Interface ICorDebugRegisterSet2](icordebugregisterset2-interface.md)
