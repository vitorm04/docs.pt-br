---
title: "Método ICorDebugStepper::IsActive"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper.IsActive
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper::IsActive
helpviewer_keywords:
- IsActive method, ICorDebugStepper interface [.NET Framework debugging]
- ICorDebugStepper::IsActive method [.NET Framework debugging]
ms.assetid: 8b35e7a9-b40e-40a9-8d8e-b82e823fc575
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 25e4b59c59ee4340c14da22143f49c645e1dcc7b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugstepperisactive-method"></a>Método ICorDebugStepper::IsActive
Obtém um valor que indica se este ICorDebugStepper está atualmente executando uma etapa.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT IsActive (  
    [out] BOOL   *pbActive  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pbActive`  
 [out] Retorna `true` se o seletor está executando uma etapa; caso contrário, retornará `false`.  
  
## <a name="remarks"></a>Comentários  
 Qualquer ação de etapa permanece ativa até que o depurador recebe um [: Stepcomplete](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md) chamar, que automaticamente desativa o seletor. Um seletor também pode ser desativado prematuramente chamando [ICorDebugStepper](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md) antes do retorno de chamada condição for atingida.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
