---
title: Método IMetaDataImport::GetPinvokeMap
ms.date: 03/30/2017
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
ms.openlocfilehash: c458fef77b49f522ca21dd5487731f4d43588cea
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437103"
---
# <a name="imetadataimportgetpinvokemap-method"></a>Método IMetaDataImport::GetPinvokeMap
Obtém um token ModuleRef para representar o assembly de destino de uma chamada PInvoke.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetPinvokeMap (  
   [in]  mdToken       tk,  
   [out] DWORD         *pdwMappingFlags,  
   [out] LPWSTR        szImportName,  
   [in]  ULONG         cchImportName,  
   [out] ULONG         *pchImportName,  
   [out] mdModuleRef   *pmrImportDLL  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `tk`  
 no Um token FieldDef ou MethodDef para obter os metadados de mapeamento do PInvoke.  
  
 `pdwMappingFlags`  
 fora Um ponteiro para sinalizadores usados para mapeamento. Esse valor é um bitmask da enumeração [CorPinvokeMap](../../../../docs/framework/unmanaged-api/metadata/corpinvokemap-enumeration.md) .  
  
 `szImportName`  
 fora O nome da DLL de destino não gerenciada.  
  
 `cchImportName`  
 no O tamanho em caracteres largos de `szImportName`.  
  
 `pchImportName`  
 fora O número de caracteres largos retornados em `szImportName`.  
  
 `pmrImportDLL`  
 fora Um ponteiro para um token de ModuleRef que representa a biblioteca de objetos de destino não gerenciado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Incluído como um recurso em MsCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
