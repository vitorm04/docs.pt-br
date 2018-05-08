---
title: Método ISymUnmanagedWriter::DefineGlobalVariable
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineGlobalVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineGlobalVariable
helpviewer_keywords:
- ISymUnmanagedWriter::DefineGlobalVariable method [.NET Framework debugging]
- DefineGlobalVariable method [.NET Framework debugging]
ms.assetid: 843c904a-8176-4d8f-bd47-b4d4c29f4c5c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f1dd657c004c58480ea2f603ad4494753463c79b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedwriterdefineglobalvariable-method"></a>Método ISymUnmanagedWriter::DefineGlobalVariable
Define uma única variável global.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT DefineGlobalVariable(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `name`  
 [in] Um ponteiro para um `WCHAR` que define o nome da variável global.  
  
 `attributes`  
 [in] Os atributos de variável global.  
  
 `cSig`  
 [in] Um `ULONG32` que indica o tamanho, em caracteres, do `signature` buffer.  
  
 `signature`  
 [in] A assinatura de variável global.  
  
 `addrKind`  
 [in] O tipo de endereço.  
  
 `addr1`  
 [in] O primeiro endereço para a especificação do parâmetro.  
  
 `addr2`  
 [in] O segundo endereço para a especificação do parâmetro.  
  
 `addr3`  
 [in] O terceiro endereço para a especificação do parâmetro.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [Método DefineLocalVariable](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)  
 [Método DefineGlobalVariable2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineglobalvariable2-method.md)
