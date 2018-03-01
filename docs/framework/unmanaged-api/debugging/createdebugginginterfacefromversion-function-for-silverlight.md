---
title: "Função CreateDebuggingInterfaceFromVersion para Silverlight"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CreateDebuggingInterfaceFromVersion
helpviewer_keywords:
- CreateDebuggingInterfaceFromVersion function
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 35c7a18f-133a-4584-bd25-bb338568b0c6
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c38171c5887bb207b3692e9fa92aa2be2bc72a27
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="createdebugginginterfacefromversion-function-for-silverlight"></a>Função CreateDebuggingInterfaceFromVersion para Silverlight
Aceita uma cadeia de versão de tempo de execução (CLR) linguagem comum que é retornada o [função CreateVersionStringFromModule](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)e retorna uma interface de depurador correspondente (normalmente, [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  LPCWSTR      szDebuggeeVersion,  
    [out] IUnknown**   ppCordb,  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `szDebuggeeVersion`  
 [in] Cadeia de caracteres de versão do CLR no depurador de destino, que é retornado pelo [função CreateVersionStringFromModule](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md).  
  
 `ppCordb`  
 [out] Ponteiro para um ponteiro para um objeto COM (`IUnknown`). Esse objeto será convertido em um [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) objeto antes de ser retornado.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK  
 `ppCordb`referencia um objeto que implementa o [interface ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface.  
  
 E_INVALIDARG  
 O `szDebuggeeVersion` ou `ppCordb` é nulo.  
  
 CORDBG_E_DEBUG_COMPONENT_MISSING  
 Um componente necessário para a depuração CLR não pode ser localizado. Isso significa que o mscordbi.dll ou mscordaccore.dll não foi encontrado no mesmo diretório que o destino CoreCLR. dll.  
  
 CORDBG_E_INCOMPATIBLE_PROTOCOL  
 Mscordbi.dll ou mscordaccore.dll não é a mesma versão do CoreCLR. dll de destino.  
  
 E_FAIL (ou outros códigos de retorno E_)  
 Não é possível retornar um [interface ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md).  
  
## <a name="remarks"></a>Comentários  
 A interface que é retornada fornece os recursos para anexar a um CLR em um processo de destino e depurar o código gerenciado que está executando o CLR.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** dbgshim.h  
  
 **Biblioteca:** dbgshim.dll  
  
 **Versões do .NET framework:** 3.5 SP1
