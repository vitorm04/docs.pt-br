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
ms.openlocfilehash: 388f227377ddf73fe1297e1c777bb1c0607c13d2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177878"
---
# <a name="imetadataassemblyemitdefineexportedtype-method"></a>Método IMetaDataAssemblyEmit::DefineExportedType
Cria `ExportedType` uma estrutura contendo metadados para o tipo exportado especificado e retorna o token de metadados associado.  
  
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
  
## <a name="parameters"></a>parâmetros  
 `szName`  
 [em] O nome do tipo a ser exportado. Para a versão 1.1 do tempo de execução do idioma comum, `TypeDef` o nome do tipo exportado deve corresponder exatamente ao nome dado no para o tipo.  
  
 `tkImplementation`  
 [em] Um token especificando onde o tipo exportado é implementado. Os valores válidos e seus significados associados são:  
  
- `mdFile`O tipo é implementado em um arquivo diferente dentro deste conjunto.  
  
- `mdAssemblyRef`O tipo é implementado em uma montagem diferente.  
  
- `mdExportedTYpe`O tipo está aninhado dentro de algum outro tipo.  
  
- `mdFileNil`O tipo está no mesmo arquivo do manifesto e não é um tipo aninhado.  
  
 `tkTypeDef`  
 [em] Um token para os metadados que especifica o tipo a ser exportado. Esse valor é `TypeDef` inserido na tabela do arquivo que implementa o tipo e só é relevante se esse arquivo estiver neste conjunto.  
  
 `dwExportedTypeFlags`  
 [em] Uma combinação bitwise dos valores de enumeração [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) que definem as configurações de propriedade para o tipo exportado.  
  
 `pmdct`  
 [fora] Um ponteiro para o token de metadados retornado que indica o tipo exportado.  
  
## <a name="remarks"></a>Comentários  
 Uma `ExportedType` estrutura de metadados deve ser definida para cada tipo que é exposto por esta montagem e que é implementada em um módulo diferente daquele que contém o manifesto.  
  
## <a name="requirements"></a>Requisitos  
 **Plataforma:** Consulte [os requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como recurso em MsCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
