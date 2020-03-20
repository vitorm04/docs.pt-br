---
title: Método IMetaDataEmit2::DefineGenericParam
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.DefineGenericParam
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::DefineGenericParam
helpviewer_keywords:
- IMetaDataEmit2::DefineGenericParam method [.NET Framework metadata]
- DefineGenericParam method [.NET Framework metadata]
ms.assetid: 47b2a3b6-907d-43dc-858d-1ae7dca1316a
topic_type:
- apiref
ms.openlocfilehash: 1868d13a9dbb73dbdf64e49c395bdbff02ce89d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177450"
---
# <a name="imetadataemit2definegenericparam-method"></a>Método IMetaDataEmit2::DefineGenericParam
Cria uma definição para um parâmetro de tipo genérico, e obtém um token para esse parâmetro de tipo genérico.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT DefineGenericParam (
    [in]  mdToken         tk,
    [in]  ULONG           ulParamSeq,
    [in]  DWORD           dwParamFlags,
    [in]  LPCWSTR         szname,
    [in]  DWORD           reserved,
    [in]  mdToken         rtkConstraints[],
    [out] mdGenericParam  *pgp  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `tk`  
 [em] Um `mdTypeDef` `mdMethodDef` ou token que representa o método ou construtor para o qual definir um parâmetro genérico.  
  
 `ulParamSeq`  
 [em] O índice do parâmetro genérico.  
  
 `dwParamFlags`  
 [em] Um valor da enumeração [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) que descreve o tipo para o parâmetro genérico.  
  
 `szname`  
 [em] O nome do parâmetro.  
  
 `reserved`  
 [em] Este parâmetro é reservado para a extensibilidade futura.  
  
 `rtkConstraints`  
 [em] Uma matriz de restrições de tipo com término zero. Os membros da `mdTypeDef` `mdTypeRef`matriz `mdTypeSpec` devem ser um token de metadados ou de metadados.  
  
 `pgp`  
 [fora] Um símbolo que representa o parâmetro genérico.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como recurso em MsCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
