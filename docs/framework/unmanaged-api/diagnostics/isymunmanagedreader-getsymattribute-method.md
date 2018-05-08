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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c9f22f23835f01022d5d62596b2cf63425759193
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedreadergetsymattribute-method"></a>Método ISymUnmanagedReader::GetSymAttribute
Obtém um atributo personalizado com base no seu nome. Ao contrário de atributos personalizados de metadados, os atributos personalizados são mantidos no repositório de símbolos.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetSymAttribute (  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is (cBuffer),  
        length_is (*pcBuffer)] BYTE buffer[]);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `parent`  
 [in] O token de metadados para o objeto para o qual o atributo é solicitado.  
  
 `name`  
 [in] Um ponteiro para a variável que indica o atributo para recuperar.  
  
 `cBuffer`  
 [in] O tamanho do `buffer` matriz.  
  
 `pcBuffer`  
 [out] Um ponteiro para a variável que recebe o comprimento dos dados de atributo.  
  
 `buffer`  
 [out] Um ponteiro para a variável que recebe os dados de atributo.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
