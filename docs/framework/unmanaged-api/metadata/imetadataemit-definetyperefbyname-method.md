---
title: Método IMetaDataEmit::DefineTypeRefByName
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineTypeRefByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineTypeRefByName
helpviewer_keywords:
- DefineTypeRefByName method [.NET Framework metadata]
- IMetaDataEmit::DefineTypeRefByName method [.NET Framework metadata]
ms.assetid: c30a4ce3-2d3e-411a-98df-e62ac4a5dd50
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4dd08afba664a491b3ba398f3da4c6a73cda5378
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54517130"
---
# <a name="imetadataemitdefinetyperefbyname-method"></a>Método IMetaDataEmit::DefineTypeRefByName
Obtém os metadados de um token para um tipo que é definido no escopo especificado, que está fora do escopo atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT DefineTypeRefByName (   
    [in]  mdToken     tkResolutionScope,   
    [in]  LPCWSTR     szName,   
    [out] mdTypeRef   *ptr   
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `tkResolutionScope`  
 [in] O token especificando o escopo de resolução. Os seguintes tipos de token são válidos:  
  
-   `mdModuleRef`, se o tipo é definido no mesmo assembly no qual o chamador é definido.  
  
-   `mdAssemblyRef`, se o tipo é definido em um assembly diferente no qual o chamador é definido.  
  
-   `mdTypeRef`, se o tipo for um tipo aninhado.  
  
-   `mdModule`, se o tipo é definido no mesmo módulo no qual o chamador é definido.  
  
-   Nulo, se o tipo é definido globalmente.  
  
 `szName`  
 [in] O nome do tipo de destino em Unicode.  
  
 `ptr`  
 [out] Um ponteiro para o `mdTypeRef` token que é atribuído ao tipo.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
