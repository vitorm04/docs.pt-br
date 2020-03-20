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
ms.openlocfilehash: 3777ad4b12c7d0593c095c470aba81088137a859
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179177"
---
# <a name="iclrdatatargetgetthreadcontext-method"></a>Método ICLRDataTarget::GetThreadContext
Obtém o contexto de execução atual para o segmento dado no processo de destino. Esse método é chamado pelos serviços comuns de acesso a dados em tempo de execução do idioma.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextFlags,  
    [in] ULONG32            contextSize,  
    [out, size_is(contextSize)]
        BYTE                *context  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `threadID`  
 [em] O identificador do sistema operacional de um segmento no processo de destino.  
  
 `contextFlags`  
 [em] Sinalizadores que especificam quais partes do contexto retornar. A implementação retornará pelo menos essas partes do contexto.  
  
 `contextSize`  
 [em] O tamanho do contexto.  
  
 `context`  
 [fora] Ponteiro para um buffer no qual colocar o contexto.  
  
 Os dados `context` no buffer devem estar no formato `CONTEXT` da estrutura Win32. O contexto especifica dados de registro específicos do processador, `CONTEXT` de modo que a definição da estrutura Win32 depende da arquitetura do processador. Consulte o arquivo de cabeçalho WinNT.h `CONTEXT` para a definição da estrutura Win32.  
  
## <a name="remarks"></a>Comentários  
 Este método é implementado pelo autor do aplicativo de depuração.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** ClrData.idl, ClrData.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICLRDataTarget](iclrdatatarget-interface.md)
