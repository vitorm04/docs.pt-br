---
title: Método ISymUnmanagedWriter::GetDebugInfo
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.GetDebugInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::GetDebugInfo
helpviewer_keywords:
- ISymUnmanagedWriter::GetDebugInfo method [.NET Framework debugging]
- GetDebugInfo method [.NET Framework debugging]
ms.assetid: dd31c210-6829-45eb-927e-cc53932638b7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ce74b043db67fa1086724dd76001935f9c1c0498
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57470935"
---
# <a name="isymunmanagedwritergetdebuginfo-method"></a>Método ISymUnmanagedWriter::GetDebugInfo
Retorna as informações necessárias para que um compilador gravar a entrada de diretório de depuração no cabeçalho de arquivo executável (PE) da portátil. O gravador de símbolo preenche todos os campos, exceto para `TimeDateStamp` e `PointerToRawData`. (O compilador é responsável por definir esses dois campos adequadamente).  
  
 Um compilador deve chamar esse método, emita o blob de dados até o arquivo PE, defina o `PointerToRawData` campo o IMAGE_DEBUG_DIRECTORY para apontar para os dados emitidos e gravar o IMAGE_DEBUG_DIRECTORY até o arquivo PE. O compilador também deve definir a `TimeDateStamp` campo para igualar o `TimeDateStamp` do arquivo PE que está sendo gerado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetDebugInfo(  
    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,  
    [in]  DWORD cData,  
    [out] DWORD *pcData,  
    [out, size_is(cData),  
        length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pIDD`  
 [no, out] Um ponteiro para um IMAGE_DEBUG_DIRECTORY que preencherá o gravador de símbolo.  
  
 `cData`  
 [in] Um `DWORD` que contém o tamanho dos dados de depuração.  
  
 `pcData`  
 [out] Um ponteiro para um `DWORD` que recebe o tamanho do buffer necessário para conter os dados de depuração.  
  
 `data`  
 [out] Um ponteiro para um buffer que é grande o suficiente para manter os dados de depuração para o repositório de símbolos.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também
- [Interface ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
