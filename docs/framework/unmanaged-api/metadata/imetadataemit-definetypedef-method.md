---
title: Método IMetaDataEmit::DefineTypeDef
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineTypeDef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineTypeDef
helpviewer_keywords:
- IMetaDataEmit::DefineTypeDef method [.NET Framework metadata]
- DefineTypeDef method [.NET Framework metadata]
ms.assetid: dd11c485-be95-4b97-9cd8-68679a4fb432
topic_type:
- apiref
ms.openlocfilehash: 4f1c3e823b35fcf7d5935eee111e042b2291d216
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175753"
---
# <a name="imetadataemitdefinetypedef-method"></a>Método IMetaDataEmit::DefineTypeDef
Cria uma definição de tipo para um tipo de tempo de execução de idioma comum e obtém um token de metadados para essa definição de tipo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT DefineTypeDef (
    [in]  LPCWSTR     szTypeDef,
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[],
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `szTypeDef`  
 [em] O nome do tipo em Unicode.  
  
 `dwTypeDefFlags`  
 [em] `TypeDef` atributos. Isto é uma `CoreTypeAttr` pequena máscara de valores.  
  
 `tkExtends`  
 [em] O símbolo da classe base. Deve ser um `mdTypeDef` ou `mdTypeRef` um símbolo.  
  
 `rtkImplements`  
 [em] Uma matriz de tokens especificando as interfaces que esta classe ou interface implementa.  
  
 `ptd`  
 [fora] O `mdTypeDef` token atribuído.  
  
## <a name="remarks"></a>Comentários  
 Um sinalizador `dwTypeDefFlags` em especifica se o tipo que está sendo criado é um tipo de referência de sistema de tipo comum (classe ou interface) ou um tipo de valor de tipo comum.  
  
 Dependendo dos parâmetros fornecidos, este método, como `mdInterfaceImpl` efeito colateral, também pode criar um registro para cada interface herdada ou implementada por esse tipo. No entanto, este método `mdInterfaceImpl` não retorna nenhum desses tokens. Se um cliente quiser adicionar `mdInterfaceImpl` ou modificar um token posteriormente, ele deve usar a `IMetaDataImport` interface para enumera-los. Se você quiser usar a semântica COM da `[default]` interface, você `rtkImplements`deve fornecer a interface padrão como o primeiro elemento em ; um atributo personalizado definido na classe indicará que a classe tem uma `mdInterfaceImpl` interface padrão (que é sempre assumida como o primeiro token declarado para a classe).  
  
 Cada elemento `rtkImplements` da matriz `mdTypeDef` `mdTypeRef` contém um ou token. O último elemento na `mdTokenNil`matriz deve ser .  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como recurso em MSCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
