---
title: Método IMetaDataImport::EnumMembers
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMembers
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMembers
helpviewer_keywords:
- IMetaDataImport::EnumMembers method [.NET Framework metadata]
- EnumMembers method [.NET Framework metadata]
ms.assetid: 3fb8e178-342b-4c89-9bcf-f7f834e6cb77
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 46ee8c62861a62ac044f295f7da082756d87347b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataimportenummembers-method"></a>Método IMetaDataImport::EnumMembers
Enumera os tokens de MemberDef que representa os membros do tipo especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT EnumMembers (   
   [in, out]  HCORENUM    *phEnum,   
   [in]  mdTypeDef   cl,   
   [out] mdToken     rMembers[],   
   [in]  ULONG       cMax,   
   [out] ULONG       *pcTokens  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `phEnum`  
 [out no] Um ponteiro para o enumerador.  
  
 `cl`  
 [in] Um token de TypeDef que representa o tipo cujos membros são a serem enumerados.  
  
 `rMembers`  
 [out] A matriz usada para manter os tokens de MemberDef.  
  
 `cMax`  
 [in] O tamanho máximo da `rMembers` matriz.  
  
 `pcTokens`  
 [out] O número real de tokens MemberDef retornado em `rMembers`.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|`S_OK`|`EnumMembers` retornou com êxito.|  
|`S_FALSE`|Não há nenhum token MemberDef enumerar. Nesse caso, `pcTokens` é zero.|  
  
## <a name="remarks"></a>Comentários  
 Quando enumerando coleções de membros de uma classe, `EnumMembers` retorna somente os membros definidos diretamente na classe. Ele não retorna todos os membros de classe herdada, mesmo se a classe fornece uma implementação para esses membros herdados. Para enumerar os membros herdados, o chamador deve percorrer explicitamente a cadeia de herança. Observe que as regras para a cadeia de herança podem variar dependendo do idioma ou o compilador que emitiu os metadados originais.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
