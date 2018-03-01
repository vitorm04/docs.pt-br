---
title: "Função CreateCordbObject"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7007e541e9999e0cb14a83845eb28d71336b3ff6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="createcordbobject-function"></a>Função CreateCordbObject
Cria uma interface do depurador ([ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)) que fornece funcionalidade para criar uma instância de uma sessão de depuração gerenciada em um processo remoto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT CordbCreateObject (  
       [in]  int         iDebuggerVersion,   
       [out] IUnknown**  ppCordb  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `iDebuggerVersion`  
 [in] Versão do depurador do processo de destino. Esse parâmetro deve ser CorDebugVersion_2_0 para depuração remota.  
  
 `ppCordb`  
 [out] Ponteiro para um ponteiro para um objeto que será convertido em um [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface e retornado.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK  
 O número de CLRs no processo com êxito foi determinado e o identificador correspondente e matrizes de caminho foram preenchidos corretamente.  
  
 E_INVALIDARG  
 `ppCordb`é nulo, ou `iDebuggerVersion` não é CorDebugVersion_2_0.  
  
 E_OUTOFMEMORY  
 Não é possível alocar memória suficiente para`ppCordb`  
  
 E_FAIL (ou outros códigos de retorno E_)  
 Outras falhas.  
  
## <a name="remarks"></a>Comentários  
 O [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface é retornada no `ppCordb` é a interface de depuração de nível superior para todos os serviços de depuração de gerenciados.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CoreClrRemoteDebuggingInterfaces.h  
  
 **Biblioteca:** mscordbi_macx86.dll  
  
 **Versões do .NET framework:** 3.5 SP1
