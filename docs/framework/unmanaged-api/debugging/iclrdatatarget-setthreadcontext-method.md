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
ms.openlocfilehash: d76a907434b12b85aaedeef169390ec6f0df724a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179123"
---
# <a name="iclrdatatargetsetthreadcontext-method"></a>Método ICLRDataTarget::SetThreadContext
Define o contexto atual do segmento especificado no processo de destino. Esse método é chamado pelos serviços de acesso a dados do tempo de execução de idioma comum (CLR).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextSize,  
    [in, size_is(contextSize)]
         BYTE               *context  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `threadID`  
 [em] O identificador do sistema operacional de um segmento no processo de destino.  
  
 `contextSize`  
 [em] O tamanho do contexto.  
  
 `context`  
 [em] Ponteiro para um buffer contendo o contexto.  
  
 Os dados `context` no buffer estarão no formato `CONTEXT` da estrutura Win32. O contexto especifica dados de registro específicos do processador, `CONTEXT` de modo que a definição da estrutura Win32 depende da arquitetura do processador. Consulte o arquivo de cabeçalho WinNT.h `CONTEXT` para a definição da estrutura Win32.  
  
## <a name="remarks"></a>Comentários  
 Este método é implementado pelo autor do aplicativo de depuração.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** ClrData.idl, ClrData.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICLRDataTarget](iclrdatatarget-interface.md)
