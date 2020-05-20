---
title: Método ISymUnmanagedReader::GetMethodsFromDocumentPosition
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodsFromDocumentPosition
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodsFromDocumentPosition
helpviewer_keywords:
- GetMethodsFromDocumentPosition method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodsFromDocumentPosition method [.NET Framework debugging]
ms.assetid: 83605f1e-e4f3-49e6-859b-f13cad68bb54
topic_type:
- apiref
ms.openlocfilehash: bba0fc039c403d45e8a5b60f2b0231eb24226280
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614949"
---
# <a name="isymunmanagedreadergetmethodsfromdocumentposition-method"></a>Método ISymUnmanagedReader::GetMethodsFromDocumentPosition
Retorna uma matriz de métodos, cada um contendo o ponto de interrupção na posição especificada em um documento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetMethodsFromDocumentPosition (  
    [in]  ISymUnmanagedDocument* document,  
    [in]  ULONG32 line,  
    [in]  ULONG32 column,  
    [in]  ULONG32 cMethod,  
    [out] ULONG32* pcMethod,  
    [out, size_is (cMethod),  
        length_is (*pcMethod)] ISymUnmanagedMethod* pRetVal[]);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `document`  
 no O documento especificado.  
  
 `line`  
 no A linha do documento especificado.  
  
 `column`  
 no A coluna do documento especificado.  
  
 `cMethod`  
 no O tamanho da `pRetVal` matriz.  
  
 `pcMethod`  
 fora Um ponteiro para uma variável que recebe o número de elementos retornados na `pRetVal` matriz.  
  
 `pRetVal`  
 fora Uma matriz de ponteiros, cada um dos quais aponta para um objeto [ISymUnmanagedMethod](isymunmanagedmethod-interface.md) que representa um método que contém o ponto de interrupção.  
  
## <a name="return-value"></a>Valor retornado  
 S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Confira também

- [Interface ISymUnmanagedReader](isymunmanagedreader-interface.md)
