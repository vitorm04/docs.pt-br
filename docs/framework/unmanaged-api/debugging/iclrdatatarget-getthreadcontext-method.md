---
title: Método ICLRDataTarget::GetThreadContext
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetThreadContext
helpviewer_keywords:
- ICLRDataTarget::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICLRDataTarget interface [.NET Framework debugging]
ms.assetid: b9d8c3b5-3a2e-4225-95d4-dd052c4532c3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c2e1dc374a5205c774e4470363b38c604fa0862
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57500493"
---
# <a name="iclrdatatargetgetthreadcontext-method"></a>Método ICLRDataTarget::GetThreadContext
Obtém o contexto de execução atual para o determinado thread no processo de destino. Esse método é chamado pelo serviço de acesso de dados do common language runtime.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextFlags,  
    [in] ULONG32            contextSize,  
    [out, size_is(contextSize)]   
        BYTE                *context  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `threadID`  
 [in] O identificador de sistema operacional de um thread no processo de destino.  
  
 `contextFlags`  
 [in] Sinalizadores que especificam quais partes do contexto para retornar. A implementação retornará ao menos estas partes do contexto.  
  
 `contextSize`  
 [in] O tamanho do contexto.  
  
 `context`  
 [out] Ponteiro para um buffer no qual colocar o contexto.  
  
 Os dados do `context` buffer deve estar no formato do Win32 `CONTEXT` estrutura. O contexto Especifica dados de registro específicas do processador, portanto, a definição do Win32 `CONTEXT` estrutura depende da arquitetura do processador. Consulte o arquivo de cabeçalho de Winnt. H a definição de Win32 `CONTEXT` estrutura.  
  
## <a name="remarks"></a>Comentários  
 Este método é implementado pelo autor do aplicativo de depuração.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** ClrData.idl, ClrData.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
