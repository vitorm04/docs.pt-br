---
title: Método ISymUnmanagedDocument::FindClosestLine
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.FindClosestLine
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::FindClosestLine
helpviewer_keywords:
- FindClosestLine method [.NET Framework debugging]
- ISymUnmanagedDocument::FindClosestLine method [.NET Framework debugging]
ms.assetid: 628f2a04-e529-407d-841e-3b3da219a9cb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 96ad0e34bf638c378f37e317f790696c2ac7cb25
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54519691"
---
# <a name="isymunmanageddocumentfindclosestline-method"></a>Método ISymUnmanagedDocument::FindClosestLine
Retorna a linha mais próxima que é um ponto de sequência, considerando uma linha neste documento que pode ou não ser um ponto de sequência.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT FindClosestLine(  
    [in]  ULONG32  line,  
    [out, retval] ULONG32*  pRetVal);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `line`  
 [in] Uma linha neste documento.  
  
 `pRetVal`  
 [out] Um ponteiro para uma variável que recebe a linha.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK se o método for bem-sucedido; Caso contrário, um código de erro.  
  
## <a name="see-also"></a>Consulte também
- [Interface ISymUnmanagedDocument](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
