---
title: Método IMetaDataImport::EnumMethodsWithName
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodsWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodsWithName
helpviewer_keywords:
- IMetaDataImport::EnumMethodsWithName method [.NET Framework metadata]
- EnumMethodsWithName method [.NET Framework metadata]
ms.assetid: a8624913-2e23-46ad-a0c1-bb8eccbbf20f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f15ee906fb20cb60272cee3deffa68dbe852f689
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62042612"
---
# <a name="imetadataimportenummethodswithname-method"></a>Método IMetaDataImport::EnumMethodsWithName
Enumera métodos que têm o nome especificado e que são definidos pelo tipo referenciado pelo token de TypeDef especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT EnumMethodsWithName (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdTypeDef       cl,  
   [in]  LPCWSTR         szName,  
   [out] mdMethodDef     rMethods[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `phEnum`  
 [no, out] Um ponteiro para o enumerador. Isso deve ser NULL para a primeira chamada desse método.  
  
 `cl`  
 [in] Um token de TypeDef que representa o tipo cujos métodos para enumerar.  
  
 `szName`  
 [in] O nome que limita o escopo da enumeração.  
  
 `rMethods`  
 [out] A matriz usada para armazenar os tokens MethodDef.  
  
 `cMax`  
 [in] O tamanho máximo da `rMethods` matriz.  
  
 `pcTokens`  
 [out] O número de tokens MethodDef retornado no `rMethods`.  
  
## <a name="remarks"></a>Comentários  
 Esse método enumera os campos e métodos, mas não as propriedades ou eventos. Diferentemente [imetadataimport:: Enummethods](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md), `EnumMethodsWithName` descarta todos os tokens de método que não têm o nome especificado.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodsWithName` retornado com êxito.|  
|`S_FALSE`|Não há nenhum token para enumerar. Nesse caso, `pcTokens` é zero.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
