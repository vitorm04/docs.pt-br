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
ms.openlocfilehash: a7fed8cb70785f0ccfcadf1e16181db303ac98e0
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789190"
---
# <a name="createcoreclrdebugtarget-function"></a>Função CreateCoreClrDebugTarget
Cria uma conexão com um proxy de depurador que está sendo executado em um computador remoto e retorna um objeto [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) que pode ser usado para consultar processos em execução e os tempos de execução carregados no computador remoto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CreateCoreClrDebugTarget (  
       [in]  DWORD    dwAddress,   
       [out] ICoreClrDebugTarget**     ppTarget  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `dwAddress`  
 no Endereço IPv4 de um computador de destino remoto.  
  
 `ppTarget`  
 fora Ponteiro para um ponteiro para um objeto [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) que será criado.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK  
 O número de CLRs no processo foi determinado com êxito e as matrizes de identificador e caminho correspondentes foram preenchidas corretamente.  
  
 {1&gt;E_OUTOFMEMORY&lt;1}  
 Não é possível alocar memória suficiente para `ppTarget`.  
  
 E_FAIL (ou outros códigos de retorno de E_)  
 Outras falhas.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CoreClrRemoteDebuggingInterfaces. h  
  
 **Biblioteca:** mscordbi_macx86. dll  
  
 **Versões do .NET Framework:** 3,5 SP1
