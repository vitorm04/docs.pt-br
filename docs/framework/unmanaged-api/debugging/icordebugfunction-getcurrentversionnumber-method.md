---
title: Método ICorDebugFunction::GetCurrentVersionNumber
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 61b2de0595ac9330d9bb4e8e2dcbe4591928eb91
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
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
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
