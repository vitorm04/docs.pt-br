---
title: "Método ISymUnmanagedWriter2::DefineLocalVariable2"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ISymUnmanagedWriter2.DefineLocalVariable2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2::DefineLocalVariable2
helpviewer_keywords:
- ISymUnmanagedWriter2::DefineLocalVariable2 method [.NET Framework debugging]
- DefineLocalVariable2 method [.NET Framework debugging]
ms.assetid: e774eefe-858c-4362-8d2d-28ebf2ba1a24
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1124b57bed16e349c753be872c1b709a287e6237
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter2definelocalvariable2-method"></a>Método ISymUnmanagedWriter2::DefineLocalVariable2
Define uma única variável no escopo léxico atual. Esse método pode ser chamado várias vezes para uma variável de mesmo nome que tem várias casas ao longo de um escopo. Nesse caso, no entanto, os valores de `startOffset` e `endOffset` parâmetros não devem se sobrepor.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT DefineLocalVariable2(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] mdSignature  sigToken,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3,  
    [in] ULONG32      startOffset,  
    [in] ULONG32      endOffset);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `name`  
 [in] O nome da variável local.  
  
 `attributes`  
 [in] Os atributos de variável locais.  
  
 `sigToken`  
 [in] O token de metadados da assinatura.  
  
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
 **Cabeçalho:** CorSym.idl  
  
## <a name="see-also"></a>Consulte também  
 [Interface ISymUnmanagedWriter2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 [Método DefineLocalVariable](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)
