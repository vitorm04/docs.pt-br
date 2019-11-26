---
title: Método ISymUnmanagedWriter::SetUserEntryPoint
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetUserEntryPoint
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetUserEntryPoint
helpviewer_keywords:
- ISymUnmanagedWriter::SetUserEntryPoint method [.NET Framework debugging]
- SetUserEntryPoint method [.NET Framework debugging]
ms.assetid: d4dcc575-3ac8-4453-9be1-2b24f47363d7
topic_type:
- apiref
ms.openlocfilehash: 951fc10a4560e0b4e256312017cdcd9a389f17f5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427821"
---
# <a name="isymunmanagedwritersetuserentrypoint-method"></a>Método ISymUnmanagedWriter::SetUserEntryPoint
Specifies the user-defined method that is the entry point for this module. For example, this entry point could be the user's main method instead of compiler-generated stubs before main.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetUserEntryPoint(  
    [in] mdMethodDef entryMethod);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `entryMethod`  
 [in] The metadata token for the method that is the user entry point.  
  
## <a name="return-value"></a>Valor retornado  
 S_OK if the method succeeds; otherwise, E_FAIL or some other error code.  
  
## <a name="requirements"></a>Requisitos  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também

- [Interface ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
