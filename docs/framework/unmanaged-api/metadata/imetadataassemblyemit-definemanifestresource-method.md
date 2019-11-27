---
title: Método IMetaDataAssemblyEmit::DefineManifestResource
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineManifestResource
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineManifestResource
helpviewer_keywords:
- DefineManifestResource method [.NET Framework metadata]
- IMetaDataAssemblyEmit::DefineManifestResource method [.NET Framework metadata]
ms.assetid: 27f6d295-0fe9-4cda-b77e-6e7d5c53df09
topic_type:
- apiref
ms.openlocfilehash: 83170815f4aa65988bb6a6394bd466a0ba376ebf
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432057"
---
# <a name="imetadataassemblyemitdefinemanifestresource-method"></a>Método IMetaDataAssemblyEmit::DefineManifestResource
Cria uma estrutura de `ManifestResource` que contém metadados para o recurso de manifesto especificado e retorna o token de metadados associado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT DefineManifestResource (  
    [in] LPCWSTR                szName,   
    [in] mdToken                tkImplementation,   
    [in] DWORD                  dwOffset,   
    [in] DWORD                  dwResourceFlags,  
    [out] mdManifestResource    *pmdmr  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `szName`  
 no O nome do recurso.  
  
 `tkImplementation`  
 no Um token de metadados do tipo `mdtFile` ou `mdtAssemblyRef` que mapeia para o provedor de recursos. Um valor nulo indica que o arquivo no qual os metadados são inseridos é o provedor de recursos.  
  
 `dwOffset`  
 no O deslocamento para o início do recurso dentro do arquivo. Para recursos em arquivos autônomos, isso sempre será zero. Se o recurso for inserido em um arquivo PE (executável portátil), esse será um deslocamento do BLOB de recursos, que começa no local especificado no arquivo de cabeçalho cor. h.  
  
 `dwResourceFlags`  
 no Uma combinação de bits de valores de sinalizador que especifica configurações de propriedades para a definição de recurso.  
  
 `pmdmr`  
 fora Um ponteiro para o token de metadados retornado.  
  
## <a name="remarks"></a>Comentários  
 Uma estrutura de metadados `ManifestResource` deve ser definida para cada recurso que é implementado em cada um dos arquivos do assembly.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataforma:** Consulte [requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Usado como um recurso em MsCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
