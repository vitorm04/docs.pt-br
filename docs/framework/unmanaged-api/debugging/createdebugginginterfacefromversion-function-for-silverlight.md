---
title: Função CreateDebuggingInterfaceFromVersion para Silverlight
ms.date: 03/30/2017
f1_keywords:
- CreateDebuggingInterfaceFromVersion
helpviewer_keywords:
- CreateDebuggingInterfaceFromVersion function
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 35c7a18f-133a-4584-bd25-bb338568b0c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 77164f9d8a1641ba37fa504d09d77ec6aecc3db5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61965802"
---
# <a name="createdebugginginterfacefromversion-function-for-silverlight"></a>Função CreateDebuggingInterfaceFromVersion para Silverlight
Aceita uma cadeia de versão de runtime (CLR) linguagem comum que é retornada a [função CreateVersionStringFromModule](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)e retorna uma interface correspondente do depurador (normalmente, [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  LPCWSTR      szDebuggeeVersion,  
    [out] IUnknown**   ppCordb,  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `szDebuggeeVersion`  
 [in] Cadeia de caracteres de versão do CLR em que o depurador de destino, que é retornado pelo [função CreateVersionStringFromModule](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md).  
  
 `ppCordb`  
 [out] Ponteiro para um ponteiro para um objeto COM (`IUnknown`). Este objeto será convertido para um [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) antes de ser retornado do objeto.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK  
 `ppCordb` referencia um objeto que implementa o [interface ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface.  
  
 E_INVALIDARG  
 Tanto `szDebuggeeVersion` ou `ppCordb` é nulo.  
  
 CORDBG_E_DEBUG_COMPONENT_MISSING  
 Um componente que é necessário para a depuração do CLR não pode ser localizado. Isso significa que o mscordbi ou mscordaccore.dll não foi encontrado no mesmo diretório que o CoreCLR. dll de destino.  
  
 CORDBG_E_INCOMPATIBLE_PROTOCOL  
 Mscordbi ou mscordaccore.dll não é a mesma versão que o CoreCLR. dll de destino.  
  
 E_FAIL (ou outros códigos de retorno e _)  
 Não é possível retornar um [interface ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md).  
  
## <a name="remarks"></a>Comentários  
 A interface que é retornada fornece os recursos para anexar a um CLR em um processo de destino e depurar o código gerenciado que está executando o CLR.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** dbgshim.h  
  
 **Biblioteca:** dbgshim  
  
 **Versões do .NET framework:** 3,5 SP1
