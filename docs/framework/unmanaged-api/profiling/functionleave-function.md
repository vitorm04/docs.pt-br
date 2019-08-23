---
title: Função FunctionLeave
ms.date: 03/30/2017
api_name:
- FunctionLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave
helpviewer_keywords:
- FunctionLeave function [.NET Framework profiling]
ms.assetid: 18e89f45-e068-426a-be16-9f53a4346860
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 238a5f19bd8cbd89a5537b2b9297bfa9e1f54613
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952882"
---
# <a name="functionleave-function"></a>Função FunctionLeave
Notifica o criador de perfil de que uma função está prestes a retornar ao chamador.  
  
> [!NOTE]
> A `FunctionLeave` função foi preterida no .NET Framework 2,0. Ele continuará funcionando, mas incorrerá em uma penalidade de desempenho. Em vez disso, use a função [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
void __stdcall FunctionLeave (  
    [in] FunctionID funcID  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `funcID`  
 no O identificador da função que está retornando.  
  
## <a name="remarks"></a>Comentários  
 A `FunctionLeave` função é um retorno de chamada; você deve implementá-la. A implementação deve usar o `__declspec`atributo`naked`de classe de armazenamento ().  
  
 O mecanismo de execução não salva nenhum registro antes de chamar essa função.  
  
- Na entrada, você deve salvar todos os registros que usar, incluindo aqueles na FPU (unidade de ponto flutuante).  
  
- Ao sair, você deve restaurar a pilha removendo todos os parâmetros que foram enviados por Push por seu chamador.  
  
 A implementação de `FunctionLeave` não deve bloquear, pois atrasará a coleta de lixo. A implementação não deve tentar uma coleta de lixo porque a pilha pode não estar em um estado amigável de coleta de lixo. Se for feita uma tentativa de coleta de lixo, o tempo de `FunctionLeave` execução será bloqueado até o retorno.  
  
 Além disso, `FunctionLeave` a função não deve chamar um código gerenciado ou, de qualquer forma, causar uma alocação de memória gerenciada.  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl  
  
 **Biblioteca** CorGuids.lib  
  
 **.NET Framework versões:** 1.1, 1.0  
  
## <a name="see-also"></a>Consulte também

- [Função FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [Função FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [Função FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [Método SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [Criando perfil de funções estáticas globais](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
