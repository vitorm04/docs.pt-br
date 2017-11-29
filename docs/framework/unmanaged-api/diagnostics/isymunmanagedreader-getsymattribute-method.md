---
title: "Método ISymUnmanagedReader::GetSymAttribute"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.GetSymAttribute
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::GetSymAttribute
helpviewer_keywords:
- GetSymAttribute method [.NET Framework debugging]
- ISymUnmanagedReader::GetSymAttribute method [.NET Framework debugging]
ms.assetid: c675ce7e-76e7-45ff-8273-3b6489a2767c
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f57d2c4541945d90b1695850311928884fdc9cc5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
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
