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
ms.openlocfilehash: 77d9ec0cf1cbca63382e7f29de85c2f9566dc2bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416160"
---
# <a name="icordebugeval2callparameterizedfunction-method"></a>Método ICorDebugEval2::CallParameterizedFunction
Configura uma chamada para o ICorDebugFunction especificado, que pode ser aninhado dentro de uma classe cujo construtor obtém <xref:System.Type> parâmetros, ou podem ser próprio levar <xref:System.Type> parâmetros.  
  
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
  
#### <a name="parameters"></a>Parâmetros  
 `pFunction`  
 [in] Um ponteiro para um `ICorDebugFunction` objeto que representa a função a ser chamado.  
  
 `nTypeArgs`  
 [in] O número de argumentos que usa a função.  
  
 `ppTypeArgs`  
 [in] Uma matriz de ponteiros, cada um deles aponta para um objeto ICorDebugType que representa um argumento de função.  
  
 `nArgs`  
 [in] O número de valores passados na função.  
  
 `ppArgs`  
 [in] Uma matriz de ponteiros, cada um deles aponta para um objeto ICorDebugValue que representa um valor passado um argumento de função.  
  
## <a name="remarks"></a>Comentários  
 `CallParameterizedFunction` é como [: CallFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-callfunction-method.md) exceto que a função pode ser dentro de uma classe com parâmetros de tipo, se levará de parâmetros de tipo, ou ambos. Os argumentos de tipo devem ser fornecidos pela primeira vez para a classe e, em seguida, para a função.  
  
 Se a função está em um domínio de aplicativo diferente, ocorrerá uma transição. No entanto, todos os argumentos de tipo e o valor devem ser no domínio de aplicativo de destino.  
  
 Avaliação de função pode ser executada somente em cenários limitados. Se `CallParameterizedFunction` ou `ICorDebugEval::CallFunction` falhar, o HRESULT retornado indicará o mais geral possível motivo da falha.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
