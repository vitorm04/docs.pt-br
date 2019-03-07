---
title: Função CreateCoreClrDebugTarget
ms.date: 03/30/2017
api_name:
- CreateCorClrDebugTarget
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CreateCoreClrDebugTarget
helpviewer_keywords:
- remote debugging API [Silverlight]
- Silverlight, remote debugging
- CreateCoreClrDebugTarget function
ms.assetid: 1cf4ca8e-d9bb-4633-9adf-5e24315bf87a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 48ce5381c745669b813f5b28d801add7daba7825
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57470042"
---
# <a name="createcoreclrdebugtarget-function"></a>Função CreateCoreClrDebugTarget
Cria uma conexão a um proxy de depurador que está em execução em um computador remoto e retorna um [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) objeto que pode ser usado para consultar os processos em execução e tempos de execução carregados no computador remoto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT CreateCoreClrDebugTarget (  
       [in]  DWORD    dwAddress,   
       [out] ICoreClrDebugTarget**     ppTarget  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `dwAddress`  
 [in] Endereço IPv4 de uma máquina de destino remoto.  
  
 `ppTarget`  
 [out] Ponteiro para um ponteiro para um [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) objeto será criado.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK  
 O número de CLRs no processo com êxito foi determinado e o identificador correspondente e matrizes de caminho foram preenchidos corretamente.  
  
 E_OUTOFMEMORY  
 Não é possível alocar memória suficiente para `ppTarget`.  
  
 E_FAIL (ou outros códigos de retorno e _)  
 Outras falhas.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CoreClrRemoteDebuggingInterfaces.h  
  
 **Biblioteca:** mscordbi_macx86.dll  
  
 **Versões do .NET framework:** 3,5 SP1
