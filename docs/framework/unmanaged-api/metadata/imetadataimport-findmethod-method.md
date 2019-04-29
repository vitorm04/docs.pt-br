---
title: Método IMetaDataImport::FindMethod
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMethod
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMethod
helpviewer_keywords:
- FindMethod method [.NET Framework metadata]
- IMetaDataImport::FindMethod method [.NET Framework metadata]
ms.assetid: 0f9bde1d-e306-438d-941b-d0925b322304
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 28aa8313e7ba0c071187d0f1f6d78431b16fc005
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777865"
---
# <a name="imetadataimportfindmethod-method"></a>Método IMetaDataImport::FindMethod
Obtém um ponteiro para o MethodDef token para o método que é incluído por especificado <xref:System.Type> e que tenha a assinatura de nome e os metadados especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT FindMethod (  
   [in]  mdTypeDef          td,  
   [in]  LPCWSTR            szName,   
   [in]  PCCOR_SIGNATURE    pvSigBlob,   
   [in]  ULONG              cbSigBlob,   
   [out] mdMethodDef        *pmb  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `td`  
 [in] O `mdTypeDef` token para o tipo (uma classe ou interface) que inclui o membro a ser pesquisado. Se esse valor for `mdTokenNil`, em seguida, a pesquisa é feita para uma função global.  
  
 `szName`  
 [in] O nome do método a ser pesquisado.  
  
 `pvSigBlob`  
 [in] Um ponteiro para a assinatura de metadados de binários do método.  
  
 `cbSigBlob`  
 [in] O tamanho em bytes do `pvSigBlob`.  
  
 `pmb`  
 [out] Um ponteiro para o token MethodDef correspondente.  
  
## <a name="remarks"></a>Comentários  
 Especificar o método usando a sua classe delimitadora ou interface (`td`), seu nome (`szName`) e, opcionalmente, sua assinatura (`pvSigBlob`). Pode haver vários métodos com o mesmo nome em uma classe ou interface. Nesse caso, passe a assinatura do método para encontrar a correspondência exclusiva.  
  
 A assinatura é passada para `FindMethod` devem ter sido gerados no escopo atual, porque as assinaturas são associadas a um determinado escopo. Uma assinatura pode inserir um token que identifica o tipo de valor ou classe delimitador. O token é um índice na tabela TypeDef local. Você não pode criar uma assinatura de tempo de execução fora do contexto do escopo atual e use essa assinatura como entrada para cada entrada `FindMethod`.  
  
 `FindMethod` localiza apenas os métodos que foram definidos diretamente na classe ou interface; ele não localizará os métodos herdados.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Reflection.MethodInfo>
- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
