---
title: Método IMetaDataImport2::EnumMethodSpecs
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumMethodSpecs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumMethodSpecs
helpviewer_keywords:
- IMetaDataImport2::EnumMethodSpecs method [.NET Framework metadata]
- EnumMethodSpecs method [.NET Framework metadata]
ms.assetid: b3fc1e6c-bcb6-4915-baf8-7dc0a31b8724
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6c2122c06c6e4f1137173f02e37fb0982864e7ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448368"
---
# <a name="imetadataimport2enummethodspecs-method"></a>Método IMetaDataImport2::EnumMethodSpecs
Obtém um enumerador para uma matriz de tokens MethodSpec associados com a especificada MethodDef ou MemberRef token.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT EnumMethodSpecs (  
    [in, out] HCORENUM      *phEnum,   
    [in]      mdToken       tk,  
    [out]     mdMethodSpec  rMethodSpecs[],  
    [in]      ULONG         cMax,  
    [out]     ULONG         *pcMethodSpecs  
);   
```  
  
#### <a name="parameters"></a>Parâmetros  
 `phEnum`  
 [out no] Um ponteiro para o enumerador para `rMethodSpecs`.  
  
 `tk`  
 [in] O token de MemberRef ou MethodDef que representa o método cujos MethodSpec tokens são a serem enumerados. Se o valor de `tk` é 0 (zero), todos os tokens de MethodSpec no escopo serão enumerados.  
  
 `rMethodSpecs`  
 [out] A matriz de tokens MethodSpec enumerar.  
  
 `cMax`  
 [in] O número máximo solicitado de tokens para colocar em `rMethodSpecs`.  
  
 `pcMethodSpecs`  
 [out] O número retornado de tokens são colocados em `rMethodSpecs`.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodSpecs` retornou com êxito.|  
|`S_FALSE`|`phEnum` não tem nenhum elemento de membro. Nesse caso, `pcMethodSpecs` é definido como 0 (zero).|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** usado como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
