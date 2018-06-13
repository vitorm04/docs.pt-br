---
title: Método IMetaDataImport::GetParamForMethodIndex
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetParamForMethodIndex
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetParamForMethodIndex
helpviewer_keywords:
- IMetaDataImport::GetParamForMethodIndex method [.NET Framework metadata]
- GetParamForMethodIndex method [.NET Framework metadata]
ms.assetid: ec3bfa95-1920-4511-932e-3ff23d76fcb8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 31096f7a5fd23bbd54f2beb9258c9d529e94f373
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448749"
---
# <a name="imetadataimportgetparamformethodindex-method"></a>Método IMetaDataImport::GetParamForMethodIndex
Obtém o token que representa um parâmetro especificado do método representado pelo token MethodDef especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetParamForMethodIndex (  
   [in]  mdMethodDef      md,  
   [in]  ULONG            ulParamSeq,  
   [out] mdParamDef       *ppd  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `md`  
 [in] Um token que representa o método para retornar o token do parâmetro.  
  
 `ulParamSeq`  
 [in] A posição ordinal na lista de parâmetros onde ocorre o parâmetro solicitado. Parâmetros são numerados a partir de um, com o valor de retorno do método na posição zero.  
  
 `ppd`  
 [out] Um ponteiro para um token de ParamDef que representa o parâmetro solicitado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
