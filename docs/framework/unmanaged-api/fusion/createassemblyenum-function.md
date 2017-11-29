---
title: "Função CreateAssemblyEnum"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateAssemblyEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type: DLLExport
f1_keywords: CreateAssemblyEnum
helpviewer_keywords: CreateAssemblyEnum function [.NET Framework fusion]
ms.assetid: 3506df38-6cea-42f6-946e-4287863bcfb3
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c229496a79b146b5dcac3d06fa3efd9237e39d3a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="createassemblyenum-function"></a>Função CreateAssemblyEnum
Obtém um ponteiro para um [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) instância que pode enumerar os objetos no assembly com especificado [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT CreateAssemblyEnum (  
    [out] IAssemblyEnum  **pEnum,  
    [in]  IUnknown       *pUnkReserved,  
    [in]  IAssemblyName  *pName,  
    [in]  DWORD          dwFlags,  
    [in]  LPVOID         pvReserved  
 );  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pEnum`  
 [out] Ponteiro para um local de memória que contém a solicitação `IAssemblyEnum` ponteiro.  
  
 `pUnkReserved`  
 [in] Reservado para extensibilidade futura. `pUnkReserved`deve ser uma referência nula.  
  
 `pName`  
 [in] O `IAssemblyName` do assembly solicitado. Esse nome é usado para filtrar a enumeração. Ele pode ser nulo para enumerar todos os assemblies no cache de assembly global.  
  
 `dwFlags`  
 [in] Sinalizadores para modificar o comportamento do enumerador. Este parâmetro contém exatamente um bit do [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) enumeração.  
  
 `pvReserved`  
 [in] Reservado para extensibilidade futura. `pvReserved`deve ser uma referência nula.  
  
## <a name="remarks"></a>Comentários  
 O `dwFlags` parâmetro contém exatamente um bit do `ASM_CACHE_FLAGS` enumeração.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Fusion.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)  
 [Interface IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [Funções estáticas globais de fusão](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
