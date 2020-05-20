---
title: Método IBindingDisplay::GetCurrentDisplay
ms.date: 03/30/2017
api_name:
- IBindingDisplay.GetCurrentDisplay
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IBindingDisplay::GetCurrentDisplay
helpviewer_keywords:
- IBindingDisplay::GetCurrentDisplay method [.NET Framework debugging]
- GetCurrentDisplay method [.NET Framework debugging]
ms.assetid: d28eeea4-c4e0-40d4-91de-198d98cfa13c
topic_type:
- apiref
ms.openlocfilehash: 6fe8c3266a8c9a52cd1022589cd68485c4326fd1
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442183"
---
# <a name="ibindingdisplaygetcurrentdisplay-method"></a>Método IBindingDisplay::GetCurrentDisplay
Retorna as informações de exibição da Associação atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetCurrentDisplay (  
    [out, retval] SAFEARRAY(struct BindingDisplayTabControl) *display  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `display`  
 [out, retval] Um ponteiro para um SafeArray que contém as informações de exibição de associação.  
  
## <a name="remarks"></a>Comentários  
 O método [IBindingDisplay:: InitializeForProcess](ibindingdisplay-initializeforprocess-method.md) deve ter êxito anteriormente e o programa deve ser interrompido por um depurador.  
  
 O chamador deve desalocar a `SAFEARRAY` memória retornada usando [SafeArrayDestroy](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy).  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** BindingDisplay. h  
  
 **Biblioteca:** BindingDisplay. idl  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IBindingDisplay](ibindingdisplay-interface.md)
- [Método InitializeForProcess](ibindingdisplay-initializeforprocess-method.md)
