---
title: Método IMetaDataImport::GetScopeProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetScopeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetScopeProps
helpviewer_keywords:
- IMetaDataImport::GetScopeProps method [.NET Framework metadata]
- GetScopeProps method [.NET Framework metadata]
ms.assetid: c8ba42d2-d9fa-43cb-bbc0-f33e1e592cb6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0e5d998bd85f1cc872acde74fdf954299a279c40
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466265"
---
# <a name="imetadataimportgetscopeprops-method"></a>Método IMetaDataImport::GetScopeProps
Obtém o nome e, opcionalmente, o identificador de versão do assembly ou módulo no escopo atual de metadados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetScopeProps (  
   [out] LPWSTR           szName,  
   [in]  ULONG            cchName,  
   [out] ULONG            *pchName,  
   [out, optional] GUID   *pmvid  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `szName`  
 [out] Um buffer para o nome do assembly ou módulo.  
  
 `cchName`  
 [in] O tamanho em caracteres largos da `szName`.  
  
 `pchName`  
 [out] O número de caracteres largos retornado no `szName`.  
  
 `pmvid`  
 [out, opcional] Um ponteiro para um GUID que identifica com exclusividade a versão do assembly ou módulo.  
  
## <a name="remarks"></a>Comentários  
 O [imetadataemit:: Setmoduleprops](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) método é usado para definir essas propriedades.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
