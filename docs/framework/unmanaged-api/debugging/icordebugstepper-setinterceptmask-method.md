---
title: "Método ICorDebugStepper::SetInterceptMask"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper.SetInterceptMask
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper::SetInterceptMask
helpviewer_keywords:
- SetInterceptMask method [.NET Framework debugging]
- ICorDebugStepper::SetInterceptMask method [.NET Framework debugging]
ms.assetid: 6245e2ae-5cc2-43ff-8cc1-71953d12113a
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2a99b504c0ce58ca6b89153667598cd4c2c682d9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugsteppersetinterceptmask-method"></a>Método ICorDebugStepper::SetInterceptMask
Define um valor que especifica os tipos de código que são entrado em.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetInterceptMask (  
    [in] CorDebugIntercept    mask  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `mask`  
 [in] Uma combinação de valores da enumeração CorDebugIntercept que especifica os tipos de código.  
  
## <a name="remarks"></a>Comentários  
 Se o bit de um interceptor for definido, o seletor será concluída quando o tipo determinado de interceptação de código é encontrado. Se o bit estiver desmarcado, o código interceptando será ignorado.  
  
 O `SetInterceptMask` método pode ter imprevistas interações com [: Setunmappedstopmask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) (a partir do ponto de vista do usuário). Por exemplo, se visível somente (ou seja, não interno) parte do código de inicialização de classe não tem informações de mapeamento e STOP_NO_MAPPING_INFO não está definido (consulte o [: Setunmappedstopmask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) método e o Enumeração CorDebugUnmappedStop), o seletor orientará sobre a inicialização de classe. Por padrão, somente o valor INTERCEPT_NONE do `CorDebugIntercept` enumeração será usada.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
