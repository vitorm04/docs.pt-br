---
title: "Método ISymUnmanagedWriter::DefineLocalVariable"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.DefineLocalVariable
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::DefineLocalVariable
helpviewer_keywords:
- ISymUnmanagedWriter::DefineLocalVariable method [.NET Framework debugging]
- DefineLocalVariable method [.NET Framework debugging]
ms.assetid: 6fab8a58-3883-490f-8b27-64042c90f104
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e454aa2c2dd8ceb8f8dbbc03bdd1e70e8a800de2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriterdefinelocalvariable-method"></a>Método ISymUnmanagedWriter::DefineLocalVariable
Define uma única variável no escopo léxico atual. Esse método pode ser chamado várias vezes para uma variável de mesmo nome que tem várias casas ao longo de um escopo. Nesse caso, no entanto, os valores de `startOffset` e `endOffset` parâmetros não devem se sobrepor.  
  
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
  
#### <a name="parameters"></a>Parâmetros  
 `name`  
 [in] Um ponteiro para um `WCHAR` que define o nome da variável local.  
  
 `attributes`  
 [in] Os atributos de variável locais.  
  
 `cSig`  
 [in] Um `ULONG32` que indica o tamanho, em bytes, do `signature` buffer.  
  
 `signature`  
 [in] A assinatura de variável local.  
  
 `addrKind`  
 [in] O tipo de endereço.  
  
 `addr1`  
 [in] O primeiro endereço para a especificação do parâmetro.  
  
 `addr2`  
 [in] O segundo endereço para a especificação do parâmetro.  
  
 `addr3`  
 [in] O terceiro endereço para a especificação do parâmetro.  
  
 `startOffset`  
 [in] O deslocamento de início para a variável. Esse parâmetro é opcional. Se for 0, esse parâmetro é ignorado e a variável é definida em toda a todo o escopo. Se for um valor diferente de zero, a variável está dentro de deslocamentos do escopo atual.  
  
 `endOffset`  
 [in] O deslocamento de fim para a variável. Esse parâmetro é opcional. Se for 0, esse parâmetro é ignorado e a variável é definida em toda a todo o escopo. Se for um valor diferente de zero, a variável está dentro de deslocamentos do escopo atual.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [Método DefineGlobalVariable](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)  
 [Método DefineLocalVariable2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-definelocalvariable2-method.md)
