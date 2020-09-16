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
ms.openlocfilehash: db2474741012c4fd1734adafed112821c42c099c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90541702"
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
  
 O chamador deve desalocar a `SAFEARRAY` memória retornada usando [SafeArrayDestroy](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy).  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** BindingDisplay. h  
  
 **Biblioteca:** BindingDisplay. idl  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IBindingDisplay](ibindingdisplay-interface.md)
- [Método InitializeForProcess](ibindingdisplay-initializeforprocess-method.md)
