---
title: "Método IMetaDataAssemblyEmit::SetManifestResourceProps"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.SetManifestResourceProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::SetManifestResourceProps
helpviewer_keywords:
- SetManifestResourceProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetManifestResourceProps method [.NET Framework metadata]
ms.assetid: ef77efd1-849c-4e51-ba92-7ee3d2bf0339
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e3cc447b18ac6ccabd642ab0a1fb5b887fb4fbe4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
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
 [in] Uma combinação bit a bit de valores de sinalizador que especifica os atributos do recurso.  
  
## <a name="remarks"></a>Comentários  
 Para criar um `ManifestResource` estrutura de metadados, use o [Imetadataassemblyemit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md) método.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** usado como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
