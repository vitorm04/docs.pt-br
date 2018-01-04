---
title: "Método ICorDebugProcess2::SetDesiredNGENCompilerFlags"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess2.SetDesiredNGENCompilerFlags
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess2::SetDesiredNGENCompilerFlags
helpviewer_keywords:
- ICorDebugProcess2::SetDesiredNGENCompilerFlags method [.NET Framework debugging]
- SetDesiredNGENCompilerFlags method [.NET Framework debugging]
ms.assetid: 98320175-7c5e-4dbb-8683-86fa82e2641f
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f8c5ac4fab96ac7ec3a2b086dbc34763dde08dc2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess2setdesiredngencompilerflags-method"></a>Método ICorDebugProcess2::SetDesiredNGENCompilerFlags
Define os sinalizadores que devem ser inseridos em uma imagem pré-compilado em ordem para o tempo de execução carregar a imagem no processo atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetDesiredNGENCompilerFlags (  
    [in] DWORD    pdwFlags  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pdwFlags`  
 [in] Um valor de [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeração que especifica os sinalizadores de compilador usada para selecionar a imagem correta de pré-compilada.  
  
## <a name="remarks"></a>Comentários  
 O `SetDesiredNGENCompilerFlags` método Especifica os sinalizadores que devem ser inseridos em uma imagem pré-compilado, para que o tempo de execução será carregado se a imagem nesse processo. Os sinalizadores definidos por esse método são usados apenas para selecionar a imagem pré-compilado correta. Se essa imagem não existir, o tempo de execução carregará a imagem do Microsoft intermediate language (MSIL) e o compilador just-in-time (JIT) em vez disso. Nesse caso, o depurador ainda deve usar o [Icordebugmodule2](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md) método para definir os sinalizadores conforme desejado para a compilação JIT.  
  
 Se uma imagem é carregada, mas alguns compilação JIT deve ser realizadas para essa imagem (que será o caso se a imagem contém genéricos), os sinalizadores de compilador especificados pelo `SetDesiredNGENCompilerFlags` método aplicará a compilação JIT extra.  
  
 O `SetDesiredNGENCompilerFlags` método deve ser chamado durante a [Icordebugmanagedcallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) retorno de chamada. Tentativas de chamar o `SetDesiredNGENCompilerFlags` método posteriormente falhará. Além disso, as tentativas de definir os sinalizadores que não estão definidos no `CorDebugJITCompilerFlags` enumeração ou são ilegal para determinado processo falhará.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [Interface ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
