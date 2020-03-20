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
ms.openlocfilehash: 8c3f98a124dbbcae3b0500932a2357ed1757951f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177240"
---
# <a name="imetadataimportgetfieldprops-method"></a>Método IMetaDataImport::GetFieldProps
Obtém metadados associados ao campo referenciado pelo token FieldDef especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
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
  
## <a name="parameters"></a>parâmetros  
 `mb`  
 [em] Um token FieldDef que representa o campo para obter metadados associados.  
  
 `pClass`  
 [fora] Um ponteiro para um token TypeDef que representa o tipo da classe a que o campo pertence.  
  
 `szField`  
 [fora] O nome do campo.  
  
 `cchField`  
 [em] O tamanho em caracteres largos do buffer para *szField*.  
  
 `pchField`  
 [fora] O tamanho real do buffer devolvido.  
  
 `pdwAttr`  
 [fora] Sinalizadores associados aos metadados do campo.  
  
 `ppvSigBlob`  
 [em] Um ponteiro para o valor binário de metadados que descreve o campo.  
  
 `pcbSigBlob`  
 [fora] O tamanho em bytes de `ppvSigBlob`.  
  
 `pdwCPlusTypeFlag`  
 [fora] Uma bandeira que especifica o tipo de valor do campo.  
  
 `ppValue`  
 [fora] Um valor constante para o campo.  
  
 `pcchValue`  
 [fora] O tamanho em `ppValue`chars de , ou zero se não houver nenhuma corda.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Incluído como um recurso em MsCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
