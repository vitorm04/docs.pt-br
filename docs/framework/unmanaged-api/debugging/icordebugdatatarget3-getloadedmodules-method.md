---
title: Método ICorDebugDataTarget3::GetLoadedModules
ms.date: 03/30/2017
ms.assetid: 9a48c05b-1949-416e-933c-52549b6fcf5e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c51ce8ff76e0fc1588cdd136de83b77dcab0f10
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413489"
---
# <a name="icordebugdatatarget3getloadedmodules-method"></a>Método ICorDebugDataTarget3::GetLoadedModules
Obtém uma lista dos módulos que foram carregados até o momento.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetLoadedModules(  
   [in] ULONG32 cRequestedModules,  
   [out] ULONG32 *pcFetchedModules,  
   [out, size_is(cRequestedModules), length_is(*pcFetchedModules)] ICorDebugLoadedModule *pLoadedModules[]  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `cRequestedModules`  
 [in] O número de módulos para o qual as informações são solicitadas.  
  
 `pcFetchedModules`  
 [out] Um ponteiro para o número de módulos sobre quais informações foi retornadas.  
  
 `pLoadedModules`  
 [out] Um ponteiro para uma matriz de [ICorDebugLoadedModule](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md) objetos que fornecem informações sobre os módulos carregados.  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
>  Esse método só está disponível com o .NET Native.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebugDataTarget3](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-interface.md)  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
