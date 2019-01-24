---
title: Método IMetaDataImport::GetTypeSpecFromToken
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetTypeSpecFromToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetTypeSpecFromToken
helpviewer_keywords:
- GetTypeSpecFromToken method [.NET Framework metadata]
- IMetaDataImport::GetTypeSpecFromToken method [.NET Framework metadata]
ms.assetid: ee518bda-3296-482e-a7b7-e9d51dd1a181
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 53d0f3bd991d502e4ddcad7df1e24d18af367e7a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54598388"
---
# <a name="imetadataimportgettypespecfromtoken-method"></a>Método IMetaDataImport::GetTypeSpecFromToken
Obtém a assinatura de metadados de binários da especificação do tipo representada pelo token especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetTypeSpecFromToken (   
   [in]  mdTypeSpec            typespec,   
   [out] PCCOR_SIGNATURE       *ppvSig,   
   [out] ULONG                 *pcbSig  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `typespec`  
 [in] O token de TypeSpec associado com a assinatura de metadados solicitada.  
  
 `ppvSig`  
 [out] Um ponteiro para a assinatura de metadados de binário.  
  
 `pcbSig`  
 [out] O tamanho, em bytes, da assinatura de metadados.  
  
## <a name="return-value"></a>Valor de retorno  
 Um HRESULT que indica êxito ou falha. Falhas podem ser testadas com a macro FAILED.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
