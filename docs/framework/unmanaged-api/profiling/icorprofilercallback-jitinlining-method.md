---
title: Método ICorProfilerCallback::JITInlining
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITInlining
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITInlining
helpviewer_keywords:
- JITInlining method [.NET Framework profiling]
- ICorProfilerCallback::JITInlining method [.NET Framework profiling]
ms.assetid: c2f45801-dd38-4b78-b6b7-64397dc73f83
topic_type:
- apiref
ms.openlocfilehash: 3e13b17fb03530730a78f6889309f1993419574b
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866202"
---
# <a name="icorprofilercallbackjitinlining-method"></a>Método ICorProfilerCallback::JITInlining
Notifica o criador de perfil de que o compilador JIT (just-in-time) está prestes a inserir uma função em linha com outra função.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT JITInlining(  
    [in]  FunctionID callerId,  
    [in]  FunctionID calleeId,  
    [out] BOOL      *pfShouldInline);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `callerId`  
 no A ID da função na qual a função de `calleeId` será inserida.  
  
 `calleeId`  
 no A ID da função a ser inserida.  
  
 `pfShouldInline`  
 [fora] `true` para permitir que a inserção ocorra; caso contrário, `false`.  
  
## <a name="remarks"></a>Comentários  
 O criador de perfil pode definir `pfShouldInline` como `false` para impedir que a função `calleeId` seja inserida na função `callerId`. Além disso, o criador de perfil pode desabilitar a inserção embutida globalmente usando o valor COR_PRF_DISABLE_INLINING da enumeração [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) .  
  
 Funções inseridas embutidas não geram eventos para entrar ou sair. Portanto, o criador de perfil deve definir `pfShouldInline` para `false` a fim de produzir um chamadas preciso. A definição de `pfShouldInline` como `false` afetará o desempenho, pois a inserção embutida normalmente aumenta a velocidade e reduz o número de eventos de compilação JIT separados para o método inserido.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorProfilerCallback](icorprofilercallback-interface.md)
