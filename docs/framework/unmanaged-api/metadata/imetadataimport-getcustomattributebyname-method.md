---
title: Método IMetaDataImport::GetCustomAttributeByName
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetCustomAttributeByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetCustomAttributeByName
helpviewer_keywords:
- IMetaDataImport::GetCustomAttributeByName method [.NET Framework metadata]
- GetCustomAttributeByName method [.NET Framework metadata]
ms.assetid: 909aa530-2e3b-4d0a-a38a-a2750e535d7d
topic_type:
- apiref
ms.openlocfilehash: bd7ba7ff10918e5953ea8ae89a60af3115af48a3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437690"
---
# <a name="imetadataimportgetcustomattributebyname-method"></a>Método IMetaDataImport::GetCustomAttributeByName
Obtém o atributo personalizado, dado seu nome e proprietário.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetCustomAttributeByName (  
   [in]  mdToken          tkObj,  
   [in]  LPCWSTR          szName,  
   [out] const void       **ppData,  
   [out] ULONG            *pcbData  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `tkObj`  
 no Um token de metadados que representa o objeto que possui o atributo personalizado.  
  
 `szName`  
 no O nome do atributo personalizado.  
  
 `ppData`  
 fora Um ponteiro para uma matriz de dados que é o valor do atributo personalizado.  
  
 `pcbData`  
 fora O tamanho em bytes dos dados retornados em *`ppData`.  
  
## <a name="remarks"></a>Comentários  
 É legal definir vários atributos personalizados para o mesmo proprietário; Eles podem até mesmo ter o mesmo nome. No entanto, `GetCustomAttributeByName` retorna apenas uma instância. (`GetCustomAttributeByName` retorna a primeira instância que ele encontra.) Para localizar todas as instâncias de um atributo personalizado, chame o método [IMetaDataImport:: EnumCustomAttributes](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumcustomattributes-method.md) .  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Incluído como um recurso em MsCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
