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
ms.openlocfilehash: 340d2de09562ea9b767203a7fa839cdc6b729b3b
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860897"
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
  
## <a name="return-value"></a>Valor retornado  
 S_OK  
 O número de CLRs no processo foi determinado com êxito e as matrizes de identificador e caminho correspondentes foram preenchidas corretamente.  
  
 E_INVALIDARG  
 `ppCordb`é nulo ou `iDebuggerVersion` não é CorDebugVersion_2_0.  
  
 E_OUTOFMEMORY  
 Não é possível alocar memória suficiente para`ppCordb`  
  
 E_FAIL (ou outros códigos de retorno de E_)  
 Outras falhas.  
  
## <a name="remarks"></a>Comentários  
 A interface [ICorDebug](icordebug-interface.md) que é retornada no `ppCordb` é a interface de depuração de nível superior para todos os serviços de depuração gerenciados.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CoreClrRemoteDebuggingInterfaces. h  
  
 **Biblioteca:** mscordbi_macx86. dll  
  
 **Versões do .NET Framework:** 3,5 SP1
