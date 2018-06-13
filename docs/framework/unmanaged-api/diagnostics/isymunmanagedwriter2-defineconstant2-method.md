---
title: Método ISymUnmanagedWriter2::DefineConstant2
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2.DefineConstant2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2::DefineConstant2
helpviewer_keywords:
- DefineConstant2 method [.NET Framework debugging]
- ISymUnmanagedWriter2::DefineConstant2 method [.NET Framework debugging]
ms.assetid: dd2bc956-7dbe-49fc-a646-daa0d267f2df
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c6f9f198fc1115aed7b531515ab07ddc35d36ba8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427330"
---
# <a name="isymunmanagedwriter2defineconstant2-method"></a>Método ISymUnmanagedWriter2::DefineConstant2
Define um nome para um valor constante.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT DefineConstant2(  
    [in] const WCHAR  *name,  
    [in] VARIANT      value,  
    [in] mdSignature  sigToken);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `name`  
 [in] O nome de constante.  
  
 `value`  
 [in] O valor da constante.  
  
 `sigToken`  
 [in] O token de metadados da constante.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface ISymUnmanagedWriter2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 [Método DefineConstant](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineconstant-method.md)
