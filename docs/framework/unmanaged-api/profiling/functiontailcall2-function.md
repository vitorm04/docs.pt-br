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
ms.openlocfilehash: 60276327617ae24e9bdcebf958613c21d3808429
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175181"
---
# <a name="functiontailcall2-function"></a>Função FunctionTailcall2
Notifica o profiler de que a função de execução atualmente está prestes a executar uma chamada de cauda para outra função e fornece informações sobre o quadro de pilha.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
void __stdcall FunctionTailcall2 (  
    [in] FunctionID         funcId,
    [in] UINT_PTR           clientData,
    [in] COR_PRF_FRAME_INFO func  
);  
```  
  
## <a name="parameters"></a>parâmetros

- `funcId`

  \[em] O identificador da função de execução atual que está prestes a fazer uma chamada de cauda.

- `clientData`

  \[em] O identificador de função remapped, que o profiler previamente especificado via [FunctionIDMapper](functionidmapper-function.md), da função de execução atual que está prestes a fazer uma chamada de cauda.
  
- `func`

  \[em] `COR_PRF_FRAME_INFO` Um valor que aponta para informações sobre o quadro de pilha.

  O profiler deve tratá-lo como uma alça opaca que pode ser passada de volta para o mecanismo de execução no método [ICorProfilerInfo2::GetFunctionInfo2.](icorprofilerinfo2-getfunctioninfo2-method.md)

## <a name="remarks"></a>Comentários  
 A função de destino da chamada de cauda usará o quadro de pilha atual e retornará diretamente ao chamador da função que fez a chamada traseira. Isso significa que um retorno de chamada [FunctionLeave2](functionleave2-function.md) não será emitido para uma função que é o alvo de uma chamada de cauda.  
  
 O valor `func` do parâmetro não é `FunctionTailcall2` válido após o retorno da função porque o valor pode mudar ou ser destruído.  
  
 A `FunctionTailcall2` função é um retorno de chamada; você deve implementá-lo. A implementação `__declspec`deve`naked`usar o atributo () classe de armazenamento.  
  
 O motor de execução não salva nenhum registro antes de chamar esta função.  
  
- Na entrada, você deve salvar todos os registros que você usa, incluindo os da unidade de ponto flutuante (FPU).  
  
- Na saída, você deve restaurar a pilha, atirando todos os parâmetros que foram empurrados pelo seu interlocutor.  
  
 A implantação `FunctionTailcall2` não deve bloquear porque vai atrasar a coleta de lixo. A implementação não deve tentar uma coleta de lixo porque a pilha pode não estar em um estado favorável à coleta de lixo. Se uma coleta de lixo for tentada, o tempo de execução será bloqueado até `FunctionTailcall2` o retorno.  
  
 Além disso, a `FunctionTailcall2` função não deve chamar para código gerenciado ou de qualquer forma causar uma alocação de memória gerenciada.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Função FunctionEnter2](functionenter2-function.md)
- [Função FunctionLeave2](functionleave2-function.md)
- [Método SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [Criando perfil de funções estáticas globais](profiling-global-static-functions.md)
