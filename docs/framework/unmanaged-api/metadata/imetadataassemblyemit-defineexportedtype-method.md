---
title: Método IMetaDataAssemblyEmit::DefineExportedType
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineExportedType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineExportedType
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineExportedType method [.NET Framework metadata]
- DefineExportedType method [.NET Framework metadata]
ms.assetid: fad01d7a-3178-4c8c-9f0a-4641e3701c9b
topic_type:
- apiref
ms.openlocfilehash: 44f97ef498eb8e64c55fc86b9f290b9e088293f6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432073"
---
# <a name="imetadataassemblyemitdefineexportedtype-method"></a>Método IMetaDataAssemblyEmit::DefineExportedType
Cria uma estrutura de `ExportedType` que contém metadados para o tipo exportado especificado e retorna o token de metadados associado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT DefineExportedType (  
    [in]  LPCWSTR             szName,  
    [in]  mdToken             tkImplementation,   
    [in]  mdTypeDef           tkTypeDef,  
    [in]  DWORD               dwExportedTypeFlags,  
    [out] mdExportedType      *pmdct  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `szName`  
 no O nome do tipo a ser exportado. Para a versão 1,1 do Common Language Runtime, o nome do tipo exportado deve corresponder exatamente ao nome fornecido no `TypeDef` para o tipo.  
  
 `tkImplementation`  
 no Um token que especifica onde o tipo exportado é implementado. Os valores válidos e seus significados associados são:  
  
- `mdFile` o tipo é implementado em um arquivo diferente dentro desse assembly.  
  
- `mdAssemblyRef` o tipo é implementado em um assembly diferente.  
  
- `mdExportedTYpe` o tipo é aninhado em algum outro tipo.  
  
- `mdFileNil` o tipo está no mesmo arquivo que o manifesto e não é um tipo aninhado.  
  
 `tkTypeDef`  
 no Um token para os metadados que especifica o tipo a ser exportado. Esse valor é inserido na tabela `TypeDef` no arquivo que implementa o tipo e é relevante apenas se esse arquivo estiver nesse assembly.  
  
 `dwExportedTypeFlags`  
 no Uma combinação de bits de [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) de valores de enumeração que define as configurações de propriedade para o tipo exportado.  
  
 `pmdct`  
 fora Um ponteiro para o token de metadados retornado que indica o tipo exportado.  
  
## <a name="remarks"></a>Comentários  
 Uma estrutura de metadados `ExportedType` deve ser definida para cada tipo exposto por esse assembly e implementada em um módulo que não seja aquele que contém o manifesto.  
  
## <a name="requirements"></a>Requisitos  
 **Plataforma:** Consulte [requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Usado como um recurso em MsCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
