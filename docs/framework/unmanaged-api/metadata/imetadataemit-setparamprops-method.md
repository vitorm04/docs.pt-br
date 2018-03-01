---
title: "Método IMetaDataEmit::SetParamProps"
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
- IMetaDataEmit.SetParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetParamProps
helpviewer_keywords:
- IMetaDataEmit::SetParamProps method [.NET Framework metadata]
- SetParamProps method [.NET Framework metadata]
ms.assetid: a95a3908-9f87-4084-937e-8e01ef03ad63
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e8ada9deddf8528321797c1f9bd06b5b775ac4bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitsetparamprops-method"></a>Método IMetaDataEmit::SetParamProps
Define ou altera os recursos de um parâmetro de método definido por uma chamada anterior ao [: Defineparam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetParamProps (   
    [in]  mdParamDef  pd,   
    [in]  LPCWSTR     szName,   
    [in]  DWORD       dwParamFlags,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,   
    [in]  ULONG       cchValue   
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pd`  
 [in] O token para o parâmetro de destino.  
  
 `szName`  
 [in] O nome do parâmetro em Unicode.  
  
 `dwParamFlags`  
 [in] Os sinalizadores para o parâmetro.  
  
 `dwCPlusTypeFlag`  
 [in] O ELEMENT_TYPE _ * para o valor da constante.  
  
 `pValue`  
 [in] O valor da constante para o parâmetro.  
  
 `cchValue`  
 [in] O tamanho em caracteres (Unicode) do `pValue`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** usado como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
