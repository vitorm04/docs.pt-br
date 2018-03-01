---
title: "Método IMetaDataImport::GetPinvokeMap"
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
- IMetaDataImport.GetPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPinvokeMap
helpviewer_keywords:
- IMetaDataImport::GetPinvokeMap method [.NET Framework metadata]
- GetPinvokeMap method [.NET Framework metadata]
ms.assetid: b8685c1e-b80c-4198-8eb3-748d6f48a99e
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a28d628040a35d309515703563239a5f802dc4a1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetpinvokemap-method"></a>Método IMetaDataImport::GetPinvokeMap
Obtém um ModuleRef token para representar o assembly de destino de uma chamada de PInvoke.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetPinvokeMap (  
   [in]  mdToken       tk,  
   [out] DWORD         *pdwMappingFlags,  
   [out] LPWSTR        szImportName,  
   [in]  ULONG         cchImportName,  
   [out] ULONG         *pchImportName,  
   [out] mdModuleRef   *pmrImportDLL  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `tk`  
 [in] Um token para obter os metadados de mapeamento de PInvoke para FieldDef ou MethodDef.  
  
 `pdwMappingFlags`  
 [out] Um ponteiro para sinalizadores usados para mapeamento. Esse valor é um bitmask do [CorPinvokeMap](../../../../docs/framework/unmanaged-api/metadata/corpinvokemap-enumeration.md) enumeração.  
  
 `szImportName`  
 [out] O nome do DLL não gerenciada de destino.  
  
 `cchImportName`  
 [in] O tamanho em caracteres largos de `szImportName`.  
  
 `pchImportName`  
 [out] O número de caracteres largos retornados em `szImportName`.  
  
 `pmrImportDLL`  
 [out] Um ponteiro para um token de ModuleRef que representa a biblioteca de objeto de destino não gerenciada.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
