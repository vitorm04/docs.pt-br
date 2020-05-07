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
ms.openlocfilehash: 2271611b5cbbfe487e5798be0429ed94c227a67f
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860875"
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
  
## <a name="return-value"></a>Valor retornado  
 S_OK  
 O número de CLRs no processo foi determinado com êxito e as matrizes de identificador e caminho correspondentes foram preenchidas corretamente.  
  
 E_OUTOFMEMORY  
 Não é possível alocar memória `ppTarget`suficiente para.  
  
 E_FAIL (ou outros códigos de retorno de E_)  
 Outras falhas.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CoreClrRemoteDebuggingInterfaces. h  
  
 **Biblioteca:** mscordbi_macx86. dll  
  
 **Versões do .NET Framework:** 3,5 SP1
