---
title: Método ICorDebugStepper::SetInterceptMask
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetInterceptMask
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetInterceptMask
helpviewer_keywords:
- SetInterceptMask method [.NET Framework debugging]
- ICorDebugStepper::SetInterceptMask method [.NET Framework debugging]
ms.assetid: 6245e2ae-5cc2-43ff-8cc1-71953d12113a
topic_type:
- apiref
ms.openlocfilehash: e88fa543eca39c14962f0dbbe8053829713401c8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137576"
---
# <a name="icordebugsteppersetinterceptmask-method"></a>Método ICorDebugStepper::SetInterceptMask
Define um valor que especifica os tipos de código que são percorridos.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetInterceptMask (  
    [in] CorDebugIntercept    mask  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `mask`  
 no Uma combinação de valores da enumeração CorDebugIntercept que especifica os tipos de código.  
  
## <a name="remarks"></a>Comentários  
 Se o bit de um interceptor for definido, o stepper será concluído quando o tipo de código de interceptação for encontrado. Se o bit for apagado, o código de interceptação será ignorado.  
  
 O método `SetInterceptMask` pode ter interações imprevistas com [ICorDebugStepper:: SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) (do ponto de vista do usuário). Por exemplo, se a única parte visível (ou seja, não interna) do código de inicialização da classe não tiver informações de mapeamento e STOP_NO_MAPPING_INFO não estiver definido (consulte o método [ICorDebugStepper:: SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) e o CorDebugUnmappedStop Enumeração), o stepper passará pela inicialização da classe. Por padrão, somente o valor INTERCEPT_NONE da enumeração `CorDebugIntercept` será usado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
