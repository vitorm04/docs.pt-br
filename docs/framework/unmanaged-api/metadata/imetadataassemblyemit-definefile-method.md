---
title: "Método IMetaDataAssemblyEmit::DefineFile"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataAssemblyEmit.DefineFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineFile
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineFile method [.NET Framework metadata]
- DefineFile method [.NET Framework metadata]
ms.assetid: c065aadf-c1ca-4981-bde6-597042cb29c4
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 48584822d7a2f31c466401db3a24156a71ad7011
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyemitdefinefile-method"></a>Método IMetaDataAssemblyEmit::DefineFile
Cria um `File` estrutura de metadados que contém metadados para o assembly referenciado pelo assembly e retorna o token de metadados associados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT DefineFile (  
    [in]  LPCWSTR        szName,   
    [in]  const void     *pbHashValue,   
    [in]  ULONG          cbHashValue,  
    [in]  DWORD          dwFileFlags,  
    [out] mdFile         *pmdf  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `szName`  
 [in] O nome do arquivo a ser consumido.  
  
 `pbHashValue`  
 [in] Um ponteiro para o hash de dados associados ao assembly.  
  
 `cbHashValue`  
 [in] O tamanho em bytes do `pbHashValue`.  
  
 `dwFileFlags`  
 [in] Uma combinação bit a bit de `FileFlags` valores que especificam as configurações de propriedade.  
  
 `pmdf`  
 [out] Um ponteiro para retornado `File` token.  
  
## <a name="remarks"></a>Comentários  
 Um `File` estrutura de metadados deve ser definida para cada arquivo que fazia parte desse assembly no momento em que este assembly foi compilado, excluindo o arquivo que contém os metadados.  
  
## <a name="requirements"></a>Requisitos  
 **Plataforma:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** usado como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
