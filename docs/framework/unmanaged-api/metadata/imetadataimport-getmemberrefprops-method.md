---
title: Método IMetaDataImport::GetMemberRefProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMemberRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMemberRefProps
helpviewer_keywords:
- GetMemberRefProps method [.NET Framework metadata]
- IMetaDataImport::GetMemberRefProps method [.NET Framework metadata]
ms.assetid: 0ea73055-ece0-4151-a094-414c88ef8941
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a2c431abb7a4a872454b9c2689ee195ed36ef236
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59177002"
---
# <a name="imetadataimportgetmemberrefprops-method"></a>Método IMetaDataImport::GetMemberRefProps
Obtém os metadados associados ao membro referenciado pelo token especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetMemberRefProps (  
   [in]  mdMemberRef       mr,   
   [out] mdToken           *ptk,   
   [out] LPWSTR            szMember,   
   [in]  ULONG             cchMember,   
   [out] ULONG             *pchMember,   
   [out] PCCOR_SIGNATURE   *ppvSigBlob,   
   [out] ULONG             *pbSig   
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `mr`  
 [in] O token de MemberRef para retornar os metadados associados para.  
  
 `ptk`  
 [out] Um token de TypeDef ou TypeRef ou TypeSpec que representa a classe que declara o membro ou um token de ModuleRef que representa a classe de módulo que declara o membro ou um MethodDef que representa o membro.  
  
 `szMember`  
 [out] Um buffer de cadeia de caracteres para o nome do membro.  
  
 `cchMember`  
 [in] O tamanho solicitado em caracteres largos da `szMember`.  
  
 `pchMember`  
 [out] O tamanho retornado em caracteres largos da `szMember`.  
  
 `ppvSibBlob`  
 [out] Um ponteiro para a assinatura de metadados de binários para o membro.  
  
 `pbSig`  
 [out] O tamanho em bytes do `ppvSigBlob`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
