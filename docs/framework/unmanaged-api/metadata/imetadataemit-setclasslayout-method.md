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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e22cf8e540bfdb53ad243640dac110b5750e53e7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataemitsetclasslayout-method"></a>Método IMetaDataEmit::SetClassLayout
Conclui o layout dos campos de uma classe que tenha sido definido por uma chamada anterior ao [método DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetClassLayout (  
    [in]  mdTypeDef           td,   
    [in]  DWORD               dwPackSize,   
    [in]  COR_FIELD_OFFSET    rFieldOffsets[],   
    [in]  ULONG               ulClassSize   
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `td`  
 [in] Um `mdTypeDef` token que especifica a classe a ser dispostos.  
  
 `dwPackSize`  
 [in] O tamanho de remessa: 1, 2, 4, 8 ou 16 bytes. O tamanho de empacotamento é o número de bytes entre campos adjacentes.  
  
 `rFieldOffsets`  
 [in] Uma matriz de [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) estruturas, cada uma delas Especifica um campo da classe e o campo de deslocamento dentro da classe. Encerrar a matriz com `mdTokenNil`.  
  
 `ulClassSize`  
 [in] O tamanho, em bytes, da classe.  
  
## <a name="remarks"></a>Comentários  
 A classe é definida inicialmente chamando o [Definetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) método e especificando um dos três layouts para os campos da classe: automático, sequencial ou explícito. Normalmente, você usaria o layout automático e permitir que o tempo de execução escolhe a melhor maneira para dispor os campos.  
  
 Entretanto, você pode querer os campos organizados de acordo com a organização que usa código não gerenciado. Nesse caso, escolha o layout explícito ou sequencial e chame `SetClassLayout` para concluir o layout dos campos:  
  
-   Layout sequencial: especifique o tamanho de remessa. Um campo é alinhado de acordo com seu tamanho natural ou o tamanho de empacotamento, o que resulta no deslocamento menor do campo. Definir `rFieldOffsets` e `ulClassSize` como zero.  
  
-   Layout explícito: especifique o deslocamento de cada campo ou especifique o tamanho de classe e o tamanho de remessa.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** usado como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
