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
ms.openlocfilehash: a61254ba751e47b0089a3f7528aca337a32e2db3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175363"
---
# <a name="imetadataimportgetmemberrefprops-method"></a>Método IMetaDataImport::GetMemberRefProps
Obtém metadados associados ao membro referenciado pelo token especificado.  
  
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
  
## <a name="parameters"></a>parâmetros  
 `mr`  
 [em] O token MemberRef para retornar metadados associados para.  
  
 `ptk`  
 [fora] Um tipoDef ou TypeRef, ou token TypeSpec que representa a classe que declara o membro, ou um token ModuleRef que representa a classe de módulo que declara o membro, ou um MethodDef que representa o membro.  
  
 `szMember`  
 [fora] Um buffer de cordas para o nome do membro.  
  
 `cchMember`  
 [em] O tamanho solicitado em `szMember`caracteres amplos de .  
  
 `pchMember`  
 [fora] O tamanho retornado em `szMember`caracteres largos de .  
  
 `ppvSibBlob`  
 [fora] Um ponteiro para a assinatura binária de metadados para o membro.  
  
 `pbSig`  
 [fora] O tamanho em bytes de `ppvSigBlob`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Incluído como um recurso em MsCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
