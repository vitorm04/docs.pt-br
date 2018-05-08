---
title: Função FunctionTailcall2
ms.date: 03/30/2017
api_name:
- FunctionTailcall2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall2
helpviewer_keywords:
- FunctionTailcall2 function [.NET Framework profiling]
ms.assetid: 249f9892-b5a9-41e1-b329-28a925904df6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7a515c2622f81c666523aa012fa1e34e5251c074
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="functiontailcall2-function"></a>Função FunctionTailcall2
Notifica o criador de perfil que a função atualmente em execução está prestes a realizar uma chamada tail para outra função e fornece informações sobre o quadro de pilhas.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
void __stdcall FunctionTailcall2 (  
    [in] FunctionID         funcId,   
    [in] UINT_PTR           clientData,   
    [in] COR_PRF_FRAME_INFO func  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `funcId`  
 [in] O identificador da função atualmente em execução que está prestes a fazer uma cauda chamada.  
  
 `clientData`  
 [in] O identificador de função remapeados, o criador de perfil especificado anteriormente por meio de [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md), da função atualmente em execução que está prestes a fazer uma cauda chamada.  
  
 `func`  
 [in] Um `COR_PRF_FRAME_INFO` valor que aponta para obter informações sobre o quadro de pilhas.  
  
 O criador de perfil deve tratar isso como um identificador opaco que pode ser passado de volta para o mecanismo de execução no [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) método.  
  
## <a name="remarks"></a>Comentários  
 A função de destino da chamada final usará o quadro de pilhas atual e retornará diretamente para o chamador da função que fez com que a parte final chamada. Isso significa que um [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) retorno de chamada não será emitido para uma função que é o destino de uma chamada tail.  
  
 O valor da `func` parâmetro não é válido após o `FunctionTailcall2` função retorna porque o valor pode ser alterado ou ser destruído.  
  
 O `FunctionTailcall2` função é um retorno de chamada; você deve implementá-la. A implementação deve usar o `__declspec`(`naked`) atributo de classe de armazenamento.  
  
 O mecanismo de execução não salva quaisquer registros antes de chamar essa função.  
  
-   Na entrada, você deve salvar todos os registros que você usa, incluindo aqueles na unidade de ponto flutuante (FPU).  
  
-   Na saída, você deve restaurar a pilha por retirar desativar todos os parâmetros que foram empurrados pelo chamador.  
  
 A implementação de `FunctionTailcall2` não devem bloquear porque ele atrasará a coleta de lixo. A implementação não deve tentar uma coleta de lixo, porque a pilha pode não estar em um estado de amigável para coleta de lixo. Se você tentar uma coleta de lixo, tempo de execução será bloqueado até que `FunctionTailcall2` retorna.  
  
 Além disso, o `FunctionTailcall2` função não deve chamar código gerenciado ou em qualquer causa de maneira uma alocação de memória gerenciada.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Função FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [Função FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [Método SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [Criando perfil de funções estáticas globais](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
