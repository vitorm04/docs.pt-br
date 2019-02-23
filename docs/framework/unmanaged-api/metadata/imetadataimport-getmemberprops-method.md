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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 40631a15bd07b5aa54488e5d3b99cee751e2e0bd
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/23/2019
ms.locfileid: "56748330"
---
# <a name="imetadataimportgetmemberprops-method"></a>Método IMetaDataImport::GetMemberProps
Obtém as informações armazenadas nos metadados para uma definição de membro especificado, incluindo o nome, a assinatura binária e o endereço virtual relativo, da <xref:System.Type> membro referenciado pelo token de metadados especificado. Esse é um método auxiliar simples: se *mb* é um MethodDef, então **GetMethodProps** é chamado; se *mb* é um FieldDef, em seguida, **GetFieldProps** é chamado. Consulte estes outros métodos para obter detalhes. 
  
## <a name="syntax"></a>Sintaxe  
  
```  
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
  
#### <a name="parameters"></a>Parâmetros  
 `mb`  
 [in] O token que referencia o membro para obter os metadados associados para.  
  
 `pClass`  
 [out] Um ponteiro para o token de metadados que representa a classe do membro.  
  
 `szMember`  
 [out] O nome do membro.  
  
 `cchMember`  
 [in] O tamanho em caracteres largos do `szMember` buffer.  
  
 `pchMember`  
 [out] O tamanho em caracteres largos do nome retornado.  
  
 `pdwAttr`  
 [out] Quaisquer valores de sinalizador aplicados ao membro.  
  
 `ppvSigBlob`  
 [out] Um ponteiro para a assinatura binária metadados do membro.  
  
 `pcbSigBlob`  
 [out] O tamanho em bytes do `ppvSigBlob`.  
  
 `pulCodeRVA`  
 [out] Um ponteiro para o endereço virtual relativo do membro.  
  
 `pdwImplFlags`  
 [out] Os sinalizadores de implementação do método associados ao membro.  
  
 `pdwCPlusTypeFlag`  
 [out] Um sinalizador que marca um <xref:System.ValueType>. Ele é um do `ELEMENT_TYPE_*` valores.
  
 `ppValue`  
 [out] Um valor de cadeia de caracteres constante retornado por este membro.  
  
 `pcchValue`  
 [out] O tamanho em caracteres de `ppValue`, ou zero se `ppValue` não mantém uma cadeia de caracteres.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
