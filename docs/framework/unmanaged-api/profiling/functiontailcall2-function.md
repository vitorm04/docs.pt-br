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
ms.openlocfilehash: 2d99c6d8bd2af02456c6a90143b524c337483868
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866876"
---
# <a name="functiontailcall2-function"></a>Função FunctionTailcall2
Notifica o criador de perfil de que a função atualmente em execução está prestes a executar uma chamada tail para outra função e fornece informações sobre o registro de ativação.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
void __stdcall FunctionTailcall2 (  
    [in] FunctionID         funcId,   
    [in] UINT_PTR           clientData,   
    [in] COR_PRF_FRAME_INFO func  
);  
```  
  
## <a name="parameters"></a>Parâmetros

- `funcId`

  \[em] o identificador da função atualmente em execução que está prestes a fazer uma chamada final.

- `clientData`

  \[in] o identificador da função remapeada, que o criador de perfil especificou anteriormente via [FunctionIDMapper](functionidmapper-function.md), da função atualmente em execução que está prestes a fazer uma chamada final.
  
- `func`

  \[em] um valor de `COR_PRF_FRAME_INFO` que aponta para informações sobre o registro de ativação.

  O criador de perfil deve tratar isso como um identificador opaco que pode ser passado de volta para o mecanismo de execução no método [ICorProfilerInfo2:: GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) .

## <a name="remarks"></a>Comentários  
 A função de destino da chamada tail usará o quadro de pilhas atual e retornará diretamente para o chamador da função que fez a chamada final. Isso significa que um retorno de chamada [FunctionLeave2](functionleave2-function.md) não será emitido para uma função que seja o destino de uma chamada tail.  
  
 O valor do parâmetro `func` não é válido depois que a função `FunctionTailcall2` retorna, pois o valor pode ser alterado ou destruído.  
  
 A função `FunctionTailcall2` é um retorno de chamada; Você deve implementá-lo. A implementação deve usar o atributo de classe de armazenamento `__declspec`(`naked`).  
  
 O mecanismo de execução não salva nenhum registro antes de chamar essa função.  
  
- Na entrada, você deve salvar todos os registros que usar, incluindo aqueles na FPU (unidade de ponto flutuante).  
  
- Ao sair, você deve restaurar a pilha removendo todos os parâmetros que foram enviados por Push por seu chamador.  
  
 A implementação de `FunctionTailcall2` não deve bloquear, pois atrasará a coleta de lixo. A implementação não deve tentar uma coleta de lixo porque a pilha pode não estar em um estado amigável de coleta de lixo. Se uma coleta de lixo for tentada, o tempo de execução será bloqueado até que `FunctionTailcall2` retorne.  
  
 Além disso, a função `FunctionTailcall2` não deve chamar um código gerenciado ou, de qualquer forma, causar uma alocação de memória gerenciada.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Função FunctionEnter2](functionenter2-function.md)
- [Função FunctionLeave2](functionleave2-function.md)
- [Método SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [Criando perfil de funções estáticas globais](profiling-global-static-functions.md)
