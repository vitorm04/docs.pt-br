---
title: Método ISymUnmanagedWriter::SetSymAttribute
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetSymAttribute
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetSymAttribute
helpviewer_keywords:
- SetSymAttribute method [.NET Framework debugging]
- ISymUnmanagedWriter::SetSymAttribute method [.NET Framework debugging]
ms.assetid: 64d9b80e-b883-4539-89c7-03573185a1eb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bd1a55d4100d74b769b2bc1b8fe33d2042f5e739
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428295"
---
# <a name="isymunmanagedwritersetsymattribute-method"></a>Método ISymUnmanagedWriter::SetSymAttribute
Define um atributo personalizado com base no seu nome. Esses atributos são mantidos no repositório de símbolos, ao contrário de atributos personalizados de metadados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetSymAttribute(  
    [in] mdToken parent,  
    [in] const WCHAR *name,  
    [in] ULONG32 cData,  
    [in, size_is(cData)] unsigned char data[]);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `parent`  
 [in] O token de metadados para o qual o atributo é definido.  
  
 `name`  
 [in] Um ponteiro para um `WCHAR` que contém o nome do atributo.  
  
 `cData`  
 [in] Um `ULONG32` que indica o tamanho do `data` matriz.  
  
 `data`  
 [in] O valor do atributo.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
