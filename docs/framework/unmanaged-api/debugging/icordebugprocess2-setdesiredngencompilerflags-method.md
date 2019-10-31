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
ms.openlocfilehash: 9313fc58dec8099f42dbff07685ca14791fa324f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137169"
---
# <a name="icordebugprocess2setdesiredngencompilerflags-method"></a>Método ICorDebugProcess2::SetDesiredNGENCompilerFlags
Define os sinalizadores que devem ser inseridos em uma imagem pré-compilada para que o tempo de execução carregue essa imagem no processo atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetDesiredNGENCompilerFlags (  
    [in] DWORD    pdwFlags  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pdwFlags`  
 no Um valor da enumeração [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) que especifica os sinalizadores de compilador usados para selecionar a imagem previamente compilada correta.  
  
## <a name="remarks"></a>Comentários  
 O método `SetDesiredNGENCompilerFlags` especifica os sinalizadores que devem ser inseridos em uma imagem pré-compilada para que o tempo de execução carregue essa imagem nesse processo. Os sinalizadores definidos por esse método são usados apenas para selecionar a imagem pré-compilada correta. Se essa imagem não existir, o tempo de execução carregará a imagem do Microsoft Intermediate Language (MSIL) e o compilador JIT (just-in-time). Nesse caso, o depurador ainda deve usar o método [ICorDebugModule2:: SetJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md) para definir os sinalizadores conforme desejado para a compilação JIT.  
  
 Se uma imagem for carregada, mas alguma compilação JIT precisar ocorrer para essa imagem (que será o caso se a imagem contiver genéricos), os sinalizadores do compilador especificados pelo método `SetDesiredNGENCompilerFlags` serão aplicados à compilação adicional do JIT.  
  
 O método `SetDesiredNGENCompilerFlags` deve ser chamado durante o retorno de chamada [ICorDebugManagedCallback:: CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) . As tentativas de chamar o método `SetDesiredNGENCompilerFlags` depois falharão. Além disso, as tentativas de definir sinalizadores que não estão definidos na enumeração `CorDebugJITCompilerFlags` ou não são legais para o processo especificado falharão.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [Interface ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
