---
title: Função FunctionLeave3
ms.date: 03/30/2017
api_name:
- FunctionLeave3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave3
helpviewer_keywords:
- FunctionLeave3 function [.NET Framework profiling]
ms.assetid: 5d798088-7992-48a0-ae55-d2a7ee31913f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 14f4f16a73c50de2d23804f77bca180f4e9827b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453916"
---
# <a name="functionleave3-function"></a>Função FunctionLeave3
Notifica o criador de perfil que o controle está sendo retornado de uma função.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
void __stdcall FunctionLeave3(FunctionOrRemappedID functionOrRemappedID);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `functionOrRemappedID`  
 [in] O identificador da função da qual o controle é retornado.  
  
## <a name="remarks"></a>Comentários  
 O `FunctionLeave3` função de retorno de chamada notifica o criador de perfil como funções estão sendo chamado, mas não oferece suporte a inspeção do valor de retorno. Use o [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 método](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) para registrar sua implementação dessa função.  
  
 O `FunctionLeave3` função é um retorno de chamada; você deve implementá-la. A implementação deve usar o `__declspec(naked)` atributo de classe de armazenamento.  
  
 O mecanismo de execução não salva quaisquer registros antes de chamar essa função.  
  
-   Na entrada, você deve salvar todos os registros que você usa, incluindo aqueles na unidade de ponto flutuante (FPU).  
  
-   Na saída, você deve restaurar a pilha por retirar desativar todos os parâmetros que foram empurrados pelo chamador.  
  
 A implementação de `FunctionLeave3` não devem bloquear, porque ele atrasará a coleta de lixo. A implementação não deve tentar uma coleta de lixo, porque a pilha pode não estar em um estado de amigável para coleta de lixo. Se você tentar uma coleta de lixo, tempo de execução será bloqueado até que `FunctionLeave3` retorna.  
  
 O `FunctionLeave3` função não deve chamar código gerenciado ou fazer com que uma alocação de memória gerenciada de forma alguma.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [SetEnterLeaveFunctionHooks3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)  
 [SetEnterLeaveFunctionHooks3WithInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)  
 [SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [SetFunctionIDMapper2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)  
 [Criando perfil de funções estáticas globais](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
