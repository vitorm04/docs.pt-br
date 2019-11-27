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
ms.openlocfilehash: 3dfdd473b01bfe83def52f957c52e0f4d11375ad
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434387"
---
# <a name="imetadataemitdefinetyperefbyname-method"></a>Método IMetaDataEmit::DefineTypeRefByName
Obtém um token de metadados para um tipo que é definido no escopo especificado, que está fora do escopo atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT DefineTypeRefByName (   
    [in]  mdToken     tkResolutionScope,   
    [in]  LPCWSTR     szName,   
    [out] mdTypeRef   *ptr   
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `tkResolutionScope`  
 no O token que especifica o escopo de resolução. Os seguintes tipos de token são válidos:  
  
- `mdModuleRef`, se o tipo for definido no mesmo assembly no qual o chamador está definido.  
  
- `mdAssemblyRef`, se o tipo for definido em um assembly diferente daquele em que o chamador é definido.  
  
- `mdTypeRef`, se o tipo for um tipo aninhado.  
  
- `mdModule`, se o tipo for definido no mesmo módulo no qual o chamador é definido.  
  
- NULL, se o tipo for definido globalmente.  
  
 `szName`  
 no O nome do tipo de destino em Unicode.  
  
 `ptr`  
 fora Um ponteiro para o `mdTypeRef` token que é atribuído ao tipo.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Usado como um recurso em MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
