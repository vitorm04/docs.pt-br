---
title: Método IMetaDataImport::EnumInterfaceImpls
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumInterfaceImpls
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumInterfaceImpls
helpviewer_keywords:
- IMetaDataImport::EnumInterfaceImpls method [.NET Framework metadata]
- EnumInterfaceImpls method [.NET Framework metadata]
ms.assetid: ba6e178f-128b-4e47-a13c-b4be73eb106c
topic_type:
- apiref
ms.openlocfilehash: b535fdd5027a26cc4dd0eafec9883f0186773dd1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175493"
---
# <a name="imetadataimportenuminterfaceimpls-method"></a>Método IMetaDataImport::EnumInterfaceImpls
Enumera todas as interfaces implementadas `TypeDef`pelo especificado .
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT EnumInterfaceImpls (  
   [in, out]  HCORENUM       *phEnum,
   [in]   mdTypeDef          td,  
   [out]  mdInterfaceImpl    rImpls[],
   [in]   ULONG              cMax,  
   [out]  ULONG*             pcImpls  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `phEnum`  
 [dentro, fora] Um ponteiro para o enumerador.  
  
 `td`  
 [em] O token do TypeDef cujos tokens MethodDef representando implementações de interface devem ser enumerados.  
  
 `rImpls`  
 [fora] A matriz usada para armazenar os tokens MethodDef.  
  
 `cMax`  
 [em] O comprimento máximo `rImpls` da matriz.  
  
 `pcImpls`  
 [fora] O número real de tokens retornou em `rImpls`.  
  
## <a name="return-value"></a>Valor retornado  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|`S_OK`|`EnumInterfaceImpls`retornou com sucesso.|  
|`S_FALSE`|Não há tokens MethodDef para enumerar. Nesse caso, `pcImpls` está definido como zero.|  

## <a name="remarks"></a>Comentários

A enumeração retorna `mdInterfaceImpl` uma coleção de tokens para `TypeDef`cada interface implementada pelo especificado . Os tokens de interface são devolvidos na ordem `DefineTypeDef` `SetTypeDefProps`em que as interfaces foram especificadas (através ou ). As propriedades dos `mdInterfaceImpl` tokens retornados podem ser consultadas usando [GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md).
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Incluído como um recurso em MsCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
