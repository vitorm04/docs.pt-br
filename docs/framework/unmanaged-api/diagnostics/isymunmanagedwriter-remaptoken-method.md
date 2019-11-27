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
ms.openlocfilehash: 9e441d4ff39632d9381e445ee99249d04539ad87
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427877"
---
# <a name="isymunmanagedwriterremaptoken-method"></a>Método ISymUnmanagedWriter::RemapToken
Notifica o gravador de símbolo de que um token de metadados foi remapeado conforme os metadados foram emitidos. Se o gravador de símbolo tiver armazenado o token antigo no armazenamento de símbolo, ele deverá atualizar o token armazenado com o novo valor ou salvar o mapa do leitor de símbolo correspondente para remapear durante a fase de leitura.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT RemapToken(  
    [in] mdToken  oldToken,  
    [in] mdToken  newToken);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `oldToken`  
 no O token de metadados que foi remapeado.  
  
 `newToken`  
 no O novo token de metadados para o qual `oldToken` foi remapeado.  
  
## <a name="return-value"></a>Valor retornado  
 S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Cabeçalho:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Consulte também

- [Interface ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
