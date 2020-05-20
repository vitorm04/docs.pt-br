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
ms.openlocfilehash: 53cc908e0dc8cc5cc980ec365ccac0df4e620cac
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609762"
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
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Confira também

- [Interface ISymUnmanagedWriter](isymunmanagedwriter-interface.md)
