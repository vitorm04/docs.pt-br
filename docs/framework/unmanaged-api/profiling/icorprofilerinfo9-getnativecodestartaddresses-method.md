---
title: ICorProfilerInfo9::GetNativeCodeStartAddresses
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetNativeCodeStartAddresses
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: f5c7f11a322e4cf3ed38608e0f380dd632bc8fb6
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973806"
---
# <a name="icorprofilerinfo9getnativecodestartaddresses-method"></a>Método ICorProfilerInfo9:: GetNativeCodeStartAddresses
  
 Dada uma FunctionID e rejitId, enumera o endereço inicial do código de início de todas as versões com compilação JIT desse código que existem atualmente.   
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetNativeCodeStartAddresses( [in]  FunctionID functionID,
                                     [in]  ReJITID reJitId,
                                     [in]  ULONG32 cCodeStartAddresses,
                                     [out] ULONG32 *pcCodeStartAddresses,
                                     [out] UINT_PTR codeStartAddresses[]);
```  
  
#### <a name="parameters"></a>Parâmetros  
 `functionId`  
 no A ID da função cujos endereços de início de código nativo devem ser retornados.  
  
 `reJitId`  
 no A identidade da função de compilação JIT recompilada. 
  
 `cCodeStartAddresses` \
 no O tamanho máximo da `codeStartAddresses` matriz.

 `pcCodeStartAddresses` \
 fora O número de endereços disponíveis.

 `codeStartAddresses` \
 fora Uma matriz de `UINT_PTR`, cada uma delas é o endereço inicial de um corpo nativo para a função especificada. 

## <a name="remarks"></a>Comentários  
 Quando a compilação em camadas está habilitada, uma função pode ter mais de um corpo de código nativo. 

## <a name="requirements"></a>Requisitos  
 **Compatíveis** Consulte [sistemas operacionais com suporte do .NET Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca** CorGuids.lib  
  
 **Versões do .net:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)] 
  
## <a name="see-also"></a>Consulte também
- [Interface ICorProfilerInfo9](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-interface.md)

