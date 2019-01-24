---
title: Método ISymUnmanagedWriter::SetScopeRange
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetScopeRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetScopeRange
helpviewer_keywords:
- SetScopeRange method [.NET Framework debugging]
- ISymUnmanagedWriter::SetScopeRange method [.NET Framework debugging]
ms.assetid: d4d98676-444b-46ca-bfe6-0d827385cd22
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: da50542d9f57e008b31ce2e6ed9698df1275d5eb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54618799"
---
# <a name="isymunmanagedwritersetscoperange-method"></a>Método ISymUnmanagedWriter::SetScopeRange
Define o intervalo de deslocamento do escopo léxico especificado. O escopo se torna o novo escopo atual e é enviada por push para uma pilha de escopos. Escopos devem formar uma hierarquia. Irmãos não podem se sobrepor.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT OpenScope(  
    [in] ULONG32  scopeID,  
    [in] ULONG32  startOffset,  
    [in] ULONG32  endOffset);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `scopeId`  
 [in] O identificador de escopo para o escopo.  
  
 `startOffset`  
 [in] O deslocamento, em bytes, da primeira instrução no escopo léxico desde o início do método.  
  
 `endOffset`  
 [in] O deslocamento, em bytes, da última instrução no escopo léxico desde o início do método.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="remarks"></a>Comentários  
 [Isymunmanagedwriter:: Openscope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) retorna um identificador de escopo opaco que pode ser usado com `ISymUnmanagedWriter::SetScopeRange` definir um escopo inicial e final deslocamento em um momento posterior. Nesse caso, os deslocamentos passados para `ISymUnmanagedWriter::OpenScope` e [isymunmanagedwriter:: Closescope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) são ignorados. Identificadores de escopo só são válidos no método atual.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também
- [Interface ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
