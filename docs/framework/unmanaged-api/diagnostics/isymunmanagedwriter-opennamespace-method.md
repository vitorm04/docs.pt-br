---
title: Método ISymUnmanagedWriter::OpenNamespace
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.OpenNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::OpenNamespace
helpviewer_keywords:
- ISymUnmanagedWriter::OpenNamespace method [.NET Framework debugging]
- OpenNamespace method [.NET Framework debugging]
ms.assetid: 426f4e4f-e60d-4ad1-b546-a10e3c55c283
topic_type:
- apiref
ms.openlocfilehash: ab248c6a624fbed1a6783383566be093c449ff97
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609879"
---
# <a name="isymunmanagedwriteropennamespace-method"></a>Método ISymUnmanagedWriter::OpenNamespace
Abre um novo namespace. Chame esse método antes de definir métodos ou variáveis que ocupem um namespace. Os namespaces podem ser aninhados.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT OpenNamespace(  
    [in] const WCHAR *name);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `name`  
 no Um ponteiro para o nome do novo namespace.  
  
## <a name="return-value"></a>Valor retornado  
 S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Confira também

- [Interface ISymUnmanagedWriter](isymunmanagedwriter-interface.md)
- [Método CloseNamespace](isymunmanagedwriter-closenamespace-method.md)
