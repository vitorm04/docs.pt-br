---
title: Método ISymUnmanagedWriter::OpenScope
ms.date: 03/30/2017
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
ms.openlocfilehash: 915b05d0d2ac611678fdcc94dd42bbb1962e6ceb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427898"
---
# <a name="isymunmanagedwriteropenscope-method"></a>Método ISymUnmanagedWriter::OpenScope
Abre um novo escopo léxico no método atual. O escopo se torna o novo escopo atual e é enviado por push para uma pilha de escopos. Os escopos devem formar uma hierarquia. Irmãos não têm permissão para se sobrepor.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT OpenScope(  
    [in] ULONG32 startOffset,  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `startOffset`  
 no O deslocamento da primeira instrução no escopo léxico, em bytes, desde o início do método.  
  
 `pRetVal`  
 fora Um ponteiro para um `ULONG32` que recebe o identificador de escopo.  
  
## <a name="return-value"></a>Valor retornado  
 S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="remarks"></a>Comentários  
 `ISymUnmanagedWriter::OpenScope` retorna um identificador de escopo opaco que pode ser usado com [ISymUnmanagedWriter:: SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) para definir o deslocamento de início e término de um escopo em um momento posterior. Nesse caso, os deslocamentos passados para `ISymUnmanagedWriter::OpenScope` e [ISymUnmanagedWriter:: CloseScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) são ignorados. Os identificadores de escopo são válidos somente no método atual.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Cabeçalho:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Consulte também

- [Interface ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
