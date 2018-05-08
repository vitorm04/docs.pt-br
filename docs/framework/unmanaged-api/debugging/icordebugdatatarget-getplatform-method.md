---
title: Método ICorDebugDataTarget::GetPlatform
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.GetPlatform Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::GetPlatform
helpviewer_keywords:
- GetPlatform method [.NET Framework debugging]
- ICorDebugDataTarget::GetPlatform method [.NET Framework debugging]
ms.assetid: 9ee96c9d-7a3d-4129-a6cc-7675c7f2dda4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 17ae761b2d48552aded8191ddbea26552d8da277
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugdatatargetgetplatform-method"></a>Método ICorDebugDataTarget::GetPlatform
Fornece informações sobre a plataforma, incluindo arquitetura de processador e sistema operacional, que está executando o processo de destino.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetPlatform([out] CorDebugPlatform * pTargetPlatform);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pTargetPlatform`  
 [out] Um ponteiro para um [CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md) enumeração que descreve a plataforma de destino.  
  
## <a name="remarks"></a>Comentários  
 O `CorDebugPlatformEnum` valor de retorno de enumeração é usado pelo [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface para determinar os detalhes do processo de destino como o tamanho do ponteiro, layout do espaço de endereço, conjunto de registro, formato de instrução, layout de contexto, e convenções de chamada.  
  
 O `pTargetPlatform` valor pode se referir a uma plataforma que está sendo emulada para o destino em vez de especificar o hardware atual em uso. Por exemplo, um processo que esteja executando o Windows no ambiente do Windows (WOW) em uma edição de 64 bits do sistema operacional Windows deve usar o `CORDB_PLATFORM_WINDOWS_X86` valor o [CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md) enumeração.  
  
 Esse método deve ter êxito. Se ele falhar, a plataforma de destino é inutilizável. O método pode falhar pelos seguintes motivos:  
  
-   A plataforma que está sendo emulada para o destino não é utilizável.  
  
-   O hardware real na plataforma de destino não é utilizável.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
