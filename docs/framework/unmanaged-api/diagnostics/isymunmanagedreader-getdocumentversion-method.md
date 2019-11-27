---
title: Método ISymUnmanagedReader::GetDocumentVersion
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetDocumentVersion
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetDocumentVersion
helpviewer_keywords:
- GetDocumentVersion method [.NET Framework debugging]
- ISymUnmanagedReader::GetDocumentVersion method [.NET Framework debugging]
ms.assetid: a51f1f64-e084-44c5-830c-2222da5a6bbf
topic_type:
- apiref
ms.openlocfilehash: 3bc578be680951a1d41c92fb2169c860882b2e31
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448300"
---
# <a name="isymunmanagedreadergetdocumentversion-method"></a>Método ISymUnmanagedReader::GetDocumentVersion
Obtém a versão especificada do documento especificado. A versão do documento começa em 1 e é incrementada toda vez que o documento é atualizado usando o método [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) . Se o parâmetro `pbCurrent` for `true`, essa será a versão mais recente do documento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetDocumentVersion (  
    [in]  ISymUnmanagedDocument *pDoc,  
    [out] int* version,  
    [out] BOOL* pbCurrent);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pDoc`  
 no O documento especificado.  
  
 `version`  
 fora Um ponteiro para uma variável que recebe a versão do documento especificado.  
  
 `pbCurrent`  
 fora Um ponteiro para uma variável que recebe `true` se esta for a versão mais recente do documento ou `false` se não for a versão mais recente.  
  
## <a name="return-value"></a>Valor retornado  
 S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Cabeçalho:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Consulte também

- [Interface ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
