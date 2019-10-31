---
title: Método ICorDebugEval2::CallParameterizedFunction
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.CallParameterizedFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::CallParameterizedFunction
helpviewer_keywords:
- ICorDebugEval2::CallParameterizedFunction method [.NET Framework debugging]
- CallParameterizedFunction method [.NET Framework debugging]
ms.assetid: 72f54a45-dbe6-4bb4-8c99-e879a27368e5
topic_type:
- apiref
ms.openlocfilehash: b521c96d26202119dad6fedb61cbd9da8b3c2e52
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137633"
---
# <a name="icordebugeval2callparameterizedfunction-method"></a>Método ICorDebugEval2::CallParameterizedFunction
Define uma chamada para o ICorDebugFunction especificado, que pode ser aninhado dentro de uma classe cujo construtor usa <xref:System.Type> parâmetros ou pode levar <xref:System.Type> parâmetros.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CallParameterizedFunction (  
    [in] ICorDebugFunction     *pFunction,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[],  
    [in] ULONG32               nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pFunction`  
 no Um ponteiro para um objeto `ICorDebugFunction` que representa a função a ser chamada.  
  
 `nTypeArgs`  
 no O número de argumentos que a função usa.  
  
 `ppTypeArgs`  
 no Uma matriz de ponteiros, cada um dos quais aponta para um objeto ICorDebugType que representa um argumento de função.  
  
 `nArgs`  
 no O número de valores passados na função.  
  
 `ppArgs`  
 no Uma matriz de ponteiros, cada um dos quais aponta para um objeto ICorDebugValue que representa um valor passado em um argumento de função.  
  
## <a name="remarks"></a>Comentários  
 `CallParameterizedFunction` é como [ICorDebugEval:: CallFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-callfunction-method.md) , exceto que a função pode estar dentro de uma classe com parâmetros de tipo, ela própria pode pegar parâmetros de tipo ou ambos. Os argumentos de tipo devem ser fornecidos primeiro para a classe e, em seguida, para a função.  
  
 Se a função estiver em um domínio de aplicativo diferente, ocorrerá uma transição. No entanto, todos os argumentos Type e Value devem estar no domínio do aplicativo de destino.  
  
 A avaliação de função pode ser executada somente em cenários limitados. Se `CallParameterizedFunction` ou `ICorDebugEval::CallFunction` falhar, o HRESULT retornado indicará o motivo mais geral possível para a falha.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
