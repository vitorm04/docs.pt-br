---
title: Método ISymUnmanagedWriter4::GetDebugInfoWithPadding
ms.date: 03/30/2017
ms.assetid: 881e20ca-8131-4bd0-ba41-c2d6391b0fe2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6a703c7c8adf5d770ea74f8ed869568978f3b42f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428619"
---
# <a name="isymunmanagedwriter4getdebuginfowithpadding-method"></a>Método ISymUnmanagedWriter4::GetDebugInfoWithPadding
Funciona da mesma forma [método GetDebugInfo](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) exceto que a cadeia de caracteres de caminho é preenchida com zeros após o caractere null de terminação para tornar os dados de cadeia de caracteres de tamanho fixo de `MAX_PATH`. O preenchimento é fornecido apenas se o comprimento da cadeia de caracteres de caminho em si é menor que `MAX_PATH`.  
  
 Isso torna mais fácil escrever ferramentas que arquivos de diferença PE.  
  
## <a name="syntax"></a>Sintaxe  
  
```idl  
HRESULT GetDebugInfoWithPadding(    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,    [in] DWORD cData,    [out] DWORD *pcData,    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
#### <a name="parameters"></a>Parâmetros  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`pIDD`||  
|`cData`||  
|`pcData`||  
|`data`||  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna `HRESULT`.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface ISymUnmanagedWriter4](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)
