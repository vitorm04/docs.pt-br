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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cba4eb2b76d7057a5ed66a35342a79615cb8539f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934817"
---
# <a name="icordebugeval2callparameterizedfunction-method"></a>Método ICorDebugEval2::CallParameterizedFunction
Configura uma chamada para o ICorDebugFunction especificado, que pode ser aninhada dentro de uma classe cujo construtor obtém <xref:System.Type> parâmetros, ou pode próprio levar <xref:System.Type> parâmetros.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
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
 [in] Um ponteiro para um `ICorDebugFunction` objeto que representa a função a ser chamado.  
  
 `nTypeArgs`  
 [in] O número de argumentos que usa a função.  
  
 `ppTypeArgs`  
 [in] Uma matriz de ponteiros, cada um deles aponta para um objeto de ICorDebugType que representa um argumento de função.  
  
 `nArgs`  
 [in] O número de valores passados na função.  
  
 `ppArgs`  
 [in] Uma matriz de ponteiros, cada um deles aponta para um objeto ICorDebugValue que representa um valor passado um argumento de função.  
  
## <a name="remarks"></a>Comentários  
 `CallParameterizedFunction` é como [icordebugeval:: CallFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-callfunction-method.md) , exceto que a função possa ser dentro de uma classe com parâmetros de tipo, em si levará de parâmetros de tipo, ou ambos. Os argumentos de tipo devem ser fornecidos pela primeira vez para a classe e, em seguida, para a função.  
  
 Se a função estiver em um domínio de aplicativo diferente, uma transição ocorrerá. No entanto, todos os argumentos de tipo e o valor devem ser no domínio de aplicativo de destino.  
  
 A avaliação da função pode ser executada apenas em cenários limitados. Se `CallParameterizedFunction` ou `ICorDebugEval::CallFunction` falhar, o HRESULT retornado indicará o mais geral possível motivo da falha.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
