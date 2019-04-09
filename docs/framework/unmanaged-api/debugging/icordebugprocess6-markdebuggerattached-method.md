---
title: Método ICorDebugProcess6::MarkDebuggerAttached
ms.date: 03/30/2017
ms.assetid: bf94f090-5265-4112-8e57-5b4e20e070d0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 15e2e94ac4e30fbdb375175148a5b448c51821f0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59128018"
---
# <a name="icordebugprocess6markdebuggerattached-method"></a>Método ICorDebugProcess6::MarkDebuggerAttached
Altera o estado interno do depurado para que o método <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> na biblioteca de classes .NET Framework retorne `true`.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT MarkDebuggerAttached(  
    BOOL fIsAttached  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `fIsAttached`  
 `true` Se o <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> método deve indicar que um depurador é anexado; `false` caso contrário.  
  
## <a name="return-value"></a>Valor de retorno  
 O método pode retornar os valores listados na tabela a seguir.  
  
|Valor retornado|Descrição|  
|------------------|-----------------|  
|`S_OK`|A depuração foi atualizada com êxito.|  
|`CORDBG_E_MODULE_NOT_LOADED`|O assembly que contém o método <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> não é carregado, ou outros erros como metadados ausentes estão impedindo que ele seja reconhecido.<br /><br /> Esse erro é comum e benigno. Você deve chamar o método novamente ao carregar assemblies adicionais.|  
|Outros valores `HRESULT` com falha.|Outros valores provavelmente indicam depurador ou componentes do compilador com comportamento inadequado.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
>  Esse método só está disponível com o .NET Native.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorDebugProcess6](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
