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
ms.openlocfilehash: 73697fdd19f2492aabdc0d76e8c1a27c917c85f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405532"
---
# <a name="iclrdatatargetsetthreadcontext-method"></a>Método ICLRDataTarget::SetThreadContext
Define o contexto atual do thread especificado no processo de destino. Este método é chamado, os serviços de acesso dados common language runtime (CLR).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextSize,  
    [in, size_is(contextSize)]   
         BYTE               *context  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `threadID`  
 [in] O identificador de sistema operacional de um thread no processo de destino.  
  
 `contextSize`  
 [in] O tamanho do contexto.  
  
 `context`  
 [in] Ponteiro para um buffer que contém o contexto.  
  
 Os dados de `context` buffer será no formato do Win32 `CONTEXT` estrutura. O contexto Especifica dados de registro específicos de processador, portanto a definição de Win32 `CONTEXT` estrutura depende da arquitetura do processador. Consulte o arquivo de cabeçalho Winnt. H para a definição do Win32 `CONTEXT` estrutura.  
  
## <a name="remarks"></a>Comentários  
 Este método é implementado pelo autor do aplicativo de depuração.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** ClrData.idl, ClrData.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
