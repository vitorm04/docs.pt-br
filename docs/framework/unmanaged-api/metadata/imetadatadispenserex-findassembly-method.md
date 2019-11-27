---
title: Método IMetaDataDispenserEx::FindAssembly
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.FindAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::FindAssembly
helpviewer_keywords:
- FindAssembly method [.NET Framework metadata]
- IMetaDataDispenserEx::FindAssembly method [.NET Framework metadata]
ms.assetid: 3afe7252-5f28-48d9-a74d-1927566c404c
topic_type:
- apiref
ms.openlocfilehash: 2d974b7368dd01062d2d310d076dce05e102eb81
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442282"
---
# <a name="imetadatadispenserexfindassembly-method"></a>Método IMetaDataDispenserEx::FindAssembly
Este método não está implementado. Se chamado, ele retornará E_NOTIMPL.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT FindAssembly(  
    [in]  LPCWSTR  szAppBase,  
    [in]  LPCWSTR  szPrivateBin,  
    [in]  LPCWSTR  szGlobalBin,  
    [in]  LPCWSTR  szAssemblyName,  
    [out] LPCWSTR  szName,  
    [in]  ULONG    cchName,  
    [out] ULONG    *pcName  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `szAppBase`  
 no Não usado.  
  
 `szPrivateBin`  
 no Não usado.  
  
 `szGlobalBin`  
 no Não usado.  
  
 `szAssemblyName`  
 no O assembly a ser encontrado.  
  
 `szName`  
 fora O nome simples do assembly.  
  
 `cchName`  
 no O tamanho, em bytes, de `szName`.  
  
 `pcName`  
 fora O número de caracteres realmente retornados em `szName`.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataforma:** Consulte [requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Usado como um recurso em MsCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataDispenserEx](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [Interface IMetaDataDispenser](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
