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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2ab86277956469e558d20cea81174a7fdcc0020b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739330"
---
# <a name="createcordbobject-function"></a>Função CreateCordbObject
Cria uma interface do depurador ([ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)) que fornece funcionalidade para instanciar uma sessão de depuração gerenciada em um processo remoto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CordbCreateObject (  
       [in]  int         iDebuggerVersion,   
       [out] IUnknown**  ppCordb  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `iDebuggerVersion`  
 [in] Versão do depurador do processo de destino. Esse parâmetro deve ser CorDebugVersion_2_0 para depuração remota.  
  
 `ppCordb`  
 [out] Ponteiro para um ponteiro para um objeto que será convertido em um [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) de interface e retornado.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK  
 O número de CLRs no processo com êxito foi determinado e o identificador correspondente e matrizes de caminho foram preenchidos corretamente.  
  
 E_INVALIDARG  
 `ppCordb` é nulo, ou `iDebuggerVersion` não é CorDebugVersion_2_0.  
  
 E_OUTOFMEMORY  
 Não é possível alocar memória suficiente para `ppCordb`  
  
 E_FAIL (ou outros códigos de retorno e _)  
 Outras falhas.  
  
## <a name="remarks"></a>Comentários  
 O [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface que é retornado no `ppCordb` é a interface de depuração de nível superior para todos os gerenciados serviços de depuração.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CoreClrRemoteDebuggingInterfaces.h  
  
 **Biblioteca:** mscordbi_macx86.dll  
  
 **Versões do .NET framework:** 3,5 SP1
