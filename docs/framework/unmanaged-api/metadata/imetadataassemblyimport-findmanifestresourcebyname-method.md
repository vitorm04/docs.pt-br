---
title: Método IMetaDataAssemblyImport::FindManifestResourceByName
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.FindManifestResourceByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::FindManifestResourceByName
helpviewer_keywords:
- FindManifestResourceByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindManifestResourceByName method [.NET Framework metadata]
ms.assetid: 7b72fa11-3866-402b-bdea-2b966b77cfe0
topic_type:
- apiref
ms.openlocfilehash: f0c390509a698fdc4682ba81182d4b407d8718c9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448258"
---
# <a name="imetadataassemblyimportfindmanifestresourcebyname-method"></a>Método IMetaDataAssemblyImport::FindManifestResourceByName
Obtém um ponteiro para o recurso de manifesto com o nome especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT FindManifestResourceByName (  
    [in]  LPCWSTR                szName,   
    [out] mdManifestResource     *ptkManifestResource  
);   
```  
  
## <a name="parameters"></a>Parâmetros  
 `szName`  
 no O nome do recurso.  
  
 `ptkManifestResource`  
 fora A matriz usada para armazenar os tokens de metadados de `mdManifestResource`, cada um dos quais representa um recurso de manifesto.  
  
## <a name="remarks"></a>Comentários  
 O método `FindManifestResourceByName` usa as regras padrão empregadas pelo Common Language Runtime para resolver referências.  
  
## <a name="requirements"></a>Requisitos  
 **Plataforma:** Consulte [requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Usado como um recurso em MsCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [Como o runtime localiza assemblies](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
