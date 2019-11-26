---
title: Método IMetaDataImport2::EnumMethodSpecs
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumMethodSpecs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumMethodSpecs
helpviewer_keywords:
- IMetaDataImport2::EnumMethodSpecs method [.NET Framework metadata]
- EnumMethodSpecs method [.NET Framework metadata]
ms.assetid: b3fc1e6c-bcb6-4915-baf8-7dc0a31b8724
topic_type:
- apiref
ms.openlocfilehash: 4a1de144163ec2b4952bd16b59fb1c92b706631b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428302"
---
# <a name="imetadataimport2enummethodspecs-method"></a>Método IMetaDataImport2::EnumMethodSpecs
Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT EnumMethodSpecs (  
    [in, out] HCORENUM      *phEnum,   
    [in]      mdToken       tk,  
    [out]     mdMethodSpec  rMethodSpecs[],  
    [in]      ULONG         cMax,  
    [out]     ULONG         *pcMethodSpecs  
);   
```  
  
## <a name="parameters"></a>Parâmetros  
 `phEnum`  
 [in, out] A pointer to the enumerator for `rMethodSpecs`.  
  
 `tk`  
 [in] The MemberRef or MethodDef token that represents the method whose MethodSpec tokens are to be enumerated. If the value of `tk` is 0 (zero), all MethodSpec tokens in the scope will be enumerated.  
  
 `rMethodSpecs`  
 [out] The array of MethodSpec tokens to enumerate.  
  
 `cMax`  
 [in] The requested maximum number of tokens to place in `rMethodSpecs`.  
  
 `pcMethodSpecs`  
 [out] The returned number of tokens placed in `rMethodSpecs`.  
  
## <a name="return-value"></a>Valor retornado  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodSpecs` returned successfully.|  
|`S_FALSE`|`phEnum` has no member elements. In this case, `pcMethodSpecs` is set to 0 (zero).|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** Cor.h  
  
 **Library:** Used as a resource in MsCorEE.dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
