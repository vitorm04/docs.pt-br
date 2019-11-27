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
ms.openlocfilehash: bb796a12868cc3e44394ab493f7838dc48ab4dc5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448488"
---
# <a name="ibindingdisplayinitializeforprocess-method"></a>Método IBindingDisplay::InitializeForProcess
Inicializa o objeto [IBindingDisplay](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md) .  
  
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
 O depurador chama o método `InitializeForProcess` no momento da criação para inicializar a exibição de associação. `InitializeForProcess` deve ser chamado no momento da criação antes que qualquer outro método em `IBindingDisplay` seja chamado.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** BindingDisplay. h  
  
 **Biblioteca:** BindingDisplay. idl  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IBindingDisplay](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)
