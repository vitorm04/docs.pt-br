---
title: Método IMetaDataEmit::SetClassLayout
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetClassLayout
helpviewer_keywords:
- IMetaDataEmit::SetClassLayout method [.NET Framework metadata]
- SetClassLayout method [.NET Framework metadata]
ms.assetid: 2576c449-388d-4434-a0e1-9f53991e11b6
topic_type:
- apiref
ms.openlocfilehash: 5214298c6ad9594548ab45ed583cb5b14ce1f30d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74441771"
---
# <a name="imetadataemitsetclasslayout-method"></a>Método IMetaDataEmit::SetClassLayout
Conclui o layout de campos para uma classe que foi definida por uma chamada anterior ao [método DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetClassLayout (  
    [in]  mdTypeDef           td,   
    [in]  DWORD               dwPackSize,   
    [in]  COR_FIELD_OFFSET    rFieldOffsets[],   
    [in]  ULONG               ulClassSize   
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `td`  
 no Um token `mdTypeDef` que especifica a classe a ser disposta.  
  
 `dwPackSize`  
 no O tamanho da embalagem: 1, 2, 4, 8 ou 16 bytes. O tamanho da embalagem é o número de bytes entre os campos adjacentes.  
  
 `rFieldOffsets`  
 no Uma matriz de estruturas [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) , cada uma delas especifica um campo da classe e o deslocamento do campo dentro da classe. Encerre a matriz com `mdTokenNil`.  
  
 `ulClassSize`  
 no O tamanho, em bytes, da classe.  
  
## <a name="remarks"></a>Comentários  
 A classe é definida inicialmente chamando o método [IMetaDataEmit::D efinetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) e especificando um dos três layouts para os campos da classe: automático, sequencial ou explícito. Normalmente, você usaria o layout automático e permite que o tempo de execução escolha a melhor maneira de modelar os campos.  
  
 No entanto, talvez você queira que os campos sejam dispostos de acordo com a organização usada pelo código não gerenciado. Nesse caso, escolha o layout sequencial ou explícito e chame `SetClassLayout` para concluir o layout dos campos:  
  
- Layout sequencial: especifique o tamanho da embalagem. Um campo é alinhado de acordo com seu tamanho natural ou o tamanho da embalagem, o que resultar no deslocamento menor do campo. Defina `rFieldOffsets` e `ulClassSize` como zero.  
  
- Layout explícito: especifique o deslocamento de cada campo ou especifique o tamanho da classe e o tamanho da embalagem.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Usado como um recurso em MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
