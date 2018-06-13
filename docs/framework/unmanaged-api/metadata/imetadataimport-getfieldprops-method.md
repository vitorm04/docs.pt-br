---
title: Método IMetaDataImport::GetFieldProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetFieldProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetFieldProps
helpviewer_keywords:
- IMetaDataImport::GetFieldProps method [.NET Framework metadata]
- GetFieldProps method [.NET Framework metadata]
ms.assetid: 7b0e9b10-8cef-4ba6-8432-40bf63e65ab1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 04b6c04868efff31253b2d723c5783060382212b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448967"
---
# <a name="imetadataimportgetfieldprops-method"></a>Método IMetaDataImport::GetFieldProps
Obtém os metadados associados ao campo referenciado pelo FieldDef especificado token.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetFieldProps (  
   [in]  mdFieldDef        mb,   
   [out] mdTypeDef         *pClass,  
   [out] LPWSTR            szField,  
   [in]  ULONG             cchField,   
   [out] ULONG             *pchField,  
   [out] DWORD             *pdwAttr,  
   [in]  PCCOR_SIGNATURE   *ppvSigBlob,   
   [out] ULONG             *pcbSigBlob,   
   [out] DWORD             *pdwCPlusTypeFlag,   
   [out] UVCP_CONSTANT     *ppValue,  
   [out] ULONG             *pcchValue  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `mb`  
 [in] Um token de FieldDef que representa os metadados associados para o campo.  
  
 `pClass`  
 [out] Um ponteiro para um token de TypeDef que representa o tipo da classe que o campo pertence.  
  
 `szField`  
 [out] O nome do campo.  
  
 `cchField`  
 [in] O tamanho em caracteres largos do buffer para *szField*.  
  
 `pchField`  
 [out] O tamanho real do buffer retornado.  
  
 `pdwAttr`  
 [out] Sinalizadores associados com os metadados do campo.  
  
 `ppvSigBlob`  
 [in] Um ponteiro para o valor binário de metadados que descreve o campo.  
  
 `pcbSigBlob`  
 [out] O tamanho em bytes do `ppvSigBlob`.  
  
 `pdwCPlusTypeFlag`  
 [out] Um sinalizador que especifica o tipo de valor do campo.  
  
 `ppValue`  
 [out] Um valor constante para o campo.  
  
 `pcchValue`  
 [out] O tamanho em caracteres de `ppValue`, ou zero não se existir nenhuma cadeia de caracteres.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
