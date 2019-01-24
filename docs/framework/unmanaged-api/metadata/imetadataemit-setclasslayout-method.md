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
ms.openlocfilehash: 2dc1664551683066a33fb52e16e4909506601f2a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54588685"
---
# <a name="imetadataemitsetclasslayout-method"></a>Método IMetaDataEmit::SetClassLayout
Conclui o layout dos campos para uma classe que foi definido por uma chamada anterior ao [método DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).  
  
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
 [in] O tamanho de empacotamento: 1, 2, 4, 8 ou 16 bytes. O tamanho do empacotamento é o número de bytes entre campos adjacentes.  
  
 `rFieldOffsets`  
 [in] Uma matriz de [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) estruturas, cada um deles especifica um campo da classe e o campo de deslocamento dentro da classe. Encerrar a matriz com `mdTokenNil`.  
  
 `ulClassSize`  
 [in] O tamanho, em bytes, da classe.  
  
## <a name="remarks"></a>Comentários  
 A classe é definida inicialmente por meio da chamada a [imetadataemit:: Definetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) método e especificando um dos três layouts para os campos da classe: automático, sequencial ou explícito. Normalmente, você usaria o layout automático e permitir que o tempo de execução escolhe a melhor maneira para dispor os campos.  
  
 No entanto, convém os campos dispostos de acordo com a organização não gerenciadas de código usa. Nesse caso, escolha o layout explícito ou sequencial e chame `SetClassLayout` para concluir o layout dos campos:  
  
-   Layout sequencial: Especifique o tamanho de empacotamento. Um campo é alinhado de acordo com seu tamanho natural ou o tamanho de empacotamento, seja qual for o resultados no deslocamento do campo menor. Definir `rFieldOffsets` e `ulClassSize` como zero.  
  
-   Layout explícito: Especifique o deslocamento de cada campo ou especificar o tamanho de classe e o tamanho de empacotamento.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
