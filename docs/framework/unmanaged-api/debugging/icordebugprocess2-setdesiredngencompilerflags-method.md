---
title: Método ICorDebugProcess2::SetDesiredNGENCompilerFlags
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.SetDesiredNGENCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::SetDesiredNGENCompilerFlags
helpviewer_keywords:
- ICorDebugProcess2::SetDesiredNGENCompilerFlags method [.NET Framework debugging]
- SetDesiredNGENCompilerFlags method [.NET Framework debugging]
ms.assetid: 98320175-7c5e-4dbb-8683-86fa82e2641f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3582ebf2acee02d49aabafb03604c84249c4ce13
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747381"
---
# <a name="icordebugprocess2setdesiredngencompilerflags-method"></a>Método ICorDebugProcess2::SetDesiredNGENCompilerFlags
Define os sinalizadores que devem ser inseridos em uma imagem pré-compilada para que o tempo de execução carregar essa imagem no processo atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetDesiredNGENCompilerFlags (  
    [in] DWORD    pdwFlags  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pdwFlags`  
 [in] Um valor igual a [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeração que especifica os sinalizadores de compilador usado para selecionar a imagem correta de pré-compilada.  
  
## <a name="remarks"></a>Comentários  
 O `SetDesiredNGENCompilerFlags` método Especifica os sinalizadores que devem ser inseridos em uma imagem pré-compilada para que o tempo de execução carregará a imagem nesse processo. Os sinalizadores definidos por esse método são usados somente para selecionar a imagem correta de pré-compilado. Se nenhuma imagem desse tipo existir, o tempo de execução carregará a imagem da Microsoft intermediate language (MSIL) e o compilador just-in-time (JIT) em vez disso. Nesse caso, o depurador ainda deve usar o [ICorDebugModule2::SetJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md) método para definir os sinalizadores conforme desejado para a compilação JIT.  
  
 Se uma imagem é carregada, mas alguns compilação JIT deve ser realizadas para essa imagem (que será o caso se a imagem contém as classes genéricas), os sinalizadores de compilador especificados pelo `SetDesiredNGENCompilerFlags` método aplicará a compilação JIT extra.  
  
 O `SetDesiredNGENCompilerFlags` método deve ser chamado durante a [icordebugmanagedcallback:: CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) retorno de chamada. Tenta chamar o `SetDesiredNGENCompilerFlags` método posteriormente falhará. Além disso, tentativas de definir os sinalizadores que não estão definidos no `CorDebugJITCompilerFlags` são não é válido para o processo especificado ou enumeração falharão.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [Interface ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
