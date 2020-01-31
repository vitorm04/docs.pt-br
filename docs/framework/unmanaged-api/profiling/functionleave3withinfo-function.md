---
title: Função FunctionLeave3WithInfo
ms.date: 03/30/2017
api_name:
- FunctionLeave3WithInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave3WithInfo
helpviewer_keywords:
- FunctionLeave3WithInfo function [.NET Framework profiling]
ms.assetid: 5fa68a67-ced6-41c6-a2c0-467060fd0692
topic_type:
- apiref
ms.openlocfilehash: f7a945fb7ef10f995be2d779a88b98bbce2fdfb3
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866837"
---
# <a name="functionleave3withinfo-function"></a>Função FunctionLeave3WithInfo
Notifica o criador de perfil que o controle está sendo retornado de uma função e fornece um identificador que pode ser passado para o [método ICorProfilerInfo3:: GetFunctionLeave3Info](icorprofilerinfo3-getfunctionleave3info-method.md) para recuperar o quadro de pilha e o valor de retorno.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
void __stdcall FunctionLeave3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a>Parâmetros

- `functionIDOrClientID`

  \[em] o identificador da função da qual o controle é retornado.

- `eltInfo`

  \[em] um identificador opaco que representa informações sobre um determinado registro de ativação. Esse identificador é válido somente durante o retorno de chamada ao qual é passado.

## <a name="remarks"></a>Comentários  
 O método de retorno de chamada `FunctionLeave3WithInfo` notifica o criador de perfil conforme as funções são chamadas e permite que o criador de perfil Use o [método ICorProfilerInfo3:: GetFunctionLeave3Info](icorprofilerinfo3-getfunctionleave3info-method.md) para inspecionar o valor de retorno. Para acessar informações de valor de retorno, o sinalizador de `COR_PRF_ENABLE_FUNCTION_RETVAL` precisa ser definido. O criador de perfil pode usar o [método ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) para definir os sinalizadores de evento e, em seguida, usar o [método ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) para registrar sua implementação dessa função.  
  
 A função `FunctionLeave3WithInfo` é um retorno de chamada; Você deve implementá-lo. A implementação deve usar o `__declspec(naked)` atributo de classe de armazenamento.  
  
 O mecanismo de execução não salva nenhum registro antes de chamar essa função.  
  
- Na entrada, você deve salvar todos os registros que usar, incluindo aqueles na FPU (unidade de ponto flutuante).  
  
- Ao sair, você deve restaurar a pilha removendo todos os parâmetros que foram enviados por Push por seu chamador.  
  
 A implementação de `FunctionLeave3WithInfo` não deve bloquear, pois atrasará a coleta de lixo. A implementação não deve tentar uma coleta de lixo, pois a pilha pode não estar em um estado amigável de coleta de lixo. Se uma coleta de lixo for tentada, o tempo de execução será bloqueado até que `FunctionLeave3WithInfo` retorne.  
  
 A função `FunctionLeave3WithInfo` não deve chamar um código gerenciado ou causar uma alocação de memória gerenciada de qualquer forma.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [GetFunctionLeave3Info](icorprofilerinfo3-getfunctionleave3info-method.md)
- [FunctionEnter3](functionenter3-function.md)
- [FunctionLeave3](functionleave3-function.md)
- [FunctionTailcall3](functiontailcall3-function.md)
- [FunctionEnter3WithInfo](functionenter3withinfo-function.md)
- [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md)
- [SetEnterLeaveFunctionHooks3](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md)
- [SetFunctionIDMapper2](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [Criando perfil de funções estáticas globais](profiling-global-static-functions.md)
