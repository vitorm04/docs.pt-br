---
title: Método IMetaDataAssemblyEmit::SetManifestResourceProps
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetManifestResourceProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetManifestResourceProps
helpviewer_keywords:
- SetManifestResourceProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetManifestResourceProps method [.NET Framework metadata]
ms.assetid: ef77efd1-849c-4e51-ba92-7ee3d2bf0339
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d92129bd7c51ba2fa574f8337ba2b3727ab7b172
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54599043"
---
# <a name="imetadataassemblyemitsetmanifestresourceprops-method"></a>Método IMetaDataAssemblyEmit::SetManifestResourceProps
Modifica especificado `ManifestResource` estrutura de metadados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetManifestResourceProps (  
    [in] mdManifestResource  mr,  
    [in] mdToken             tkImplementation,   
    [in] DWORD               dwOffset,  
    [in] DWORD               dwResourceFlags  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `mr`  
 [in] O token que especifica o `ManifestResource` estrutura de metadados a ser modificado.  
  
 `tkImplementation`  
 [in] O token, do tipo `File` ou `AssemblyRef`, que é mapeado para o provedor de recursos.  
  
 `dwOffset`  
 [in] O deslocamento para o início do recurso dentro do arquivo.  
  
 `dwResourceFlags`  
 [in] Uma combinação bit a bit dos valores de sinalizador que especificam os atributos do recurso.  
  
## <a name="remarks"></a>Comentários  
 Para criar uma `ManifestResource` estrutura de metadados, use o [imetadataassemblyemit:: Definemanifestresource](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md) método.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
