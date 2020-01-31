---
title: Função FunctionEnter3WithInfo
ms.date: 03/30/2017
api_name:
- FunctionEnter3WithInfo
api_location:
- mscorwks.cll
api_type:
- COM
f1_keywords:
- FunctionEnter3WithInfo
helpviewer_keywords:
- FunctionEnter3WithInfo function [.NET Framework profiling]
ms.assetid: 277c3344-d0cb-431e-beae-eb1eeeba8eea
topic_type:
- apiref
ms.openlocfilehash: 75a9a7174f105d99e9d1c9b220cfc5bf928d46ec
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866964"
---
# <a name="functionenter3withinfo-function"></a>Função FunctionEnter3WithInfo
Notifica o criador de perfil que o controle está sendo passado para uma função e fornece um identificador que pode ser passado para o [método ICorProfilerInfo3:: GetFunctionEnter3Info](icorprofilerinfo3-getfunctionenter3info-method.md) para recuperar o quadro de pilha e os argumentos de função.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
void __stdcall FunctionEnter3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a>Parâmetros

- `functionIDOrClientID`

  \[em] o identificador da função para o qual o controle é passado.

- `eltInfo`

  \[em] um identificador opaco que representa informações sobre um determinado registro de ativação. Esse identificador é válido somente durante o retorno de chamada ao qual é passado.

## <a name="remarks"></a>Comentários  
 O método de retorno de chamada `FunctionEnter3WithInfo` notifica o criador de perfil conforme as funções são chamadas e permite que o criador de perfil Use o [método ICorProfilerInfo3:: GetFunctionEnter3Info](icorprofilerinfo3-getfunctionenter3info-method.md) para inspecionar valores de argumento. Para acessar informações de argumento, o sinalizador de `COR_PRF_ENABLE_FUNCTION_ARGS` precisa ser definido. O criador de perfil pode usar o [método ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) para definir os sinalizadores de evento e, em seguida, usar o [método ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) para registrar sua implementação dessa função.  
  
 A função `FunctionEnter3WithInfo` é um retorno de chamada; Você deve implementá-lo. A implementação deve usar o `__declspec(naked)` atributo de classe de armazenamento.  
  
 O mecanismo de execução não salva nenhum registro antes de chamar essa função.  
  
- Na entrada, você deve salvar todos os registros que usar, incluindo aqueles na FPU (unidade de ponto flutuante).  
  
- Ao sair, você deve restaurar a pilha removendo todos os parâmetros que foram enviados por Push por seu chamador.  
  
 A implementação de `FunctionEnter3WithInfo` não deve bloquear, pois atrasará a coleta de lixo. A implementação não deve tentar uma coleta de lixo, pois a pilha pode não estar em um estado amigável de coleta de lixo. Se uma coleta de lixo for tentada, o tempo de execução será bloqueado até que `FunctionEnter3WithInfo` retorne.  
  
 A função `FunctionEnter3WithInfo` não deve chamar um código gerenciado ou causar uma alocação de memória gerenciada de qualquer forma.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [GetFunctionEnter3Info](icorprofilerinfo3-getfunctionenter3info-method.md)
- [FunctionEnter3](functionenter3-function.md)
- [FunctionLeave3](functionleave3-function.md)
- [Criando perfil de funções estáticas globais](profiling-global-static-functions.md)
