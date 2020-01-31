---
title: Método ICorProfilerFunctionControl::SetILFunctionBody
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl.SetILFunctionBody
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl::SetILFunctionBody
helpviewer_keywords:
- ICorProfilerFunctionControl::SetILFunctionBody method [.NET Framework profiling]
- SetILFunctionBody method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: 2c33f0f7-75b2-4c19-b2c7-c94b54997576
topic_type:
- apiref
ms.openlocfilehash: bebc0cf6ac7912ea3a6641e0c729b759e865dac3
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864655"
---
# <a name="icorprofilerfunctioncontrolsetilfunctionbody-method"></a>Método ICorProfilerFunctionControl::SetILFunctionBody
Substitui o corpo CIL (Common Intermediate Language) do método.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetILFunctionBody(  
    [in]  ULONG   cbNewILMethodHeader,  
    [in, size_is(cbNewILMethodHeader)] LPCBYTE pbNewILMethodHeader);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `cbNewILMethodHeader`  
 [in] O tamanho total do novo CIL, incluindo o cabeçalho e quaisquer estruturas que vierem após o corpo.  
  
 `pbNewILMethodHeader`  
 [in] Um ponteiro para o novo cabeçalho CIL.  
  
## <a name="return-value"></a>Valor de retorno  
 Esse método retorna os HRESULTs específicos a seguir.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|A substituição foi bem-sucedida.|  
  
## <a name="remarks"></a>Comentários  
 Ao contrário do método [ICorProfilerInfo:: SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) , o método `SetILFunctionBody` gerencia a memória necessária para o novo corpo cil. Isso significa que o corpo de CIL fornecido pelo criador de perfil não precisa ser alocado usando a interface [IMethodMalloc](imethodmalloc-interface.md) ou alocado em um intervalo específico. Ele pode ser alocado em qualquer heap. O criador de perfil pode liberar a memória usada para o corpo de CIL depois que `SetILFunctionBody` retorna.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorProfilerFunctionControl](icorprofilerfunctioncontrol-interface.md)
