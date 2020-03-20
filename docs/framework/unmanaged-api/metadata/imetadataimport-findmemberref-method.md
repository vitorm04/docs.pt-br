---
title: Método IMetaDataImport::FindMemberRef
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMemberRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMemberRef
helpviewer_keywords:
- IMetaDataImport::FindMemberRef method [.NET Framework metadata]
- FindMemberRef method [.NET Framework metadata]
ms.assetid: 1ccda329-d752-4d89-abe8-511af3c3f4c9
topic_type:
- apiref
ms.openlocfilehash: d8b8bfd0e70e75c702f32555c10f433a1ff4ae10
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175415"
---
# <a name="imetadataimportfindmemberref-method"></a>Método IMetaDataImport::FindMemberRef
Obtém um ponteiro para o token MemberRef para a <xref:System.Type> referência de membro que está incluído no especificado e que tem o nome especificado e a assinatura de metadados.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT FindMemberRef (  
   [in]  mdTypeRef          td,  
   [in]  LPCWSTR            szName,
   [in]  PCCOR_SIGNATURE    pvSigBlob,
   [in]  ULONG              cbSigBlob,
   [out] mdMemberRef        *pmr  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `td`  
 [em] O token TypeRef para a classe ou interface que inclui a referência do membro à pesquisa. Se esse `mdTokenNil`valor for, a pesquisa é feita para uma variável global ou uma referência de função global.  
  
 `szName`  
 [em] O nome da referência do membro para procurar.  
  
 `pvSigBlob`  
 [em] Um ponteiro para a assinatura binária de metadados da referência do membro.  
  
 `cbSigBlob`  
 [em] O tamanho em bytes de `pvSigBlob`.  
  
 `pmr`  
 [fora] Um ponteiro para o token MemberRef correspondente.  
  
## <a name="remarks"></a>Comentários  
 Você especifica o membro usando sua`td`classe ou`szName`interface de fechamento (`pvSigBlob`), seu nome ( ), e opcionalmente sua assinatura ( ).  
  
 A assinatura `FindMemberRef` passada deve ter sido gerada no escopo atual, porque as assinaturas estão vinculadas a um escopo específico. Uma assinatura pode incorporar um token que identifica a classe de fechamento ou o tipo de valor. O token é um índice na tabela typeDef local. Não é possível construir uma assinatura de tempo de execução fora `FindMemberRef`do contexto do escopo atual e usar essa assinatura como entrada para .  
  
 `FindMemberRef`encontra apenas referências de membros que foram definidas diretamente na classe ou interface; não encontra referências de membros herdados.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Incluído como um recurso em MsCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
