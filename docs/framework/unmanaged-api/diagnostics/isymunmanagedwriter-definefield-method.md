---
title: Método ISymUnmanagedWriter::DefineField
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineField
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineField
helpviewer_keywords:
- ISymUnmanagedWriter::DefineField method [.NET Framework debugging]
- DefineField method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: c6a1f797-dbf4-40f5-ab99-d9b4bfb26148
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5d5b3c60845fce39ce7f904c6871e7feb16e8970
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429808"
---
# <a name="isymunmanagedwriterdefinefield-method"></a>Método ISymUnmanagedWriter::DefineField
Define uma única variável que não está dentro de um método. Esse método é usado para determinados campos em classes, campos de bits e assim por diante.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT DefineField(  
    [in] mdTypeDef    parent,  
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
 `parent`  
 [in] O tipo de metadados ou um método de token.  
  
 `name`  
 [in] O nome do campo.  
  
 `attributes`  
 [in] Os atributos de campo.  
  
 `cSig`  
 [in] Um `ULONG32` que é o tamanho, em caracteres, do buffer necessário para conter a assinatura de campo.  
  
 `signature`  
 [in] A matriz de assinaturas de campo.  
  
 `addrKind`  
 [in] O tipo de endereço.  
  
 `addr1`  
 [in] O primeiro endereço para a especificação de campo.  
  
 `addr2`  
 [in] O segundo endereço para a especificação de campo.  
  
 `addr3`  
 [in] O terceiro endereço para a especificação de campo.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
