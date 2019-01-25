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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 057dd7c25821aedddeee57a31200cf35c6df1273
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498509"
---
# <a name="imetadataimportfindmemberref-method"></a>Método IMetaDataImport::FindMemberRef
Obtém um ponteiro para o token MemberRef para o membro de referência que é delimitada por especificado <xref:System.Type> e que tenha a assinatura de nome e os metadados especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT FindMemberRef (  
   [in]  mdTypeRef          td,  
   [in]  LPCWSTR            szName,   
   [in]  PCCOR_SIGNATURE    pvSigBlob,   
   [in]  ULONG              cbSigBlob,   
   [out] mdMemberRef        *pmr  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `td`  
 [in] O token TypeRef para a classe ou interface que inclui a referência de membro a ser pesquisado. Se esse valor for `mdTokenNil`, a pesquisa é feita para uma variável global ou uma referência de função global.  
  
 `szName`  
 [in] O nome da referência de membro a ser pesquisado.  
  
 `pvSigBlob`  
 [in] Um ponteiro para a assinatura binária metadados da referência de membro.  
  
 `cbSigBlob`  
 [in] O tamanho em bytes do `pvSigBlob`.  
  
 `pmr`  
 [out] Um ponteiro para o token MemberRef correspondente.  
  
## <a name="remarks"></a>Comentários  
 Você especifica o membro usando a sua classe delimitadora ou interface (`td`), seu nome (`szName`) e, opcionalmente, sua assinatura (`pvSigBlob`).  
  
 A assinatura é passada para `FindMemberRef` devem ter sido gerados no escopo atual, porque as assinaturas são associadas a um determinado escopo. Uma assinatura pode inserir um token que identifica o tipo de valor ou classe delimitador. O token é um índice na tabela TypeDef local. Você não pode criar uma assinatura de tempo de execução fora do contexto do escopo atual e usar essa assinatura como entrada para `FindMemberRef`.  
  
 `FindMemberRef` localiza apenas as referências de membro que foram definidas diretamente na classe ou interface; ele não encontra referências do membro herdado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
