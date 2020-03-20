---
title: Método IMetaDataDispenserEx::GetOption
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.GetOption
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::GetOption
helpviewer_keywords:
- GetOption method [.NET Framework metadata]
- IMetaDataDispenserEx::GetOption method [.NET Framework metadata]
ms.assetid: d7f794e5-8e25-4d65-850a-7c34fbfce87d
topic_type:
- apiref
ms.openlocfilehash: 816e2f2dc7d4d00f74f67720ee45d7b3483e57fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177727"
---
# <a name="imetadatadispenserexgetoption-method"></a>Método IMetaDataDispenserEx::GetOption
Obtém o valor da opção especificada para o escopo de metadados atual. A opção controla como as chamadas para o escopo de metadados atuais são tratadas.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetOption (  
    [in]  REFGUID         optionId,
    [out] const VARIANT   *pValue  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `optionId`  
 [em] Um ponteiro para um GUID que especifica a opção a ser recuperada. Consulte a seção Observações para obter uma lista de GUIDs suportados.  
  
 `pValue`  
 [fora] O valor da opção devolvida. O tipo deste valor será uma variante do tipo da opção especificada.  
  
## <a name="remarks"></a>Comentários  
 A lista a seguir mostra os GUIDs que são suportados para este método. Para obter descrições, consulte o método [IMetaDataDispenserEx::SetOption.](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md) Se `optionId` não estiver nesta lista, este `E_INVALIDARG`método retorna HRESULT , indicando um parâmetro incorreto.  
  
- MetaDadosVerificandoduplicadosPara  
  
- MetaDataRefToDefCheck  
  
- MetaDataNotificationToKenMovement  
  
- MetaDataSetENC  
  
- MetaDataErrorItItOutOutOfOrder  
  
- MetaDataGeraradaptados DESEGURANÇA  
  
- Opções de MetaDataLinker  
  
## <a name="requirements"></a>Requisitos  
 **Plataforma:** Consulte [os requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como recurso em MsCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IMetaDataDispenserEx](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [Interface IMetaDataDispenser](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
