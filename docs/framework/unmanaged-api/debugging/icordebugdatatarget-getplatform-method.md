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
ms.openlocfilehash: 5715f0634346dd0c6591cfe5687690aa0fba95f1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125312"
---
# <a name="icordebugdatatargetgetplatform-method"></a>Método ICorDebugDataTarget::GetPlatform
Fornece informações sobre a plataforma, incluindo arquitetura do processador e sistema operacional, em que o processo de destino está em execução.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetPlatform([out] CorDebugPlatform * pTargetPlatform);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pTargetPlatform`  
 fora Um ponteiro para uma enumeração [CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md) que descreve a plataforma de destino.  
  
## <a name="remarks"></a>Comentários  
 O valor de retorno de enumeração de `CorDebugPlatformEnum` é usado pela interface [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) para determinar os detalhes do processo de destino, como o tamanho do ponteiro, o layout do espaço de endereço, o conjunto de registros, o formato de instrução, o layout do contexto e as convenções de chamada.  
  
 O valor `pTargetPlatform` pode se referir a uma plataforma que está sendo emulada para o destino em vez de especificar o hardware real em uso. Por exemplo, um processo em execução no ambiente do Windows no Windows (WOW) em uma edição de 64 bits do sistema operacional Windows deve usar o valor `CORDB_PLATFORM_WINDOWS_X86` da enumeração [CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md) .  
  
 Esse método deve ter sucesso. Se falhar, a plataforma de destino será inutilizável. O método pode falhar pelos seguintes motivos:  
  
- A plataforma que está sendo emulada para o destino é inutilizável.  
  
- O hardware real na plataforma de destino é inutilizável.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
