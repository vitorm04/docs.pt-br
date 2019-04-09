---
title: Método IMetaDataAssemblyEmit::SetFileProps
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetFileProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetFileProps
helpviewer_keywords:
- IMetaDataAssemblyEmit::SetFileProps method [.NET Framework metadata]
- SetFileProps method [.NET Framework metadata]
ms.assetid: 85667d38-611c-45a9-938d-930ac7a7b681
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fd0c2da234fa89bbf92c2117d6428d64502da0c5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59208170"
---
# <a name="imetadataassemblyemitsetfileprops-method"></a>Método IMetaDataAssemblyEmit::SetFileProps
Modifica especificado `File` estrutura de metadados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetFileProps (  
    [in] mdFile        file,  
    [in] const void    *pbHashValue,   
    [in] ULONG         cbHashValue,  
    [in] DWORD         dwFileFlags  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `file`  
 [in] O token de metadados que especifica o `File` estrutura de metadados a ser modificado.  
  
 `pbHashValue`  
 [in] Um ponteiro para o hash de dados associado ao arquivo.  
  
 `cbHashValue`  
 [in] O tamanho em bytes do `pbHashValue`.  
  
 `dwFileFlags`  
 [in] Uma combinação bit a bit de [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) valores que especificam vários atributos do arquivo.  
  
## <a name="remarks"></a>Comentários  
 Para criar uma `File` estrutura de metadados, use o [imetadataassemblyemit:: Definefile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md) método.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
