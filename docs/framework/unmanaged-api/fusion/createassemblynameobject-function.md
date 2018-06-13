---
title: Função CreateAssemblyNameObject
ms.date: 03/30/2017
api_name:
- CreateAssemblyNameObject
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyNameObject
helpviewer_keywords:
- CreateAssemblyNameObject function [.NET Framework fusion]
ms.assetid: 55c8b41e-fbe4-4ae0-aa29-68fbb2311691
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5433c49db8e507c6026ab0e87040dd5634ad0808
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430432"
---
# <a name="createassemblynameobject-function"></a>Função CreateAssemblyNameObject
Obtém um ponteiro de interface para um [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) instância que representa a identidade exclusiva do assembly com o nome especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT CreateAssemblyNameObject (  
    [out] LPASSEMBLYNAME  *ppAssemblyNameObj,  
    [in]  LPCWSTR         szAssemblyName,  
    [in]  DWORD           dwFlags,  
    [in]  LPVOID          pvReserved  
 );  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppAssemblyNameObj`  
 [out] Retornado `IAssemblyName`.  
  
 `szAssemblyName`  
 [in] O nome do assembly para o qual criar o novo `IAssemblyName` instância.  
  
 `dwFlags`  
 [in] Sinalizadores para passar para o construtor do objeto.  
  
 `pvReserved`  
 [in] Reservado para extensibilidade futura. `pvReserved` deve ser uma referência nula.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Fusion.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [Funções estáticas globais de fusão](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
