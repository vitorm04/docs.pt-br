---
title: "Método ICorDebugNativeFrame::CanSetIP"
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
- ICorDebugNativeFrame.CanSetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::CanSetIP
helpviewer_keywords:
- ICorDebugNativeFrame::CanSetIP method [.NET Framework debugging]
- CanSetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 13258ac6-f4e4-4f66-8fc3-f1244417a3c3
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b87ff9ae71b916a9a1141c2e5fedce7f79fbcd23
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugnativeframecansetip-method"></a>Método ICorDebugNativeFrame::CanSetIP
Obtém o HRESULT que indica se é seguro definir o ponteiro de instrução (IP) para o local de deslocamento especificado em código nativo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT CanSetIP (  
    [in] ULONG32            nOffset  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `nOffset`  
 [in] A configuração desejada para o ponteiro de instrução.  
  
## <a name="remarks"></a>Comentários  
 Use o `CanSetIP` método antes de chamar o [Icordebugnativeframe](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) método. Se `CanSetIP` retorna qualquer HRESULT que não sejam S_OK, você ainda pode invocar `ICorDebugNativeFrame::SetIP`, mas não há nenhuma garantia de que o depurador continuará a execução correta e segura do código que está sendo depurado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 
