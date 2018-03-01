---
title: "Método IMetaDataImport::FindMember"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a20930688aed210309a719de2c7187f1f5fd1f24
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportfindmember-method"></a>Método IMetaDataImport::FindMember
Obtém um ponteiro para o MemberDef token para o campo ou método que é incluído por especificado <xref:System.Type> e que tem a assinatura de nome e os metadados especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT FindMember (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,   
   [in]  PCCOR_SIGNATURE   pvSigBlob,   
   [in]  ULONG             cbSigBlob,   
   [out] mdToken           *pmb  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `td`  
 [in] O token de TypeDef para a classe ou interface que inclui o membro a ser pesquisado. Se esse valor for `mdTokenNil`, a pesquisa é feita para uma variável global ou a função global.  
  
 `szName`  
 [in] O nome do membro a ser pesquisado.  
  
 `pvSigBlob`  
 [in] Um ponteiro para a assinatura de binários de metadados do membro.  
  
 `cbSigBlob`  
 [in] O tamanho em bytes do `pvSigBlob`.  
  
 `pmb`  
 [out] Um ponteiro para o token MemberDef correspondente.  
  
## <a name="remarks"></a>Comentários  
 Especifique o membro usando sua classe ou interface de delimitador (`td`), seu nome (`szName`) e, opcionalmente, sua assinatura (`pvSigBlob`). Pode haver vários membros com o mesmo nome em uma classe ou interface. Nesse caso, passe a assinatura do membro para encontrar a correspondência exclusiva.  
  
 A assinatura é passado para `FindMember` deve foram gerados no escopo atual, porque as assinaturas associadas a um determinado escopo. Uma assinatura pode inserir um token que identifica o tipo de valor ou classe delimitador. O token é um índice na tabela de TypeDef local. Você não pode criar uma assinatura de tempo de execução fora do contexto do escopo atual e use essa assinatura como entrada para cada entrada `FindMember`.  
  
 `FindMember`localiza apenas os membros que foram definidos diretamente na classe ou interface. membros herdados não for encontrada.  
  
> [!NOTE]
>  `FindMember`é um método auxiliar. Ele chama [: Findmethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); se essa chamada não encontrar uma correspondência, `FindMember` , em seguida, chama [: Findfield](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
