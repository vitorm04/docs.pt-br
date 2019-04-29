---
title: Método IMetaDataImport::GetTypeDefProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetTypeDefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetTypeDefProps
helpviewer_keywords:
- GetTypeDefProps method [.NET Framework metadata]
- IMetaDataImport::GetTypeDefProps method [.NET Framework metadata]
ms.assetid: 00061a25-ba05-47a7-b984-fd916b06b149
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a482c7a06efe888408206f2de569e0a8739b85b8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777485"
---
# <a name="imetadataimportgettypedefprops-method"></a>Método IMetaDataImport::GetTypeDefProps
Retorna informações de metadados para o <xref:System.Type> representado pelo token de TypeDef especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetTypeDefProps (  
   [in]  mdTypeDef   td,  
   [out] LPWSTR      szTypeDef,  
   [in]  ULONG       cchTypeDef,  
   [out] ULONG       *pchTypeDef,  
   [out] DWORD       *pdwTypeDefFlags,  
   [out] mdToken     *ptkExtends  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `td`  
 [in] O token de TypeDef que representa o tipo para retornar metadados.  
  
 `szTypeDef`  
 [out] Um buffer que contém o nome do tipo.  
  
 `cchTypeDef`  
 [in] O tamanho em caracteres largos da `szTypeDef`.  
  
 `pchTypeDef`  
 [out] O número de caracteres largos retornado no `szTypeDef`.  
  
 `pdwTypeDefFlags`  
 [out] Um ponteiro para os sinalizadores que modificam a definição de tipo. Esse valor é um bitmask do [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) enumeração.  
  
 `ptkExtends`  
 [out] Um token de metadados de TypeDef ou TypeRef que representa o tipo base do tipo solicitado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
