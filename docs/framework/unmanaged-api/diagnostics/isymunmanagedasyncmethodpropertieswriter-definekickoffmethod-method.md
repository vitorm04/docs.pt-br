---
title: Método ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod
ms.date: 03/30/2017
ms.assetid: 4662f70d-817b-4374-8da8-e0545585939f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a476d92486d7f2523dfbcc8b25e9c11e26c55f2d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinekickoffmethod-method"></a>Método ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod
Define o método inicial que inicia a operação assíncrona.  
  
## <a name="syntax"></a>Sintaxe  
  
```idl  
HRESULT DefineKickoffMethod(    [in] mdToken kickoffMethod);  
```  
  
#### <a name="parameters"></a>Parâmetros  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna `HRESULT`.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface ISymUnmanagedAsyncMethodPropertiesWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
