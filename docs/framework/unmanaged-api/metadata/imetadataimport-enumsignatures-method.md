---
title: Método IMetaDataImport::EnumSignatures
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumSignatures
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumSignatures
helpviewer_keywords:
- EnumSignatures method [.NET Framework metadata]
- IMetaDataImport::EnumSignatures method [.NET Framework metadata]
ms.assetid: d0d65060-6f90-42a2-95cf-6ffb04352996
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 61285b3de76f556b498c9815508275989eb96807
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54630977"
---
# <a name="imetadataimportenumsignatures-method"></a>Método IMetaDataImport::EnumSignatures
Enumera os tokens de assinatura que representa as assinaturas autônomas no escopo atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT EnumSignatures (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdSignature  rSignatures[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcSignatures  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `phEnum`  
 [no, out] Um ponteiro para o enumerador. Isso deve ser NULL para a primeira chamada desse método.  
  
 `rSignatures`  
 [out] A matriz usada para armazenar os tokens de assinatura.  
  
 `cMax`  
 [in] O tamanho máximo da `rSignatures` matriz.  
  
 `pcSignatures`  
 [out] O número de tokens de assinatura retornado no `rSignatures`.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|`S_OK`|`EnumSignatures` retornado com êxito.|  
|`S_FALSE`|Não há nenhum token para enumerar. Nesse caso, `pcSignatures` é zero.|  
  
## <a name="remarks"></a>Comentários  
 Os tokens de assinatura são criados pela [imetadataemit:: Gettokenfromsig](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromsig-method.md) método.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
