---
title: Método IMetaDataImport2::EnumGenericParamConstraints
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumGenericParamConstraints
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumGenericParamConstraints
helpviewer_keywords:
- EnumGenericParamConstraints method [.NET Framework metadata]
- IMetaDataImport2::EnumGenericParamConstraints method [.NET Framework metadata]
ms.assetid: 8a7d4e40-28fe-4e14-b801-4049880130e7
topic_type:
- apiref
ms.openlocfilehash: d1683965193801dbdee038ab06366178891fd978
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426730"
---
# <a name="imetadataimport2enumgenericparamconstraints-method"></a>Método IMetaDataImport2::EnumGenericParamConstraints
Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT EnumGenericParamConstraints (  
    [in, out] HCORENUM                *phEnum,  
    [in]  mdGenericParam              tk,  
    [out] mdGenericParamConstraint    rGenericParamConstraints[],  
    [in]  ULONG                       cMax,  
    [out] ULONG                       *pcGenericParamConstraints  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `phEnum`  
 [in, out] A pointer to the enumerator.  
  
 `tk`  
 [in]   A token that represents the generic parameter whose constraints are to be enumerated.  
  
 `rGenericParamConstraints`  
 [out] The array of generic parameter constraints to enumerate.  
  
 `cMax`  
 [in]   The requested maximum number of tokens to place in `rGenericParamConstraints`.  
  
 `pcGenericParamConstraints`  
 [out] A pointer to the number of tokens placed in `rGenericParamConstraints`.  
  
## <a name="return-value"></a>Valor retornado  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|`S_OK`|`EnumGenericParameterConstraints` returned successfully.|  
|`S_FALSE`|`phEnum` has no member elements. In this case, `pcGenericParameterConstraints` is set to 0 (zero).|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** Cor.h  
  
 **Library:** Used as a resource in MsCorEE.dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
