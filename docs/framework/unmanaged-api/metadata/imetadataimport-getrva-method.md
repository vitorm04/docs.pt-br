---
title: Método IMetaDataImport::GetRVA
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetRVA
helpviewer_keywords:
- GetRVA method [.NET Framework metadata]
- IMetaDataImport::GetRVA method [.NET Framework metadata]
ms.assetid: ea422217-988b-4acd-b2db-c55357938275
topic_type:
- apiref
ms.openlocfilehash: a3a5cadc1b5a9df7967aae271ff10296843121dd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436961"
---
# <a name="imetadataimportgetrva-method"></a>Método IMetaDataImport::GetRVA
Obtém o endereço virtual relativo (RVA) e os sinalizadores de implementação do método ou do campo representado pelo token especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetRVA (  
   [in]  mdToken     tk,   
   [out] ULONG       *pulCodeRVA,   
   [out]  DWORD      *pdwImplFlags  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `tk`  
 no Um token de metadados MethodDef ou FieldDef que representa o objeto de código para o qual retornar o RVA. Se o token for um FieldDef, o campo deverá ser uma variável global.  
  
 `pulCodeRVA`  
 fora Um ponteiro para o endereço virtual relativo do objeto de código representado pelo token.  
  
 `pdwImplFlags`  
 fora Um ponteiro para os sinalizadores de implementação do método. Esse valor é um bitmask da enumeração [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) . O valor de `pdwImplFlags` será válido somente se `tk` for um token MethodDef.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Incluído como um recurso em MsCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
