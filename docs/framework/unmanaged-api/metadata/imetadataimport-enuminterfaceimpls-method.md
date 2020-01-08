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
ms.openlocfilehash: ef7057ad19fd34750bd15d358e9c1ebb1289cd44
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75338060"
---
# <a name="imetadataimportenuminterfaceimpls-method"></a>Método IMetaDataImport::EnumInterfaceImpls
Enumera todas as interfaces implementadas pelo `TypeDef`especificado. 
  
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
  
## <a name="parameters"></a>Parâmetros  
 `phEnum`  
 [entrada, saída] Um ponteiro para o enumerador.  
  
 `td`  
 no O token do TypeDef cujos tokens MethodDef que representam implementações de interface devem ser enumerados.  
  
 `rImpls`  
 fora A matriz usada para armazenar os tokens MethodDef.  
  
 `cMax`  
 no O comprimento máximo da matriz de `rImpls`.  
  
 `pcImpls`  
 fora O número real de tokens retornados em `rImpls`.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|`S_OK`|`EnumInterfaceImpls` retornado com êxito.|  
|`S_FALSE`|Não há tokens MethodDef para enumerar. Nesse caso, `pcImpls` é definido como zero.|  

## <a name="remarks"></a>Comentários

A enumeração retorna uma coleção de tokens de `mdInterfaceImpl` para cada interface implementada pelo `TypeDef`especificado. Os tokens de interface são retornados na ordem em que as interfaces foram especificadas (por meio de `DefineTypeDef` ou `SetTypeDefProps`). As propriedades dos tokens de `mdInterfaceImpl` retornados podem ser consultadas usando [GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md).
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Incluído como um recurso em MsCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
