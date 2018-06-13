---
title: Método ISymUnmanagedWriter::UsingNamespace
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.UsingNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::UsingNamespace
helpviewer_keywords:
- UsingNamespace method [.NET Framework debugging]
- ISymUnmanagedWriter::UsingNamespace method [.NET Framework debugging]
ms.assetid: 8d746e0a-d158-4983-88da-db0a0856bc0b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9a5ff52a95fd6ebaec05439cbc702d5513d0cc78
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427763"
---
# <a name="isymunmanagedwriterusingnamespace-method"></a>Método ISymUnmanagedWriter::UsingNamespace
Especifica que o nome totalmente qualificado de namespace fornecido está sendo usado dentro do escopo léxico aberto no momento. O namespace será usado em todos os escopos que herdam do escopo aberto no momento. Fechar o escopo atual também vai interromper o uso do namespace.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT UsingNamespace(  
    [in] const WCHAR *fullName);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `fullName`  
 [in] Um ponteiro para o nome totalmente qualificado do namespace.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
