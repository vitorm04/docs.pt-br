---
title: "Método IMetaDataImport2::GetGenericParamProps"
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
- IMetaDataImport2.GetGenericParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetGenericParamProps
helpviewer_keywords:
- IMetaDataImport2::GetGenericParamProps method [.NET Framework metadata]
- GetGenericParamProps method [.NET Framework metadata]
ms.assetid: dbb21e67-712b-49e7-a27c-a1e73ffd46c5
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 70a9669e2f47c3b56f7b50dc96ed2d3ba8314c4e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimport2getgenericparamprops-method"></a>Método IMetaDataImport2::GetGenericParamProps
Obtém os metadados associados com o parâmetro genérico representado pelo token especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetGenericParamProps (  
   [in]  mdGenericParam  gp,  
   [out] ULONG           *pulParamSeq,  
   [out] DWORD           *pdwParamFlags,  
   [out] mdToken         *ptOwner,  
   [out] DWORD           *reserved,  
   [out] LPWSTR          wzName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `gp`  
 [in] O token que representa o parâmetro genérico para o qual retornar metadados.  
  
 `pulParamSeq`  
 [out] A posição ordinal do `Type` parâmetro no método ou Construtor de pai.  
  
 `pdwParamFlags`  
 [out] Um valor de [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeração que descreve o `Type` para o parâmetro genérico.  
  
 `ptOwner`  
 [out] Um token de TypeDef ou MethodDef que representa o proprietário do parâmetro.  
  
 `reserved`  
 [out] Reservado para extensibilidade futura.  
  
 `wzName`  
 [out] O nome do parâmetro genérico.  
  
 `cchName`  
 [in] O tamanho do `wzName` buffer.  
  
 `pchName`  
 [out] O tamanho retornado do nome, em caracteres largos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** usado como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
