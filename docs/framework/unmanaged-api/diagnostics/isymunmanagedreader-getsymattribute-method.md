---
title: Método ISymUnmanagedReader::GetSymAttribute
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetSymAttribute
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetSymAttribute
helpviewer_keywords:
- GetSymAttribute method [.NET Framework debugging]
- ISymUnmanagedReader::GetSymAttribute method [.NET Framework debugging]
ms.assetid: c675ce7e-76e7-45ff-8273-3b6489a2767c
topic_type:
- apiref
ms.openlocfilehash: 7f04b5c100f1fd9c44e671b883fe469b16d33fa6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440142"
---
# <a name="isymunmanagedreadergetsymattribute-method"></a>Método ISymUnmanagedReader::GetSymAttribute
Obtém um atributo personalizado com base no seu nome. Ao contrário dos atributos personalizados de metadados, esses atributos personalizados são mantidos no repositório de símbolos.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetSymAttribute (  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is (cBuffer),  
        length_is (*pcBuffer)] BYTE buffer[]);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `parent`  
 no O token de metadados para o objeto para o qual o atributo é solicitado.  
  
 `name`  
 no Um ponteiro para a variável que indica o atributo a ser recuperado.  
  
 `cBuffer`  
 no O tamanho da matriz de `buffer`.  
  
 `pcBuffer`  
 fora Um ponteiro para a variável que recebe o comprimento dos dados de atributo.  
  
 `buffer`  
 fora Um ponteiro para a variável que recebe os dados de atributo.  
  
## <a name="return-value"></a>Valor retornado  
 S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Cabeçalho:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Consulte também

- [Interface ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
