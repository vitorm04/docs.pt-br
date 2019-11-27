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
ms.openlocfilehash: 1d6d66ea62cbf679f722f830b3638455001aedd6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437494"
---
# <a name="imetadataimportgetmemberrefprops-method"></a>Método IMetaDataImport::GetMemberRefProps
Obtém os metadados associados ao membro referenciado pelo token especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
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
 no O token de MemberRef para o qual retornar metadados associados.  
  
 `ptk`  
 fora Um TypeDef ou TypeRef ou um token TypeSpec que representa a classe que declara o membro ou um token ModuleRef que representa a classe do módulo que declara o membro ou um MethodDef que representa o membro.  
  
 `szMember`  
 fora Um buffer de cadeia de caracteres para o nome do membro.  
  
 `cchMember`  
 no O tamanho solicitado em caracteres largos de `szMember`.  
  
 `pchMember`  
 fora O tamanho retornado em caracteres largos de `szMember`.  
  
 `ppvSibBlob`  
 fora Um ponteiro para a assinatura de metadados binários do membro.  
  
 `pbSig`  
 fora O tamanho em bytes de `ppvSigBlob`.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Incluído como um recurso em MsCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
