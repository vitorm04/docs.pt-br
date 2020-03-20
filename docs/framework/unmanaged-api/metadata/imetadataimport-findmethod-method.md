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
ms.openlocfilehash: 53b3d94e8b1e273fcbc041d25a5bf586a12735c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177260"
---
# <a name="imetadataimportfindmethod-method"></a>Método IMetaDataImport::FindMethod
Obtém um ponteiro para o token MethodDef para o <xref:System.Type> método que é incluído pelo especificado e que tem o nome especificado e a assinatura de metadados.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT FindMethod (  
   [in]  mdTypeDef          td,  
   [in]  LPCWSTR            szName,
   [in]  PCCOR_SIGNATURE    pvSigBlob,
   [in]  ULONG              cbSigBlob,
   [out] mdMethodDef        *pmb  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `td`  
 [em] O `mdTypeDef` token para o tipo (uma classe ou interface) que inclui o membro para procurar. Se esse `mdTokenNil`valor for, então a pesquisa é feita para uma função global.  
  
 `szName`  
 [em] O nome do método para procurar.  
  
 `pvSigBlob`  
 [em] Um ponteiro para a assinatura binária de metadados do método.  
  
 `cbSigBlob`  
 [em] O tamanho em bytes de `pvSigBlob`.  
  
 `pmb`  
 [fora] Um ponteiro para o token MethodDef correspondente.  
  
## <a name="remarks"></a>Comentários  
 Você especifica o método usando sua`td`classe de`szName`fechamento ou interface (`pvSigBlob`), seu nome ( ), e opcionalmente sua assinatura ( ). Pode haver vários métodos com o mesmo nome em uma classe ou interface. Nesse caso, passe a assinatura do método para encontrar a correspondência única.  
  
 A assinatura `FindMethod` passada deve ter sido gerada no escopo atual, porque as assinaturas estão vinculadas a um escopo específico. Uma assinatura pode incorporar um token que identifica a classe de fechamento ou o tipo de valor. O token é um índice na tabela typeDef local. Não é possível construir uma assinatura de tempo de execução fora do `FindMethod`contexto do escopo atual e usar essa assinatura como entrada para entrada em .  
  
 `FindMethod`encontra apenas métodos que foram definidos diretamente na classe ou interface; não encontra métodos herdados.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Incluído como um recurso em MsCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- <xref:System.Reflection.MethodInfo>
- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
