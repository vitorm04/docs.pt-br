---
title: Método ICLRDataTarget::SetThreadContext
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.SetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::SetThreadContext
helpviewer_keywords:
- SetThreadContext method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::SetThreadContext method [.NET Framework debugging]
ms.assetid: 103c8502-81fe-40d7-9c1e-9008d8fb19e1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: edd70dd4cfc2e26b30ee0deec79b7d126d1f76a1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738594"
---
# <a name="iclrdatatargetsetthreadcontext-method"></a>Método ICLRDataTarget::SetThreadContext
Define o contexto atual do thread especificado no processo de destino. Esse método é chamado pelo serviço de acesso de dados do common language runtime (CLR).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextSize,  
    [in, size_is(contextSize)]   
         BYTE               *context  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `threadID`  
 [in] O identificador de sistema operacional de um thread no processo de destino.  
  
 `contextSize`  
 [in] O tamanho do contexto.  
  
 `context`  
 [in] Ponteiro para um buffer que contém o contexto.  
  
 Os dados do `context` buffer será no formato de Win32 `CONTEXT` estrutura. O contexto Especifica dados de registro específicas do processador, portanto, a definição do Win32 `CONTEXT` estrutura depende da arquitetura do processador. Consulte o arquivo de cabeçalho de Winnt. H a definição de Win32 `CONTEXT` estrutura.  
  
## <a name="remarks"></a>Comentários  
 Este método é implementado pelo autor do aplicativo de depuração.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** ClrData.idl, ClrData.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
