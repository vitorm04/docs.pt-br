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
ms.openlocfilehash: 20c7a90f27defa18a5ef311d1f3a549b81fc5c40
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175480"
---
# <a name="imetadataimportenummembers-method"></a>Método IMetaDataImport::EnumMembers
Enumera os tokens MemberDef representando membros do tipo especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT EnumMembers (
   [in, out]  HCORENUM    *phEnum,
   [in]  mdTypeDef   cl,
   [out] mdToken     rMembers[],
   [in]  ULONG       cMax,
   [out] ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `phEnum`  
 [dentro, fora] Um ponteiro para o enumerador.  
  
 `cl`  
 [em] Um token TypeDef representando o tipo cujos membros devem ser enumerados.  
  
 `rMembers`  
 [fora] A matriz usada para conter os tokens MemberDef.  
  
 `cMax`  
 [em] O tamanho máximo `rMembers` da matriz.  
  
 `pcTokens`  
 [fora] O número real de tokens MemberDef retornou em `rMembers`.  
  
## <a name="return-value"></a>Valor retornado  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|`S_OK`|`EnumMembers`retornou com sucesso.|  
|`S_FALSE`|Não há tokens MemberDef para enumerar. Nesse caso, `pcTokens` é zero.|  
  
## <a name="remarks"></a>Comentários  
 Ao enumerar coleções de membros `EnumMembers` para uma classe, retorna apenas membros (campos e métodos, mas **não** propriedades ou eventos) definidos diretamente na classe. Não devolve nenhum membro que a classe herde, mesmo que a classe forneça uma implementação para os membros herdados. Para enumerar os membros herdados, o interlocutor deve andar explicitamente na cadeia de herança. Observe que as regras para a cadeia de herança podem variar dependendo do idioma ou compilador que emitia os metadados originais.

 Propriedades e eventos não são `EnumMembers`enumerados por . Para enumerar esses, use [EnumProperties](imetadataimport-enumproperties-method.md) ou [EnumEvents](imetadataimport-enumevents-method.md).
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Incluído como um recurso em MsCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
