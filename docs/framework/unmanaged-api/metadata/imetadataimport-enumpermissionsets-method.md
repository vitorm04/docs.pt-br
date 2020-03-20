---
title: Método IMetaDataImport::EnumPermissionSets
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumPermissionSets
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumPermissionSets
helpviewer_keywords:
- EnumPermissionSets method [.NET Framework metadata]
- IMetaDataImport::EnumPermissionSets method [.NET Framework metadata]
ms.assetid: 347d7e5c-c90f-45ad-bd1e-2c7912b0b19c
topic_type:
- apiref
ms.openlocfilehash: e628cf5dab8006b0df0ab6c60dc995cd0c6bb29d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175441"
---
# <a name="imetadataimportenumpermissionsets-method"></a>Método IMetaDataImport::EnumPermissionSets
Enumera permissões para os objetos em um escopo de metadados especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT EnumPermissionSets  
   [in, out] HCORENUM      *phEnum,
   [in]      mdToken       tk,
   [in]      DWORD         dwActions,  
   [out]     mdPermission  rPermission[],  
   [in]      ULONG         cMax,  
   [out]     ULONG         *pcTokens  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `phEnum`  
 [dentro, fora] Um ponteiro para o enumerador. Isto deve ser NULO para a primeira chamada deste método.  
  
 `tk`  
 [em] Um token de metadados que limita o escopo da pesquisa ou NULL para pesquisar o escopo mais amplo possível.  
  
 `dwActions`  
 [em] Bandeiras representando <xref:System.Security.Permissions.SecurityAction> os valores a serem incluemem , `rPermission`ou zero para retornar todas as ações.  
  
 `rPermission`  
 [fora] A matriz usada para armazenar os tokens de permissão.  
  
 `cMax`  
 [em] O tamanho máximo `rPermission` da matriz.  
  
 `pcTokens`  
 [fora] O número de tokens `rPermission`de permissão retornado em .  
  
## <a name="return-value"></a>Valor retornado  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|`S_OK`|`EnumPermissionSets`retornou com sucesso.|  
|`S_FALSE`|Não há tokens para enumerar. Nesse caso, `pcTokens` é zero.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Incluído como um recurso em MsCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
