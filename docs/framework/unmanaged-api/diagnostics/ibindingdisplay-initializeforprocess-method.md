---
title: Método IBindingDisplay::InitializeForProcess
ms.date: 03/30/2017
api_name:
- IBindingDisplay.InitializeForProcess
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IBindingDisplay::InitializeForProcess
helpviewer_keywords:
- IBindingDisplay::InitializeForProcess method [.NET Framework debugging]
- InitializeForProcess method [.NET Framework debugging]
ms.assetid: 59417acb-4e59-46ad-acfe-d827e6ab6078
topic_type:
- apiref
ms.openlocfilehash: 8645878132359b6218cd62b1ff707208de53704b
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442144"
---
# <a name="ibindingdisplayinitializeforprocess-method"></a>Método IBindingDisplay::InitializeForProcess
Inicializa o objeto [IBindingDisplay](ibindingdisplay-interface.md) .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT InitializeForProcess (  
    [in] ULONG32   pid  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pid`  
 no O identificador do processo.  
  
## <a name="remarks"></a>Comentários  
 O depurador chama o `InitializeForProcess` método no momento da criação para inicializar a exibição da associação. `InitializeForProcess`deve ser chamado no momento da criação antes que qualquer outro método em `IBindingDisplay` seja chamado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** BindingDisplay. h  
  
 **Biblioteca:** BindingDisplay. idl  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IBindingDisplay](ibindingdisplay-interface.md)
