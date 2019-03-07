---
title: Método ISymUnmanagedWriter::DefineLocalVariable
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineLocalVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineLocalVariable
helpviewer_keywords:
- ISymUnmanagedWriter::DefineLocalVariable method [.NET Framework debugging]
- DefineLocalVariable method [.NET Framework debugging]
ms.assetid: 6fab8a58-3883-490f-8b27-64042c90f104
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1361d6e93fcf39a86951a78f1245e9158d6ed314
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57483609"
---
# <a name="isymunmanagedwriterdefinelocalvariable-method"></a>Método ISymUnmanagedWriter::DefineLocalVariable
Define uma única variável no escopo léxico atual. Esse método pode ser chamado várias vezes para uma variável de mesmo nome que tem vários residências ao longo de um escopo. Nesse caso, no entanto, os valores de `startOffset` e `endOffset` parâmetros não devem se sobrepor.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT DefineLocalVariable(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3,  
    [in] ULONG32      startOffset,  
    [in] ULONG32      endOffset);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `name`  
 [in] Um ponteiro para um `WCHAR` que define o nome da variável local.  
  
 `attributes`  
 [in] Atributos da variável local.  
  
 `cSig`  
 [in] Um `ULONG32` que indica o tamanho, em bytes, da `signature` buffer.  
  
 `signature`  
 [in] A assinatura da variável local.  
  
 `addrKind`  
 [in] O tipo de endereço.  
  
 `addr1`  
 [in] O primeiro endereço para a especificação de parâmetro.  
  
 `addr2`  
 [in] O segundo endereço para a especificação de parâmetro.  
  
 `addr3`  
 [in] O terceiro endereço para a especificação de parâmetro.  
  
 `startOffset`  
 [in] O deslocamento inicial da variável. Esse parâmetro é opcional. Se for 0, esse parâmetro será ignorado e a variável será definida ao longo de todo o escopo. Se for um valor diferente de zero, a variável estará dentro dos deslocamentos do escopo atual.  
  
 `endOffset`  
 [in] O deslocamento final da variável. Esse parâmetro é opcional. Se for 0, esse parâmetro será ignorado e a variável será definida ao longo de todo o escopo. Se for um valor diferente de zero, a variável estará dentro dos deslocamentos do escopo atual.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também
- [Interface ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [Método DefineGlobalVariable](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)
- [Método DefineLocalVariable2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-definelocalvariable2-method.md)
