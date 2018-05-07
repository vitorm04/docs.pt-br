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
ms.openlocfilehash: a957eb6907b55fe948d696a6a25076c3950f7381
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="createcoreclrdebugtarget-function"></a>Função CreateCoreClrDebugTarget
Cria uma conexão a um proxy do depurador que está sendo executado em um computador remoto e retorna um [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) objeto que pode ser usado para consultar os processos em execução e os tempos de execução carregados no computador remoto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT CreateCoreClrDebugTarget (  
       [in]  DWORD    dwAddress,   
       [out] ICoreClrDebugTarget**     ppTarget  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwAddress`  
 [in] Endereço IPv4 de um computador de destino remoto.  
  
 `ppTarget`  
 [out] Ponteiro para um ponteiro para um [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) objeto será criado.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK  
 O número de CLRs no processo com êxito foi determinado e o identificador correspondente e matrizes de caminho foram preenchidos corretamente.  
  
 E_OUTOFMEMORY  
 Não é possível alocar memória suficiente para `ppTarget`.  
  
 E_FAIL (ou outros códigos de retorno E_)  
 Outras falhas.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CoreClrRemoteDebuggingInterfaces.h  
  
 **Biblioteca:** mscordbi_macx86.dll  
  
 **Versões do .NET framework:** 3.5 SP1
