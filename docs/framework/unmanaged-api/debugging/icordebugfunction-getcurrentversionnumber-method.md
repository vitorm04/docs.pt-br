---
title: "Método ICorDebugFunction::GetCurrentVersionNumber"
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
- ICorDebugFunction.GetCurrentVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetCurrentVersionNumber
helpviewer_keywords:
- GetCurrentVersionNumber method [.NET Framework debugging]
- ICorDebugFunction::GetCurrentVersionNumber method [.NET Framework debugging]
ms.assetid: c3af1575-cbe6-457a-bc08-c53460edcbc8
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0c230c8ca6da69b45d05b3319220eacfa6c1f212
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugfunctiongetcurrentversionnumber-method"></a>Método ICorDebugFunction::GetCurrentVersionNumber
Obtém o número de versão da edição mais recente feita na função representada pelo objeto ICorDebugFunction.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetCurrentVersionNumber (  
    [out] ULONG32 *pnCurrentVersion  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pnCurrentVersion`  
 [out] Um ponteiro para um valor inteiro que é o número de versão da edição mais recente feita a essa função.  
  
## <a name="remarks"></a>Comentários  
 O número de versão da edição mais recente feita a essa função pode ser maior que o número de versão da função em si. Use o [Icordebugfunction2](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getversionnumber-method.md) método ou o [Getversionnumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) método para recuperar o número de versão da função.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
