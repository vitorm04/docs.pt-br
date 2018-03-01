---
title: "Método ISymUnmanagedWriter::OpenScope"
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
- ISymUnmanagedWriter.OpenScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::OpenScope
helpviewer_keywords:
- OpenScope method, ISymUnmanagedWriter interface [.NET Framework debugging]
- ISymUnmanagedWriter::OpenScope method [.NET Framework debugging]
ms.assetid: dbea0644-3873-4329-90b8-624163e87467
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 99919a1d932bca1bb8677fd71c447c7098c7d44c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriteropenscope-method"></a>Método ISymUnmanagedWriter::OpenScope
Abre um novo escopo léxico no método atual. O escopo se torna o novo escopo atual e é enviada por push para uma pilha de escopos. Escopos devem formar uma hierarquia. Irmãos não podem se sobrepor.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT OpenScope(  
    [in] ULONG32 startOffset,  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `startOffset`  
 [in] O deslocamento da primeira instrução no escopo léxico, em bytes, do início do método.  
  
 `pRetVal`  
 [out] Um ponteiro para um `ULONG32` que recebe o identificador de escopo.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="remarks"></a>Comentários  
 `ISymUnmanagedWriter::OpenScope`Retorna um identificador de escopo opaco que pode ser usado com [: Setscoperange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) definir um escopo inicial e final deslocamento mais tarde. Nesse caso, os deslocamentos passado para `ISymUnmanagedWriter::OpenScope` e [: Closescope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) são ignorados. Identificadores de escopo são válidos somente no método atual.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
