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
ms.openlocfilehash: d93763da2afbbdb1e738c802ba172e9f16e5f7af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataimportgetmemberprops-method"></a>Método IMetaDataImport::GetMemberProps
Obtém informações de metadados, incluindo o nome, a assinatura binária e o endereço virtual relativo, do <xref:System.Type> membro referenciado pelo token de metadados especificado.  
  
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
 [in] O token que referencia o membro para obter os metadados associados.  
  
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
 [out] Um ponteiro para a assinatura de binários de metadados do membro.  
  
 `pcbSigBlob`  
 [out] O tamanho em bytes do `ppvSigBlob`.  
  
 `pulCodeRVA`  
 [out] Um ponteiro para o endereço virtual relativo do membro.  
  
 `pdwImplFlags`  
 [out] Os sinalizadores de implementação do método associados ao membro.  
  
 `pdwCPlusTypeFlag`  
 [out] Um sinalizador que marca um <xref:System.ValueType>.  
  
 `ppValue`  
 [out] Um valor de constante de cadeia de caracteres retornado por este membro.  
  
 `pcchValue`  
 [out] O tamanho em caracteres do `ppValue`, ou zero se `ppValue` não tem uma cadeia de caracteres.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
