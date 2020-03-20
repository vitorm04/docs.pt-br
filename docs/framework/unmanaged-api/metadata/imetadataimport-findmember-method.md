---
title: Método IMetaDataImport::FindMember
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMember
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMember
helpviewer_keywords:
- IMetaDataImport::FindMember method [.NET Framework metadata]
- FindMember method [.NET Framework metadata]
ms.assetid: ad32fb84-c2b6-41cd-888d-787ff3a90449
topic_type:
- apiref
ms.openlocfilehash: dab155b82d87609b3d3f390133e6490502a43518
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177275"
---
# <a name="imetadataimportfindmember-method"></a>Método IMetaDataImport::FindMember
Obtém um ponteiro para o token MemberDef para campo <xref:System.Type> ou método que está incluído no especificado e que tem o nome especificado e a assinatura de metadados.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT FindMember (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,
   [in]  PCCOR_SIGNATURE   pvSigBlob,
   [in]  ULONG             cbSigBlob,
   [out] mdToken           *pmb  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `td`  
 [em] O token TypeDef para a classe ou interface que inclui o membro para procurar. Se esse `mdTokenNil`valor for, a pesquisa é feita para uma função global variável ou global.  
  
 `szName`  
 [em] O nome do membro para procurar.  
  
 `pvSigBlob`  
 [em] Um ponteiro para a assinatura binária de metadados do membro.  
  
 `cbSigBlob`  
 [em] O tamanho em bytes de `pvSigBlob`.  
  
 `pmb`  
 [fora] Um ponteiro para o token MemberDef correspondente.  
  
## <a name="remarks"></a>Comentários  
 Você especifica o membro usando sua`td`classe ou`szName`interface de fechamento (`pvSigBlob`), seu nome ( ), e opcionalmente sua assinatura ( ). Pode haver vários membros com o mesmo nome em uma classe ou interface. Nesse caso, passe a assinatura do membro para encontrar a correspondência única.  
  
 A assinatura `FindMember` passada deve ter sido gerada no escopo atual, porque as assinaturas estão vinculadas a um escopo específico. Uma assinatura pode incorporar um token que identifica a classe de fechamento ou o tipo de valor. O token é um índice na tabela typeDef local. Não é possível construir uma assinatura de tempo de execução fora do `FindMember`contexto do escopo atual e usar essa assinatura como entrada para entrada em .  
  
 `FindMember`encontra apenas membros que foram definidos diretamente na classe ou interface; não encontra membros herdados.  
  
> [!NOTE]
> `FindMember`é um método auxiliar. Ele chama [IMetaDataImport::FindMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); se essa chamada não encontrar `FindMember` uma correspondência, então chama [IMetaDataImport::FindField](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Incluído como um recurso em MsCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
