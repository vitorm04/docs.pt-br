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
ms.openlocfilehash: 0b1ecd1266528f8a08ef114de2f111dd0f71ca8b
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866925"
---
# <a name="functionleave2-function"></a>Função FunctionLeave2
Notifica o criador de perfil de que uma função está prestes a retornar ao chamador e fornece informações sobre o quadro de pilha e o valor de retorno da função.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
void __stdcall FunctionLeave2 (  
    [in]  FunctionID                        funcId,  
    [in]  UINT_PTR                          clientData,  
    [in]  COR_PRF_FRAME_INFO                func,  
    [in]  COR_PRF_FUNCTION_ARGUMENT_RANGE  *retvalRange  
);  
```  
  
## <a name="parameters"></a>Parâmetros

- `funcId`

  \[em] o identificador da função que está retornando.

- `clientData`

  \[em] o identificador da função remapeada, que o criador de perfil especificou anteriormente por meio da função [FunctionIDMapper](functionidmapper-function.md) .

- `func`

  \[em] um valor de `COR_PRF_FRAME_INFO` que aponta para informações sobre o registro de ativação.

  O criador de perfil deve tratar isso como um identificador opaco que pode ser passado de volta para o mecanismo de execução no método [ICorProfilerInfo2:: GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) .  
  
- `retvalRange`

  \[em] um ponteiro para uma estrutura de [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) que especifica o local da memória do valor de retorno da função.

  Para acessar informações de valor de retorno, o sinalizador de `COR_PRF_ENABLE_FUNCTION_RETVAL` deve ser definido. O criador de perfil pode usar o método [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) para definir os sinalizadores de evento.

## <a name="remarks"></a>Comentários  
 Os valores dos parâmetros `func` e `retvalRange` não são válidos depois que a função `FunctionLeave2` retorna, pois os valores podem ser alterados ou destruídos.  
  
 A função `FunctionLeave2` é um retorno de chamada; Você deve implementá-lo. A implementação deve usar o atributo de classe de armazenamento `__declspec`(`naked`).  
  
 O mecanismo de execução não salva nenhum registro antes de chamar essa função.  
  
- Na entrada, você deve salvar todos os registros que usar, incluindo aqueles na FPU (unidade de ponto flutuante).  
  
- Ao sair, você deve restaurar a pilha removendo todos os parâmetros que foram enviados por Push por seu chamador.  
  
 A implementação de `FunctionLeave2` não deve bloquear, pois atrasará a coleta de lixo. A implementação não deve tentar uma coleta de lixo porque a pilha pode não estar em um estado amigável de coleta de lixo. Se uma coleta de lixo for tentada, o tempo de execução será bloqueado até que `FunctionLeave2` retorne.  
  
 Além disso, a função `FunctionLeave2` não deve chamar um código gerenciado ou, de qualquer forma, causar uma alocação de memória gerenciada.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Função FunctionEnter2](functionenter2-function.md)
- [Função FunctionTailcall2](functiontailcall2-function.md)
- [Método SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [Criando perfil de funções estáticas globais](profiling-global-static-functions.md)
