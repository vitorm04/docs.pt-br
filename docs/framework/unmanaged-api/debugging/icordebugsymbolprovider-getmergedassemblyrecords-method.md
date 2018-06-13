---
title: Método ICorDebugSymbolProvider::GetMergedAssemblyRecords
ms.date: 03/30/2017
ms.assetid: cc4c510d-550d-4941-af34-81987caf3425
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 502e7e0b52bb147b5fe37dcc6e4f6d13d642b6f5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417538"
---
# <a name="icordebugsymbolprovidergetmergedassemblyrecords-method"></a>Método ICorDebugSymbolProvider::GetMergedAssemblyRecords
Obtém os registros de símbolo para todos os assemblies mesclados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetMergedAssemblyRecords(  
   [in] ULONG32 cRequestedRecords,  
   [out] ULONG32 *pcFetchedRecords,  
   [out, size_is(cRequestedRecords), length_is(*pcFetchedRecords)] ICorDebugMergedAssemblyRecord *pRecords[]  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `cRequestedRecords`  
 [in] O número de registros de símbolo solicitado.  
  
 `pcFetchedRecords`  
 [out] Um ponteiro para o número de registros de símbolo recuperados pelo método.  
  
 `pRecords`  
 Um ponteiro para uma matriz de [ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md) objetos.  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
>  Esse método só está disponível com o .NET Native.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
