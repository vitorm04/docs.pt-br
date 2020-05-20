---
title: Método ISymUnmanagedWriter4::GetDebugInfoWithPadding
ms.date: 03/30/2017
ms.assetid: 881e20ca-8131-4bd0-ba41-c2d6391b0fe2
ms.openlocfilehash: cfc6c22558cee780823c8cca0c36b883147e9496
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614637"
---
# <a name="isymunmanagedwriter4getdebuginfowithpadding-method"></a>Método ISymUnmanagedWriter4::GetDebugInfoWithPadding
O funciona da mesma forma que o [método GetDebugInfo](isymunmanagedwriter-getdebuginfo-method.md) , exceto pelo fato de que a cadeia de caracteres de caminho é preenchida com zeros após o caractere nulo de terminação para tornar os dados da cadeia de caracteres um tamanho fixo `MAX_PATH` . O preenchimento só será fornecido se o comprimento da cadeia de caracteres do caminho for menor que `MAX_PATH` .  
  
 Isso facilita a gravação de ferramentas que diferenciam arquivos PE.  
  
## <a name="syntax"></a>Sintaxe  
  
```idl  
HRESULT GetDebugInfoWithPadding(    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,    [in] DWORD cData,    [out] DWORD *pcData,    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a>Parâmetros  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`pIDD`||  
|`cData`||  
|`pcData`||  
|`data`||  
  
## <a name="return-value"></a>Valor retornado  
 Retorna `HRESULT`.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Confira também

- [Interface ISymUnmanagedWriter4](isymunmanagedwriter4-interface.md)
