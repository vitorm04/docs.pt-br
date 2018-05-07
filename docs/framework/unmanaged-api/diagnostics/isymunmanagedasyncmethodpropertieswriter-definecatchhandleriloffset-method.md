---
title: Método ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset
ms.date: 03/30/2017
ms.assetid: 92af7896-2201-408d-8b1b-23e28001eeac
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce462c4e7e9c8fb11ee74a91f3ece2465a44a834
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinecatchhandleriloffset-method"></a>Método ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset
Define o deslocamento para o manipulador catch gerado pelo compilador que encapsula um método assíncrono de IL.  
  
 O deslocamento de IL de catch gerado é usado pelo depurador para tratar o problema como se fosse código não-usuário, mesmo que isso pode ocorrer em um método de código do usuário. Em particular, ele é usado em resposta a um **CatchHandlerFound** eventos de exceção.  
  
## <a name="syntax"></a>Sintaxe  
  
```idl  
HRESULT DefineCatchHandlerILOffset(    [in] ULONG32 catchHandlerOffset);  
```  
  
#### <a name="parameters"></a>Parâmetros  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`catchHandlerOffset`||  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna `HRESULT`.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface ISymUnmanagedAsyncMethodPropertiesWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
