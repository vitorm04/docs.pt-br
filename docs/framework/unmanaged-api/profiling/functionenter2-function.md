---
title: Função FunctionEnter2
ms.date: 03/30/2017
api_name:
- FunctionEnter2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter2
helpviewer_keywords:
- FunctionEnter2 function [.NET Framework profiling]
ms.assetid: ce7a21f9-0ca3-4b92-bc4b-bb803cae3f51
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d79249a2540adbd7f1b7e9bf36c899ba94d71e2e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="functionenter2-function"></a>Função FunctionEnter2
Notifica o criador de perfil que o controle está sendo passado para uma função e fornece informações sobre a pilha de argumentos de função e de quadro. Essa função substitui o [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) função.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
void __stdcall FunctionEnter2 (  
    [in]  FunctionID                       funcId,   
    [in]  UINT_PTR                         clientData,   
    [in]  COR_PRF_FRAME_INFO               func,   
    [in]  COR_PRF_FUNCTION_ARGUMENT_INFO  *argumentInfo  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `funcId`  
 [in] O identificador da função à qual o controle é passado.  
  
 `clientData`  
 [in] O identificador de função remapeados, o criador de perfil especificado anteriormente usando o [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) função.  
  
 `func`  
 [in] Um `COR_PRF_FRAME_INFO` valor que aponta para obter informações sobre o quadro de pilhas.  
  
 O criador de perfil deve tratar isso como um identificador opaco que pode ser passado de volta para o mecanismo de execução no [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) método.  
  
 `argumentInfo`  
 [in] Um ponteiro para um [COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) estrutura que especifica os locais na memória dos argumentos da função.  
  
 Para acessar informações de argumento, o `COR_PRF_ENABLE_FUNCTION_ARGS` sinalizador deve ser definido. O criador de perfil pode usar o [: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) método para definir os sinalizadores de evento.  
  
## <a name="remarks"></a>Comentários  
 Os valores da `func` e `argumentInfo` parâmetros não são válidos após o `FunctionEnter2` função retorna porque os valores podem ser alterados ou ser destruídos.  
  
 O `FunctionEnter2` função é um retorno de chamada; você deve implementá-la. A implementação deve usar o `__declspec`(`naked`) atributo de classe de armazenamento.  
  
 O mecanismo de execução não salva quaisquer registros antes de chamar essa função.  
  
-   Na entrada, você deve salvar todos os registros que você usa, incluindo aqueles na unidade de ponto flutuante (FPU).  
  
-   Na saída, você deve restaurar a pilha por retirar desativar todos os parâmetros que foram empurrados pelo chamador.  
  
 A implementação de `FunctionEnter2` não devem bloquear porque ele atrasará a coleta de lixo. A implementação não deve tentar uma coleta de lixo, porque a pilha pode não estar em um estado de amigável para coleta de lixo. Se você tentar uma coleta de lixo, tempo de execução será bloqueado até que `FunctionEnter2` retorna.  
  
 Além disso, o `FunctionEnter2` função não deve chamar código gerenciado ou em qualquer causa de maneira uma alocação de memória gerenciada.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Função FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [Função FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 [Método SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [Criando perfil de funções estáticas globais](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
