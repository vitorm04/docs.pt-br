---
title: "Método IMetaDataConverter::GetTypeLibFromMetaData"
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
- IMetaDataConverter.GetTypeLibFromMetaData
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter::GetTypeLibFromMetaData
helpviewer_keywords:
- GetTypeLibFromMetaData method [.NET Framework metadata]
- IMetaDataConverter::GetTypeLibFromMetaData method [.NET Framework metadata]
ms.assetid: 90eab7b3-1fae-4af4-8bce-f7bc0e188a99
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1e7665eabf46d4bda822dcb41125ccfcee6d8516
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataconvertergettypelibfrommetadata-method"></a>Método IMetaDataConverter::GetTypeLibFromMetaData
Obtém um ponteiro para um `ITypeLib` instância que representa a biblioteca de tipos que tem os nomes de biblioteca e o módulo especificados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetTypeLibFromMetaData (  
    [in]  BSTR     strModule,   
    [in]  BSTR     strTlbName,   
    [out] ITypeLib **ppITL  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `strModule`  
 [in] O nome do módulo da biblioteca de tipos.  
  
 `strTlbName`  
 [in] O nome da biblioteca de tipos.  
  
 `ppITL`  
 [out] Um ponteiro para um local que recebe o endereço do `ITypeLib` instância que representa a biblioteca de tipos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataforma:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** usado como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMetaDataConverter](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-interface.md)
