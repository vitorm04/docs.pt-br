---
title: Método IMetaDataImport::FindField
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindField
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindField
helpviewer_keywords:
- IMetaDataImport::FindField method [.NET Framework metadata]
- FindField method [.NET Framework metadata]
ms.assetid: 38cd4e16-fbb2-471c-aa73-ac51a1931ad2
topic_type:
- apiref
ms.openlocfilehash: 842d6c0deb90bc45cb59454fb30fcc3544d742f1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437946"
---
# <a name="imetadataimportfindfield-method"></a>Método IMetaDataImport::FindField
Obtém um ponteiro para o token FieldDef do campo que está incluído no <xref:System.Type> especificado e que tem o nome especificado e a assinatura de metadados.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT FindField (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,  
   [in]  PCCOR_SIGNATURE   pvSigBlob,  
   [in]  ULONG             cbSigBlob,  
   [out] mdFieldDef        *pmb  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `td`  
 no O token de TypeDef para a classe ou interface que inclui o campo a ser pesquisado. Se esse valor for `mdTokenNil`, a pesquisa será feita para uma variável global.  
  
 `szName`  
 no O nome do campo a ser pesquisado.  
  
 `pvSigBlob`  
 no Um ponteiro para a assinatura de metadados binários do campo.  
  
 `cbSigBlob`  
 no O tamanho em bytes de `pvSigBlob`.  
  
 `pmb`  
 fora Um ponteiro para o token FieldDef correspondente.  
  
## <a name="remarks"></a>Comentários  
 Você especifica o campo usando sua classe ou interface (`td`) de delimitador, seu nome (`szName`) e, opcionalmente, sua assinatura (`pvSigBlob`).  
  
 A assinatura passada para `FindField` deve ter sido gerada no escopo atual, porque as assinaturas estão associadas a um escopo específico. Uma assinatura pode inserir um token que identifica a classe de circunscrição ou o tipo de valor. (O token é um índice na tabela de TypeDef local). Você não pode criar uma assinatura de tempo de execução fora do contexto do escopo atual e usar essa assinatura como entrada para `FindField`.  
  
 `FindField` localiza apenas os campos que foram definidos diretamente na classe ou na interface; Ele não localiza campos herdados.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Incluído como um recurso em MsCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
