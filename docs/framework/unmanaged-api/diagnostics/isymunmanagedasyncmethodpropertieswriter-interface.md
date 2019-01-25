---
title: Interface ISymUnmanagedAsyncMethodPropertiesWriter
ms.date: 03/30/2017
ms.assetid: caa71820-8058-4b6a-93a2-25ee757d92d3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d83270d0e7f5dabff8402f5f81dae20d4457d147
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54604219"
---
# <a name="isymunmanagedasyncmethodpropertieswriter-interface"></a>Interface ISymUnmanagedAsyncMethodPropertiesWriter
Permite que você definir informações de método assíncrono opcional para cada símbolo de método. Sempre use com um método aberto; ou seja, entre as chamadas para o [método OpenMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md) e o [método CloseMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```idl  
[object,uuid(FC073774-1739-4232-BD56-A027294BEC15),pointer_default(unique)]interface ISymUnmanagedAsyncMethodPropertiesWriter : IUnknown  
```  
  
## <a name="methods"></a>Métodos  
 Essa interface contém os seguintes métodos:  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método DefineAsyncStepInfo](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)|Definir um grupo de async await operações no método atual.<br /><br /> Cada deslocamento yield corresponde à instrução de retorno de uma expressão await, identificando um potencial yield. Cada `breakpointMethod` / `breakpointOffset` par identifica onde retomará a operação assíncrona; ele pode estar em um método diferente.|  
|[Método DefineCatchHandlerILOffset](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)|Define o deslocamento para o manipulador catch gerado pelo compilador que encapsula um método assíncrono de IL.<br /><br /> O deslocamento de IL de catch gerado é usado pelo depurador para tratar o problema como se fosse o código de não usuário, mesmo que ele pode ocorrer em um método de código do usuário. Em particular, ele é usado em resposta a um **CatchHandlerFound** eventos de exceção.|  
|[Método DefineKickoffMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)|Define o método inicial que inicia a operação assíncrona.|  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também
- [Interfaces do repositório de símbolos de diagnóstico](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
