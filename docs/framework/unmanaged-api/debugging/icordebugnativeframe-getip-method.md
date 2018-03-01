---
title: "Método ICorDebugNativeFrame::GetIP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugNativeFrame.GetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetIP
helpviewer_keywords:
- GetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
- ICorDebugNativeFrame::GetIP method [.NET Framework debugging]
ms.assetid: 99f693f3-d3b9-4fd8-9d09-b8efd03f7b67
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2f9ea20577b3132a2378013e7c5fa8356c14c8b7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugnativeframegetip-method"></a>Método ICorDebugNativeFrame::GetIP
Obtém o código nativo deslocamento local para o qual o ponteiro de instrução é definido no momento.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetIP (  
    [out] ULONG32           *pnOffset  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pnOffset`  
 [out] Um ponteiro para o local de deslocamento no código nativo.  
  
## <a name="remarks"></a>Comentários  
 Se o quadro de pilha é representado por esse "ICorDebugNativeFrame" estiver ativo, o deslocamento é o endereço da próxima instrução a ser executada. Se este quadro de pilha não estiver ativo, o deslocamento é o endereço da próxima instrução a ser executado quando o quadro de pilhas é reativado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 
