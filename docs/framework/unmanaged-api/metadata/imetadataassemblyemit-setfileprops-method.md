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
ms.openlocfilehash: 106ffeee521f69a73628b1fb6a611abc733583f9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431877"
---
# <a name="imetadataassemblyemitsetfileprops-method"></a>Método IMetaDataAssemblyEmit::SetFileProps
Modifica a estrutura de metadados de `File` especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetFileProps (  
    [in] mdFile        file,  
    [in] const void    *pbHashValue,   
    [in] ULONG         cbHashValue,  
    [in] DWORD         dwFileFlags  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `file`  
 no O token de metadados que especifica a estrutura de metadados `File` a ser modificada.  
  
 `pbHashValue`  
 no Um ponteiro para os dados de hash associados ao arquivo.  
  
 `cbHashValue`  
 no O tamanho em bytes de `pbHashValue`.  
  
 `dwFileFlags`  
 no Uma combinação de bits de valores [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) que especifica vários atributos do arquivo.  
  
## <a name="remarks"></a>Comentários  
 Para criar uma estrutura de metadados `File`, use o método [IMetaDataAssemblyEmit::D efinefile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md) .  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Usado como um recurso em MsCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
