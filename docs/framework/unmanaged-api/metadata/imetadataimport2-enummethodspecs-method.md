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
ms.openlocfilehash: 2df53ba53c64e042abc54a1d2ac043d301acdde9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177182"
---
# <a name="imetadataimport2enummethodspecs-method"></a>Método IMetaDataImport2::EnumMethodSpecs
Obtém um enumerador para uma matriz de tokens MethodSpec associados ao token MethodDef ou MemberRef especificado.  
  
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
  
## <a name="parameters"></a>parâmetros  
 `phEnum`  
 [dentro, fora] Um ponteiro para o enumerador para `rMethodSpecs`.  
  
 `tk`  
 [em] O token MemberRef ou MethodDef que representa o método cujos tokens MethodSpec devem ser enumerados. Se o `tk` valor for 0 (zero), todos os tokens MethodSpec no escopo serão enumerados.  
  
 `rMethodSpecs`  
 [fora] A matriz de tokens MethodSpec para enumerar.  
  
 `cMax`  
 [em] O número máximo solicitado de tokens para colocar em `rMethodSpecs`.  
  
 `pcMethodSpecs`  
 [fora] O número retornado de tokens colocados em `rMethodSpecs`.  
  
## <a name="return-value"></a>Valor retornado  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodSpecs`retornou com sucesso.|  
|`S_FALSE`|`phEnum`não tem elementos membros. Neste caso, `pcMethodSpecs` está definido como 0 (zero).|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como recurso em MsCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
