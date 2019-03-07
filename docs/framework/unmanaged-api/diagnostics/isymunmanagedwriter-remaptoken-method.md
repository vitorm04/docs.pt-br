---
title: Método ISymUnmanagedWriter::RemapToken
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.RemapToken
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::RemapToken
helpviewer_keywords:
- ISymUnmanagedWriter::RemapToken method [.NET Framework debugging]
- RemapToken method [.NET Framework debugging]
ms.assetid: bca92682-ee1e-467f-8fb0-d8d4617f82fe
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ec4a486b9dfb72c05a9e614fca22626dd84a83f7
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468449"
---
# <a name="isymunmanagedwriterremaptoken-method"></a>Método ISymUnmanagedWriter::RemapToken
Notifica o gravador de símbolo que um token de metadados foi remapeado, pois os metadados foi emitido. Se o gravador de símbolo tiver armazenado o token antigo no repositório de símbolos, ele deve atualizar que o token armazenado com o novo valor, ou ele deve salvar o mapa para o leitor de símbolo correspondente remapear durante a fase de leitura.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT RemapToken(  
    [in] mdToken  oldToken,  
    [in] mdToken  newToken);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `oldToken`  
 [in] O token de metadados que remapeado.  
  
 `newToken`  
 [in] O novo token de metadados para o qual `oldToken` remapeado.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também
- [Interface ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
