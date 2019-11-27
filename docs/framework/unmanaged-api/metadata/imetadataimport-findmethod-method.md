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
ms.openlocfilehash: 470b6511366cef1680eaf97f9ab376736add55c4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437888"
---
# <a name="imetadataimportfindmethod-method"></a>Método IMetaDataImport::FindMethod
Obtém um ponteiro para o token MethodDef do método que está incluído pelo <xref:System.Type> especificado e que tem o nome especificado e a assinatura de metadados.  
  
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
  
## <a name="parameters"></a>Parâmetros  
 `td`  
 no O token de `mdTypeDef` para o tipo (uma classe ou interface) que inclui o membro a ser pesquisado. Se esse valor for `mdTokenNil`, a pesquisa será feita para uma função global.  
  
 `szName`  
 no O nome do método a ser pesquisado.  
  
 `pvSigBlob`  
 no Um ponteiro para a assinatura de metadados binários do método.  
  
 `cbSigBlob`  
 no O tamanho em bytes de `pvSigBlob`.  
  
 `pmb`  
 fora Um ponteiro para o token MethodDef correspondente.  
  
## <a name="remarks"></a>Comentários  
 Você especifica o método usando sua classe ou interface (`td`) de circunscrição, seu nome (`szName`) e, opcionalmente, sua assinatura (`pvSigBlob`). Pode haver vários métodos com o mesmo nome em uma classe ou interface. Nesse caso, passe a assinatura do método para localizar a correspondência exclusiva.  
  
 A assinatura passada para `FindMethod` deve ter sido gerada no escopo atual, porque as assinaturas estão associadas a um escopo específico. Uma assinatura pode inserir um token que identifica a classe de circunscrição ou o tipo de valor. O token é um índice na tabela de TypeDef local. Você não pode criar uma assinatura de tempo de execução fora do contexto do escopo atual e usar essa assinatura como entrada para entrada no `FindMethod`.  
  
 `FindMethod` localiza apenas os métodos que foram definidos diretamente na classe ou na interface; Ele não encontra os métodos herdados.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Incluído como um recurso em MsCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Reflection.MethodInfo>
- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
