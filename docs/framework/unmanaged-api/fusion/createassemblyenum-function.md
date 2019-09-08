---
title: Função CreateAssemblyEnum
ms.date: 03/30/2017
api_name:
- CreateAssemblyEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyEnum
helpviewer_keywords:
- CreateAssemblyEnum function [.NET Framework fusion]
ms.assetid: 3506df38-6cea-42f6-946e-4287863bcfb3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1db72c44b53b5abff9aee35094abc1e0e577fad4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795379"
---
# <a name="createassemblyenum-function"></a>Função CreateAssemblyEnum
Obtém um ponteiro para uma instância de [IAssemblyEnum](iassemblyenum-interface.md) que pode enumerar os objetos no assembly com o [IAssemblyName](iassemblyname-interface.md)especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CreateAssemblyEnum (  
    [out] IAssemblyEnum  **pEnum,  
    [in]  IUnknown       *pUnkReserved,  
    [in]  IAssemblyName  *pName,  
    [in]  DWORD          dwFlags,  
    [in]  LPVOID         pvReserved  
 );  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pEnum`  
 fora Ponteiro para um local de memória que contém o `IAssemblyEnum` ponteiro solicitado.  
  
 `pUnkReserved`  
 no Reservado para extensibilidade futura. `pUnkReserved`deve ser uma referência nula.  
  
 `pName`  
 no O `IAssemblyName` do assembly solicitado. Esse nome é usado para filtrar a enumeração. Pode ser NULL para enumerar todos os assemblies no cache de assembly global.  
  
 `dwFlags`  
 no Sinalizadores para modificar o comportamento do enumerador. Esse parâmetro contém exatamente um bit da enumeração [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md) .  
  
 `pvReserved`  
 no Reservado para extensibilidade futura. `pvReserved`deve ser uma referência nula.  
  
## <a name="remarks"></a>Comentários  
 O `dwFlags` parâmetro contém exatamente um bit `ASM_CACHE_FLAGS` da enumeração.  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** Fusion. h  
  
 **Biblioteca** Incluído como um recurso em MsCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IAssemblyEnum](iassemblyenum-interface.md)
- [Interface IAssemblyName](iassemblyname-interface.md)
- [Funções estáticas globais de fusão](fusion-global-static-functions.md)
