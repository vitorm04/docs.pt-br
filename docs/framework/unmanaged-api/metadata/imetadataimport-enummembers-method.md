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
ms.openlocfilehash: 50035799fcfa4c4b08404d63fe91e7dba85722fa
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758837"
---
# <a name="imetadataimportenummembers-method"></a>Método IMetaDataImport::EnumMembers
Enumera os tokens de MemberDef que representa os membros do tipo especificado.  
  
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
  
## <a name="parameters"></a>Parâmetros  
 `phEnum`  
 [no, out] Um ponteiro para o enumerador.  
  
 `cl`  
 [in] Um token de TypeDef que representa o tipo cujos membros são a serem enumerados.  
  
 `rMembers`  
 [out] A matriz usada para manter os tokens de MemberDef.  
  
 `cMax`  
 [in] O tamanho máximo da `rMembers` matriz.  
  
 `pcTokens`  
 [out] O número real de tokens MemberDef retornado no `rMembers`.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|`S_OK`|`EnumMembers` retornado com êxito.|  
|`S_FALSE`|Não há nenhum token MemberDef para enumerar. Nesse caso, `pcTokens` é zero.|  
  
## <a name="remarks"></a>Comentários  
 Quando enumerando coleções de membros de uma classe `EnumMembers` retorna somente os membros (campos e métodos, mas **não** propriedades ou eventos) definidos diretamente na classe. Ele não retorna todos os membros que herda a classe, mesmo se a classe fornece uma implementação para esses membros herdados. Para enumerar os membros herdados, o chamador deve movimentar explicitamente a cadeia de herança. Observe que as regras para a cadeia de herança podem variar dependendo do idioma ou o compilador que se emitiu os metadados originais.
 
 Propriedades e eventos não são enumerados pelo `EnumMembers`. Para enumerar os, use [EnumProperties](imetadataimport-enumproperties-method.md) ou [EnumEvents](imetadataimport-enumevents-method.md).
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
