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
ms.openlocfilehash: 2716adcc8c79c8003202561ea2011c2469a6bc5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179230"
---
# <a name="createcordbobject-function"></a>Função CreateCordbObject
Cria uma interface de depurador[(ICorDebug)](icordebug-interface.md)que fornece funcionalidade para instanciar uma sessão de depuração gerenciada em um processo remoto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CordbCreateObject (  
       [in]  int         iDebuggerVersion,
       [out] IUnknown**  ppCordb  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `iDebuggerVersion`  
 [em] Versão dedepurador do processo de destino. Este parâmetro deve ser CorDebugVersion_2_0 para depuração remota.  
  
 `ppCordb`  
 [fora] Ponteiro para um ponteiro para um objeto que será lançado para uma interface [ICorDebug](icordebug-interface.md) e retornado.  
  
## <a name="return-value"></a>Valor retornado  
 S_OK  
 O número de CLRs no processo foi determinado com sucesso, e as matrizes de cabo e caminho correspondentes foram devidamente preenchidas.  
  
 E_INVALIDARG  
 `ppCordb`é nulo, ou `iDebuggerVersion` não é CorDebugVersion_2_0.  
  
 E_OUTOFMEMORY  
 Incapaz de alocar memória suficiente para`ppCordb`  
  
 E_FAIL (ou outros códigos de retorno E_)  
 Outras falhas.  
  
## <a name="remarks"></a>Comentários  
 A interface [ICorDebug](icordebug-interface.md) que `ppCordb` é retornada é a interface de depuração de nível superior para todos os serviços gerenciados de depuração.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CoreClrRemoteDebuggingInterfaces.h  
  
 **Biblioteca:** mscordbi_macx86.dll  
  
 **.NET Framework Versões:** 3.5 SP1
