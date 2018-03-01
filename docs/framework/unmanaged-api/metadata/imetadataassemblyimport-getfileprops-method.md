---
title: "Método IMetaDataAssemblyImport::GetFileProps"
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
- IMetaDataAssemblyImport.GetFileProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetFileProps
helpviewer_keywords:
- GetFileProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetFileProps method [.NET Framework metadata]
ms.assetid: c5e6216f-ae3d-4697-9688-66b69c1251ec
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 55984c4adaf291e3b962514cdc3bea964d1c91bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyimportgetfileprops-method"></a>Método IMetaDataAssemblyImport::GetFileProps
Obtém as propriedades do arquivo com a assinatura de metadados especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetFileProps (  
    [in]  mdFile      mdf,   
    [out] LPWSTR      szName,   
    [in]  ULONG       cchName,   
    [out] ULONG       *pchName,   
    [out] const void  **ppbHashValue,   
    [out] ULONG       *pcbHashValue,   
    [out] DWORD       *pdwFileFlags  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `mdf`  
 [in] O `mdFile` token de metadados que representa o arquivo para o qual obter as propriedades.  
  
 `szName`  
 [out] O nome simples do arquivo.  
  
 `cchName`  
 [in] O tamanho, em caracteres largos, de `szName`.  
  
 `pchName`  
 [out] O número de caracteres largos realmente retornados em `szName`.  
  
 `ppbHashValue`  
 [out] Um ponteiro para o valor de hash. Este é o hash, usando o algoritmo SHA-1, do arquivo.  
  
 `pcbHashValue`  
 [out] O número de caracteres largos no valor de hash retornado.  
  
 `pdwFileFlags`  
 [out] Um ponteiro para os sinalizadores que descrevem os metadados aplicado a um arquivo. O valor de sinalizadores é uma combinação de um ou mais [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) valores.  
  
## <a name="requirements"></a>Requisitos  
 **Plataforma:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** usado como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
