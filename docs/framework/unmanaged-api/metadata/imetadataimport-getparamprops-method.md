---
title: "Método IMetaDataImport::GetParamProps"
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
- IMetaDataImport.GetParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetParamProps
helpviewer_keywords:
- IMetaDataImport::GetParamProps method [.NET Framework metadata]
- GetParamProps method [.NET Framework metadata]
ms.assetid: 4d5e5f00-bcab-4f41-b191-176511a186a7
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f393ccd6296cb06498b30a29c7ea55f088e0a393
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetparamprops-method"></a>Método IMetaDataImport::GetParamProps
Obtém os valores de metadados para o parâmetro referenciado pelo ParamDef especificado token.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetParamProps (  
   [in]  mdParamDef      tk,  
   [out] mdMethodDef     *pmd,  
   [out] ULONG           *pulSequence,  
   [out] LPWSTR          szName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName,  
   [out] DWORD           *pdwAttr,  
   [out] DWORD           *pdwCPlusTypeFlag,  
   [out] UVCP_CONSTANT   *ppValue,  
   [out] ULONG           *pcchValue  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `tk`  
 [in] Um token de ParamDef que representa o parâmetro para retornar metadados.  
  
 `pmd`  
 [out] Um ponteiro para um token MethodDef que representa o método que utiliza o parâmetro.  
  
 `pulSequence`  
 [out] A posição ordinal do parâmetro na lista de argumentos de método.  
  
 `szName`  
 [out] Um buffer para armazenar o nome do parâmetro.  
  
 `cchName`  
 [in] O tamanho solicitado em caracteres largos de `szName`.  
  
 `pchName`  
 [out] O tamanho retornado em caracteres largos de `szName`.  
  
 `pdwAttr`  
 [out] Um ponteiro para os sinalizadores do atributo associado ao parâmetro.  
  
 `pdwCPlusTypeFlag`  
 [out] Um ponteiro para um sinalizador que especifica que o parâmetro é um <xref:System.ValueType>.  
  
 `ppValue`  
 [out] Um ponteiro para uma cadeia de caracteres constante retornado pelo parâmetro.  
  
 `pcchValue`  
 [out] O tamanho de `ppValue` em caracteres largos ou zero se `ppValue` não tem uma cadeia de caracteres.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
