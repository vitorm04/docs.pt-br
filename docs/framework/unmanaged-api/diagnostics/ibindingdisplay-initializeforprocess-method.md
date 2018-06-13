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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8954c2f6ecaf2767dd01b0601096d9e3f6df9b98
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425448"
---
# <a name="ibindingdisplayinitializeforprocess-method"></a>Método IBindingDisplay::InitializeForProcess
Inicializa o [IBindingDisplay](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md) objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT InitializeForProcess (  
    [in] ULONG32   pid  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pid`  
 [in] O identificador de processo.  
  
## <a name="remarks"></a>Comentários  
 As chamadas do depurador de `InitializeForProcess` método no momento da criação para inicializar a exibição de associação. `InitializeForProcess` deve ser chamado no momento da criação antes de qualquer outro método em `IBindingDisplay` é chamado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** BindingDisplay.h  
  
 **Biblioteca:** BindingDisplay.idl  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IBindingDisplay](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)
