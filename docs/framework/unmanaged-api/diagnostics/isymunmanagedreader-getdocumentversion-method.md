---
title: "Método ISymUnmanagedReader::GetDocumentVersion"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.GetDocumentVersion
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::GetDocumentVersion
helpviewer_keywords:
- GetDocumentVersion method [.NET Framework debugging]
- ISymUnmanagedReader::GetDocumentVersion method [.NET Framework debugging]
ms.assetid: a51f1f64-e084-44c5-830c-2222da5a6bbf
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 377457fa852e1a4ae140f72d2dd83731490b81d9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreadergetdocumentversion-method"></a>Método ISymUnmanagedReader::GetDocumentVersion
Obtém a versão especificada do documento especificado. A versão do documento começa em 1 e é incrementada toda vez que o documento é atualizado usando o [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) método. Se o `pbCurrent` parâmetro é `true`, esta é a versão mais recente do documento.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetDocumentVersion (  
    [in]  ISymUnmanagedDocument *pDoc,  
    [out] int* version,  
    [out] BOOL* pbCurrent);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pDoc`  
 [in] O documento especificado.  
  
 `version`  
 [out] Um ponteiro para uma variável que recebe a versão do documento especificado.  
  
 `pbCurrent`  
 [out] Um ponteiro para uma variável que recebe `true` se esta é a versão mais recente do documento, ou `false` se não for a versão mais recente.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
