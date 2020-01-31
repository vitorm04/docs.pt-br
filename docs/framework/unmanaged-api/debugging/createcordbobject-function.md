---
title: Função CreateCordbObject
ms.date: 03/30/2017
api_name:
- CreateCoredbObject
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CreateCordbObject
helpviewer_keywords:
- remote debugging API [Silverlight]
- CreateCordbObject function
- Silverlight, remote debugging
ms.assetid: b259821d-4fa7-464d-85cf-304dfffc8089
topic_type:
- apiref
ms.openlocfilehash: 1d190c5b558c7c523be09267e59eab7c5611563a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793852"
---
# <a name="createcordbobject-function"></a>Função CreateCordbObject
Cria uma interface do depurador ([ICorDebug](icordebug-interface.md)) que fornece funcionalidade para instanciar uma sessão de depuração gerenciada em um processo remoto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CordbCreateObject (  
       [in]  int         iDebuggerVersion,   
       [out] IUnknown**  ppCordb  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `iDebuggerVersion`  
 no Versão do depurador do processo de destino. Esse parâmetro deve ser CorDebugVersion_2_0 para depuração remota.  
  
 `ppCordb`  
 fora Ponteiro para um ponteiro para um objeto que será convertido em uma interface [ICorDebug](icordebug-interface.md) e retornado.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK  
 O número de CLRs no processo foi determinado com êxito e as matrizes de identificador e caminho correspondentes foram preenchidas corretamente.  
  
 {1&gt;E_INVALIDARG&lt;1}  
 `ppCordb` é nulo ou `iDebuggerVersion` não está CorDebugVersion_2_0.  
  
 {1&gt;E_OUTOFMEMORY&lt;1}  
 Não é possível alocar memória suficiente para `ppCordb`  
  
 E_FAIL (ou outros códigos de retorno de E_)  
 Outras falhas.  
  
## <a name="remarks"></a>Comentários  
 A interface [ICorDebug](icordebug-interface.md) retornada em `ppCordb` é a interface de depuração de nível superior para todos os serviços de depuração gerenciados.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CoreClrRemoteDebuggingInterfaces. h  
  
 **Biblioteca:** mscordbi_macx86. dll  
  
 **Versões do .NET Framework:** 3,5 SP1
