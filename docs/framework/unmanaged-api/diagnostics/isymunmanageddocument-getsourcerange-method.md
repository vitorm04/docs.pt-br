---
title: "Método ISymUnmanagedDocument::GetSourceRange"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDocument.GetSourceRange
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDocument::GetSourceRange
helpviewer_keywords:
- ISymUnmanagedDocument::GetSourceRange method [.NET Framework debugging]
- GetSourceRange method [.NET Framework debugging]
ms.assetid: 20fefee7-1040-41ba-93dc-bd42f68b90c2
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6c47f1f491b184e9abe9d56d0729100b0d9b36a7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanageddocumentgetsourcerange-method"></a>Método ISymUnmanagedDocument::GetSourceRange
Retorna o intervalo especificado da fonte incorporada no buffer fornecido. O buffer deve ser grande o suficiente para manter o código-fonte.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetSourceRange(  
    [in]  ULONG32  startLine,  
    [in]  ULONG32  startColumn,  
    [in]  ULONG32  endLine,  
    [in]  ULONG32  endColumn,  
    [in]  ULONG32  cSourceBytes,  
    [out] ULONG32  *pcSourceBytes,  
    [out, size_is(cSourceBytes),  
        length_is(*pcSourceBytes)] BYTE source[]);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `startLine`  
 [in] A linha inicial no documento atual.  
  
 `startColumn`  
 [in] A coluna de início do documento atual.  
  
 `endLine`  
 [in] A linha final no documento atual.  
  
 `endColumn`  
 [in] A coluna final no documento atual.  
  
 `cSourceBytes`  
 [in] O tamanho da fonte, em bytes.  
  
 `pcSourceBytes`  
 [out] Um ponteiro para uma variável que recebe o tamanho da fonte.  
  
 `source`  
 [out] O tamanho e o comprimento do intervalo especificado do documento de origem, em bytes.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK se o método for bem-sucedido.  
  
## <a name="see-also"></a>Consulte também  
 [Interface ISymUnmanagedDocument](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
