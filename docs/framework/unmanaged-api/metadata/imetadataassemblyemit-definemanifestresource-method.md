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
ms.openlocfilehash: 48d688b64bbe9330a176ef073e96865b719ff2c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
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
  
#### <a name="parameters"></a>Parâmetros  
 `szName`  
 [in] O nome do recurso.  
  
 `tkImplementation`  
 [in] Um token de metadados do tipo `mdtFile` ou `mdtAssemblyRef` que mapeia para o provedor de recursos. Um valor NULL indica que o arquivo no qual os metadados é inserido é o provedor de recursos.  
  
 `dwOffset`  
 [in] O deslocamento para o início do recurso dentro do arquivo. Para obter recursos em arquivos independentes, sempre será zero. Se o recurso é inserido em um arquivo de PE (executável portátil), esse é um deslocamento do recurso BLOB, que inicia no local especificado no arquivo de cabeçalho cor.h.  
  
 `dwResourceFlags`  
 [in] Uma combinação bit a bit de valores de sinalizador que especifica as configurações de propriedade para a definição de recurso.  
  
 `pmdmr`  
 [out] Um ponteiro para o token de metadados retornados.  
  
## <a name="remarks"></a>Comentários  
 Um `ManifestResource` estrutura de metadados deve ser definida para cada recurso que é implementado em cada um dos arquivos do assembly.  
  
## <a name="requirements"></a>Requisitos  
 **Plataforma:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** usado como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
