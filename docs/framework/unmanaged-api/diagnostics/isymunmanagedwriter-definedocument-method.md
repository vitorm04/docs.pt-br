---
title: Método ISymUnmanagedWriter::DefineDocument
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineDocument
helpviewer_keywords:
- ISymUnmanagedWriter::DefineDocument method [.NET Framework debugging]
- DefineDocument method [.NET Framework debugging]
ms.assetid: c3bf15b0-3250-4bbe-b9b5-c5d695289b6f
topic_type:
- apiref
ms.openlocfilehash: 02b270677131d0960db67b0ac8db38cba2b5e2df
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428047"
---
# <a name="isymunmanagedwriterdefinedocument-method"></a>Método ISymUnmanagedWriter::DefineDocument
Define um documento de origem. Os GUIDs são fornecidos para idiomas, fornecedores e tipos de documentos conhecidos.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT DefineDocument(  
    [in]  const WCHAR  *url,  
    [in]  const GUID   *language,  
    [in]  const GUID   *languageVendor,  
    [in]  const GUID   *documentType,  
    [out, retval] ISymUnmanagedDocumentWriter**  pRetVal);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `url`  
 no Um ponteiro para um `WCHAR` que define o Uniform Resource Locator (URL) que identifica o documento.  
  
 `language`  
 no Um ponteiro para um GUID que define o idioma do documento.  
  
 `languageVendor`  
 no Um ponteiro para um GUID que define a identidade do fornecedor para o idioma do documento.  
  
 `documentType`  
 no Um ponteiro para um GUID que define o tipo do documento.  
  
 `pRetVal`  
 fora Um ponteiro para a interface [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) retornada.  
  
## <a name="return-value"></a>Valor retornado  
 S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Consulte também

- [Interface ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
