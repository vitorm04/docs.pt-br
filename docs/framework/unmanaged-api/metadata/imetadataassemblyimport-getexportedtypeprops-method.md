---
title: "Método IMetaDataAssemblyImport::GetExportedTypeProps"
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
- IMetaDataAssemblyImport.GetExportedTypeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetExportedTypeProps
helpviewer_keywords:
- GetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 25ca7623-5a55-4f09-b44a-36b03d142278
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7fc5bb8266814fc4f1333de78fce4b6af86893c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyimportgetexportedtypeprops-method"></a>Método IMetaDataAssemblyImport::GetExportedTypeProps
Obtém o conjunto de propriedades do tipo exportado com a assinatura de metadados especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetExportedTypeProps (  
    [in]  mdExportedType    mdct,   
    [out] LPWSTR            szName,   
    [in]  ULONG             cchName,   
    [out] ULONG             *pchName,   
    [out] mdToken           *ptkImplementation,   
    [out] mdTypeDef         *ptkTypeDef,   
    [out] DWORD             *pdwExportedTypeFlags  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `mdct`  
 [in] Um `mdExportedType` token de metadados que representa o tipo exportado.  
  
 `szName`  
 [out] O nome do tipo exportado.  
  
 `cchName`  
 [in] O tamanho, em caracteres largos, de `szName`.  
  
 `pchName`  
 [out] O número de caracteres largos, na verdade, retornadas no`szName`  
  
 `ptkImplementation`  
 [out] Um `mdFile`, `mdAssemblyRef`, ou `mdExportedType` token de metadados que contém ou que permitam o acesso às propriedades do tipo exportado.  
  
 `ptkTypeDef`  
 [out] Um ponteiro para um `mdTypeDef` token que representa um tipo no arquivo.  
  
 `pdwExportedTypeFlags`  
 [out] Um ponteiro para os sinalizadores que descrevem os metadados aplicado ao tipo exportado. O valor de sinalizadores pode ser um ou mais [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) valores.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** usado como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
