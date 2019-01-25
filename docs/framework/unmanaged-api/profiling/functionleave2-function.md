---
title: Função FunctionLeave2
ms.date: 03/30/2017
api_name:
- FunctionLeave2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave2
helpviewer_keywords:
- FunctionLeave2 function [.NET Framework profiling]
ms.assetid: 8cdac941-8b94-4497-b874-4e571785f3fe
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 874bbf46e74550b325631a00acc16f49d818dc61
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574931"
---
# <a name="functionleave2-function"></a>Função FunctionLeave2
Notifica o criador de perfil que uma função está prestes a retornar ao chamador e fornece informações sobre o stack frame e função de valor retornado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
void __stdcall FunctionLeave2 (  
    [in]  FunctionID                        funcId,  
    [in]  UINT_PTR                          clientData,  
    [in]  COR_PRF_FRAME_INFO                func,  
    [in]  COR_PRF_FUNCTION_ARGUMENT_RANGE  *retvalRange  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `funcId`  
 [in] O identificador da função que está retornando.  
  
 `clientData`  
 [in] O identificador de função remapeada, que o criador de perfil especificado anteriormente por meio de [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) função.  
  
 `func`  
 [in] Um `COR_PRF_FRAME_INFO` valor aponta para obter informações sobre o quadro de pilhas.  
  
 O criador de perfil deve tratar isso como um identificador opaco que pode ser passado para o mecanismo de execução no [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) método.  
  
 `retvalRange`  
 [in] Um ponteiro para um [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) estrutura que especifica o local da memória do valor de retorno da função.  
  
 Para acessar informações de valor de retorno, o `COR_PRF_ENABLE_FUNCTION_RETVAL` sinalizador deve ser definido. O criador de perfil pode usar o [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) método para definir os sinalizadores de evento.  
  
## <a name="remarks"></a>Comentários  
 Os valores da `func` e `retvalRange` parâmetros não são válidos após o `FunctionLeave2` função retorna porque os valores podem ser alterados ou ser destruídos.  
  
 O `FunctionLeave2` função é um retorno de chamada; você deve implementá-la. A implementação deve usar o `__declspec`(`naked`) atributo de classe de armazenamento.  
  
 O mecanismo de execução não salva qualquer registros antes de chamar essa função.  
  
-   Na entrada, você deve salvar todos os registros que você usa, incluindo aqueles na unidade de ponto flutuante (FPU).  
  
-   Na saída, você deve restaurar a pilha de popping desativar todos os parâmetros que foram enviados por push ao seu chamador.  
  
 A implementação de `FunctionLeave2` não devem bloquear porque isso atrasará a coleta de lixo. A implementação não deve tentar uma coleta de lixo, porque a pilha não pode estar em um estado de amigável para coleta de lixo. Se você tentar uma coleta de lixo, o tempo de execução será bloqueado até que `FunctionLeave2` retorna.  
  
 Além disso, o `FunctionLeave2` função não deve chamar código gerenciado ou em qualquer causa de maneira uma alocação de memória gerenciada.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Função FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [Função FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [Método SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [Criando perfil de funções estáticas globais](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
