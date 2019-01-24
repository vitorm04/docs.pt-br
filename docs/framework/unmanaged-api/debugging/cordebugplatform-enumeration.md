---
title: Enumeração CorDebugPlatform
ms.date: 03/30/2017
api_name:
- CorDebugPlatformEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugPlatformEnum
helpviewer_keywords:
- CorDebugPlatformEnum enumeration [.NET Framework debugging]
ms.assetid: c5444816-7378-4521-afd3-bf5e4b5303d5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d8cbf09ab4ad0192902a964d55a050685b024284
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574294"
---
# <a name="cordebugplatform-enumeration"></a>Enumeração CorDebugPlatform
Fornece valores de plataforma de destino que são usados pela [icordebugdatatarget:: Getplatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) método.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum CorDebugPlatform  
{  
    CORDB_PLATFORM_WINDOWS_X86,    // Windows on Intel x86  
    CORDB_PLATFORM_WINDOWS_AMD64,  // Windows x64 (AMD64, Intel EM64T)  
    CORDB_PLATFORM_WINDOWS_IA64,   // Windows on Intel IA-64  
    CORDB_PLATFORM_MAC_PPC,        // Macintosh OS on PowerPC  
    CORDB_PLATFORM_MAC_X86,        // Macintosh OS on Intel x86  
    CORDB_PLATFORM_WINDOWS_ARM,    // Windows on ARM  
    CORDB_PLATFORM_MAC_AMD64       // MacOS on Intel x64  
} CorDebugPlatform;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|CORDB_PLATFORM_WINDOWS_X86|A plataforma de destino é Windows executando em hardware Intel x86.|  
|CORDB_PLATFORM_WINDOWS_AMD64|A plataforma de destino é Windows de 64 bits executando em hardware AMD64 ou Intel EM64T.|  
|CORDB_PLATFORM_WINDOWS_IA64|A plataforma de destino é Windows de 32 bits executando em hardware Intel IA-64.|  
|CORDB_PLATFORM_MAC_PPC|A plataforma de destino é o sistema operacional Macintosh executando em hardware PowerPC.|  
|CORDB_PLATFORM_MAC_X86|A plataforma de destino é o sistema operacional Macintosh executando em hardware Intel x86.|  
|CORDB_PLATFORM_WINDOWS_ARM|A plataforma de destino é o sistema operacional Macintosh executando em hardware Windows ARM.|  
|CORDB_PLATFORM_MAC_AMD64|A plataforma de destino é o sistema operacional Macintosh executando em hardware AMD64.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
 Os membros `CORDB_PLATFORM_WINDOWS_ARM` e `CORDB_PLATFORM_MAC_AMD64` estão disponíveis no .NET Framework 4.5.2 e em versões posteriores.  
  
## <a name="see-also"></a>Consulte também
- [Declarando enumerações](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
