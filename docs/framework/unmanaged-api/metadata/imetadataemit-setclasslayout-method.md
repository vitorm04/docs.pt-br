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
ms.openlocfilehash: e855868d18fc6cffdd5d92cfa401606caf45b76c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177571"
---
# <a name="imetadataemitsetclasslayout-method"></a>Método IMetaDataEmit::SetClassLayout
Completa o layout dos campos para uma classe definida por uma chamada anterior ao [Método DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetClassLayout (  
    [in]  mdTypeDef           td,
    [in]  DWORD               dwPackSize,
    [in]  COR_FIELD_OFFSET    rFieldOffsets[],
    [in]  ULONG               ulClassSize
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `td`  
 [em] Um `mdTypeDef` token que especifica a classe a ser definida.  
  
 `dwPackSize`  
 [em] O tamanho da embalagem: 1, 2, 4, 8 ou 16 bytes. O tamanho da embalagem é o número de bytes entre campos adjacentes.  
  
 `rFieldOffsets`  
 [em] Uma matriz de [estruturas COR_FIELD_OFFSET,](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) cada uma das quais especifica um campo da classe e o deslocamento do campo dentro da classe. Termine a `mdTokenNil`matriz com .  
  
 `ulClassSize`  
 [em] O tamanho, em bytes, da classe.  
  
## <a name="remarks"></a>Comentários  
 A classe é definida inicialmente chamando o método [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) e especificando um dos três layouts para os campos da classe: automático, seqüencial ou explícito. Normalmente, você usaria layout automático e deixaria o tempo de execução escolher a melhor maneira de definir os campos.  
  
 No entanto, você pode querer os campos definidos de acordo com o arranjo que o código não gerenciado usa. Neste caso, escolha o layout seqüencial `SetClassLayout` ou explícito e ligue para concluir o layout dos campos:  
  
- Layout seqüencial: Especifique o tamanho da embalagem. Um campo é alinhado de acordo com seu tamanho natural ou o tamanho da embalagem, o que resultar na menor compensação do campo. Set `rFieldOffsets` `ulClassSize` e para zero.  
  
- Layout explícito: Especifique a compensação de cada campo ou especifique o tamanho da classe e o tamanho da embalagem.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como recurso em MSCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
