---
title: Método ICorDebugProcess2::GetDesiredNGENCompilerFlags
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetDesiredNGENCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetDesiredNGENCompilerFlags
helpviewer_keywords:
- ICorDebugProcess2::GetDesiredNGENCompilerFlags method [.NET Framework debugging]
- GetDesiredNGENCompilerFlags method [.NET Framework debugging]
ms.assetid: fc834580-3a90-4315-95d2-349b6bb7d059
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a59067f72005e87152680e4f990fc74e4acdaa9b
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57472662"
---
# <a name="icordebugprocess2getdesiredngencompilerflags-method"></a>Método ICorDebugProcess2::GetDesiredNGENCompilerFlags
Obtém o compilador atual configurações de sinalizador de que o common language runtime (CLR) usa para selecionar o pré-compilado correto (ou seja, nativo) a imagem a ser carregado nesse processo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetDesiredNGENCompilerFlags (  
    [out] DWORD   *pdwFlags  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pdwFlags`  
 [out] Um ponteiro para uma combinação bit a bit do [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) valores de enumeração que são usados para selecionar a imagem correta pré-compilado a ser carregado.  
  
## <a name="remarks"></a>Comentários  
 Use o [ICorDebugProcess2::SetDesiredNGENCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setdesiredngencompilerflags-method.md) método para definir os sinalizadores que o CLR será usado para selecionar a imagem correta de pré-compilação compilada para carregar.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
