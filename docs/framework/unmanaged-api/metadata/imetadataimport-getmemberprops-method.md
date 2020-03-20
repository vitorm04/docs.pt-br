---
title: Método IMetaDataImport::GetMemberProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMemberProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMemberProps
helpviewer_keywords:
- IMetaDataImport::GetMemberProps method [.NET Framework metadata]
- GetMemberProps method [.NET Framework metadata]
ms.assetid: 42790918-4142-4938-b8f4-a56979a55846
topic_type:
- apiref
ms.openlocfilehash: 72e14ea0414ebdeb8f54a4bdef8ce5208fc8ef72
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177226"
---
# <a name="imetadataimportgetmemberprops-method"></a>Método IMetaDataImport::GetMemberProps
Obtém informações armazenadas nos metadados para uma definição de membro especificada, incluindo <xref:System.Type> o nome, assinatura binária e endereço virtual relativo, do membro referenciado pelo token de metadados especificado. Este é um método simples de ajuda: se *mb* é um MethodDef, então **GetMethodProps** é chamado; se *mb* é um FieldDef, então **GetFieldProps** é chamado. Veja esses outros métodos para obter detalhes.
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetMemberProps (  
   [in]  mdToken           mb,
   [out] mdTypeDef         *pClass,  
   [out] LPWSTR            szMember,
   [in]  ULONG             cchMember,
   [out] ULONG             *pchMember,
   [out] DWORD             *pdwAttr,  
   [out] PCCOR_SIGNATURE   *ppvSigBlob,
   [out] ULONG             *pcbSigBlob,
   [out] ULONG             *pulCodeRVA,
   [out] DWORD             *pdwImplFlags,
   [out] DWORD             *pdwCPlusTypeFlag,
   [out] UVCP_CONSTANT     *ppValue,  
   [out] ULONG             *pcchValue  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `mb`  
 [em] O token que faz referência ao membro para obter os metadados associados.  
  
 `pClass`  
 [fora] Um ponteiro para o token de metadados que representa a classe do membro.  
  
 `szMember`  
 [fora] O nome do membro.  
  
 `cchMember`  
 [em] O tamanho em caracteres largos do `szMember` buffer.  
  
 `pchMember`  
 [fora] O tamanho em caracteres largos do nome retornado.  
  
 `pdwAttr`  
 [fora] Quaisquer valores de bandeira aplicados ao membro.  
  
 `ppvSigBlob`  
 [fora] Um ponteiro para a assinatura binária de metadados do membro.  
  
 `pcbSigBlob`  
 [fora] O tamanho em bytes de `ppvSigBlob`.  
  
 `pulCodeRVA`  
 [fora] Um ponteiro para o endereço virtual relativo do membro.  
  
 `pdwImplFlags`  
 [fora] Qualquer método de implementação sinaliza associados ao membro.  
  
 `pdwCPlusTypeFlag`  
 [fora] Uma bandeira que <xref:System.ValueType>marca um. É um dos `ELEMENT_TYPE_*` valores.
  
 `ppValue`  
 [fora] Um valor de seqüência constante devolvido por este membro.  
  
 `pcchValue`  
 [fora] O tamanho em `ppValue`caracteres `ppValue` de , ou zero se não segurar uma seqüência.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Incluído como um recurso em MsCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
