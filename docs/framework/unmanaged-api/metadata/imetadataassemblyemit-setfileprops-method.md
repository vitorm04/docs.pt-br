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
ms.openlocfilehash: 25baa6ffda3d50915cc7898275d6a557c1b3e947
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176026"
---
# <a name="imetadataassemblyemitsetfileprops-method"></a>Método IMetaDataAssemblyEmit::SetFileProps
Modifica a estrutura `File` de metadados especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetFileProps (  
    [in] mdFile        file,  
    [in] const void    *pbHashValue,
    [in] ULONG         cbHashValue,  
    [in] DWORD         dwFileFlags  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `file`  
 [em] O token de metadados `File` que especifica a estrutura de metadados a ser modificada.  
  
 `pbHashValue`  
 [em] Um ponteiro para os dados hash associados ao arquivo.  
  
 `cbHashValue`  
 [em] O tamanho em bytes de `pbHashValue`.  
  
 `dwFileFlags`  
 [em] Uma combinação bitwise de valores [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) que especificam vários atributos do arquivo.  
  
## <a name="remarks"></a>Comentários  
 Para criar `File` uma estrutura de metadados, use o método [IMetaDataAssemblyEmit::DefineFile.](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md)  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como recurso em MsCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
