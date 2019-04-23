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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b617e29e2df22b59114c8b978daa645de1cc6176
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59186713"
---
# <a name="imetadataassemblyemitdefinemanifestresource-method"></a>Método IMetaDataAssemblyEmit::DefineManifestResource
Cria um `ManifestResource` estrutura que contém metadados para o recurso de manifesto especificado e retorna o token de metadados associados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
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
 [in] O nome do recurso.  
  
 `tkImplementation`  
 [in] Um token de metadados do tipo `mdtFile` ou `mdtAssemblyRef` que é mapeado para o provedor de recursos. Um valor NULL indica que o arquivo no qual os metadados é inserido é o provedor de recursos.  
  
 `dwOffset`  
 [in] O deslocamento para o início do recurso dentro do arquivo. Para obter recursos em arquivos autônomos, isso sempre será zero. Se o recurso estiver incorporado em um arquivo de PE (executável portátil), esse é um deslocamento do recurso BLOB, que é iniciado no local especificado no arquivo de cabeçalho cor.h.  
  
 `dwResourceFlags`  
 [in] Uma combinação bit a bit dos valores de sinalizador que especificam configurações de propriedade para a definição de recurso.  
  
 `pmdmr`  
 [out] Um ponteiro para o token de metadados retornados.  
  
## <a name="remarks"></a>Comentários  
 Um `ManifestResource` estrutura de metadados deve ser definida para cada recurso que é implementado em cada um dos arquivos do assembly.  
  
## <a name="requirements"></a>Requisitos  
 **Plataforma:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
