---
title: Função CorExitProcess
ms.date: 03/30/2017
api_name:
- CorExitProcess
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CorExitProcess
helpviewer_keywords:
- CorExitProcess function [.NET Framework hosting]
ms.assetid: a5cab4c6-990e-47f3-8798-cf422b791015
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6e1104a98afb32dea687949e9c723124014c1e62
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925312"
---
# <a name="corexitprocess-function"></a>Função CorExitProcess
Desliga o processo atual não gerenciado.  
  
 Essa função foi preterida no .NET Framework 4. Em vez disso, use o método [ICLRMetaHost:: ExitProcess](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md) .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
void STDMETHODCALLTYPE CorExitProcess (   
  int  exitCode  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `exitCode`  
 Um inteiro que especifica o código de saída do processo.  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
> Começando com o .NET Framework 4, `CorExitProcess` sai de cada tempo de execução iniciado no processo, não apenas o tempo de execução ao qual as APIs herdadas foram associadas.  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca** MSCorEE.dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Funções de hospedagem CLR preteridas](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
