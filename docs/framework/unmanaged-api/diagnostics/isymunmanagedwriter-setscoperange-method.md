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
ms.openlocfilehash: b404a187d8628a04d2aa51df15f86fcc9d0b14f8
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427852"
---
# <a name="isymunmanagedwritersetscoperange-method"></a>Método ISymUnmanagedWriter::SetScopeRange
Define o intervalo de deslocamento do escopo léxico especificado. O escopo se torna o novo escopo atual e é enviado por push para uma pilha de escopos. Os escopos devem formar uma hierarquia. Irmãos não têm permissão para se sobrepor.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT OpenScope(  
    [in] ULONG32  scopeID,  
    [in] ULONG32  startOffset,  
    [in] ULONG32  endOffset);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `scopeId`  
 no O identificador de escopo para o escopo.  
  
 `startOffset`  
 no O deslocamento, em bytes, da primeira instrução no escopo léxico a partir do início do método.  
  
 `endOffset`  
 no O deslocamento, em bytes, da última instrução no escopo léxico desde o início do método.  
  
## <a name="return-value"></a>Valor retornado  
 S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="remarks"></a>Comentários  
 [ISymUnmanagedWriter:: OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) retorna um identificador de escopo opaco que pode ser usado com `ISymUnmanagedWriter::SetScopeRange` para definir o deslocamento inicial e final de um escopo em um momento posterior. Nesse caso, os deslocamentos passados para `ISymUnmanagedWriter::OpenScope` e [ISymUnmanagedWriter:: CloseScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) são ignorados. Os identificadores de escopo só são válidos no método atual.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Cabeçalho:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Consulte também

- [Interface ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
