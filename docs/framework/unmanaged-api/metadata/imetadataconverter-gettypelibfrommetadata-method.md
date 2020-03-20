---
title: Método IMetaDataConverter::GetTypeLibFromMetaData
ms.date: 03/30/2017
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
ms.openlocfilehash: ef573eb9a572c27e685289b2740a55e898be2093
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177626"
---
# <a name="imetadataconvertergettypelibfrommetadata-method"></a>Método IMetaDataConverter::GetTypeLibFromMetaData
Obtém um `ITypeLib` ponteiro para uma instância que representa a biblioteca de tipos que tem os nomes de biblioteca e módulo especificados.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetTypeLibFromMetaData (  
    [in]  BSTR     strModule,
    [in]  BSTR     strTlbName,
    [out] ITypeLib **ppITL  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `strModule`  
 [em] O nome do módulo da biblioteca do tipo.  
  
 `strTlbName`  
 [em] O nome da biblioteca do tipo.  
  
 `ppITL`  
 [fora] Um ponteiro para um local que `ITypeLib` recebe o endereço da instância que representa a biblioteca do tipo.  
  
## <a name="requirements"></a>Requisitos  
 **Plataforma:** Consulte [os requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como recurso em MsCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IMetaDataConverter](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-interface.md)
