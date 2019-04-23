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
ms.openlocfilehash: d7f8cccf8d583645982eb37f6afcb553914679ad
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59075638"
---
# <a name="imetadataimportgetfieldprops-method"></a>Método IMetaDataImport::GetFieldProps
Obtém o token de metadados associados ao campo referido pelo FieldDef especificado.  
  
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
  
## <a name="parameters"></a>Parâmetros  
 `mb`  
 [in] Um token de FieldDef que representa o campo para obter os metadados associados para.  
  
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
 [out] O tamanho em caracteres de `ppValue`, ou zero, se nenhuma cadeia de caracteres existe.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
