---
title: Interface ISymUnmanagedAsyncMethodPropertiesWriter
ms.date: 03/30/2017
ms.assetid: caa71820-8058-4b6a-93a2-25ee757d92d3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ec66e0064a8d6e8d4664dd8c727aa87621cfd8e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427301"
---
# <a name="isymunmanagedasyncmethodpropertieswriter-interface"></a>Interface ISymUnmanagedAsyncMethodPropertiesWriter
Permite que você defina informações do método assíncrono opcional para o símbolo de cada método. Sempre use um método aberto; ou seja, entre as chamadas para o [método OpenMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md) e [método CloseMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```idl  
[object,uuid(FC073774-1739-4232-BD56-A027294BEC15),pointer_default(unique)]interface ISymUnmanagedAsyncMethodPropertiesWriter : IUnknown  
```  
  
## <a name="methods"></a>Métodos  
 Essa interface contém os seguintes métodos:  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método DefineAsyncStepInfo](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)|Definir um grupo de async await operações no método atual.<br /><br /> Cada deslocamento yield corresponde a instrução de retorno de uma espera, identificando um rendimento potencial. Cada `breakpointMethod` / `breakpointOffset` par identifica onde continuará a operação assíncrona; pode estar em um método diferente.|  
|[Método DefineCatchHandlerILOffset](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)|Define o deslocamento para o manipulador catch gerado pelo compilador que encapsula um método assíncrono de IL.<br /><br /> O deslocamento de IL de catch gerado é usado pelo depurador para tratar catch como se fosse o código não-usuário, mesmo que isso pode ocorrer em um método de código do usuário. Em particular, ele é usado em resposta a um **CatchHandlerFound** eventos de exceção.|  
|[Método DefineKickoffMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)|Define o método inicial que inicia a operação assíncrona.|  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces do repositório de símbolos de diagnóstico](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
