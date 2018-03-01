---
title: "Método ISymUnmanagedENCUpdate::UpdateSymbolStore2"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ISymUnmanagedENCUpdate.UpdateSymbolStore2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::UpdateSymbolStore2
helpviewer_keywords:
- ISymUnmanagedENCUpdate::UpdateSymbolStore2 method [.NET Framework debugging]
- UpdateSymbolStore2 method [.NET Framework debugging]
ms.assetid: 35588317-6184-485c-ab41-4b15fc1765d9
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a366047530f3433ab1bfbb5f30d4b9b54c5bdb08
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedencupdateupdatesymbolstore2-method"></a>Método ISymUnmanagedENCUpdate::UpdateSymbolStore2
Permite que um compilador para omitir as funções que não foram modificadas desde o fluxo do programa (PDB) de banco de dados, desde que as informações de linha atende aos requisitos. As informações corretas de linha podem ser determinadas com as informações de linha PDB antigas e um delta para todas as linhas na função.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT UpdateSymbolStore2(  
    [in]  IStream      *pIStream,  
    [in]  SYMLINEDELTA* pDeltaLines,  
    [in]  ULONG         cDeltaLines);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pIStream`  
 [in] Um ponteiro para um <xref:IStream> que contém as informações de linha.  
  
 `pDeltaLines`  
 [in] Um ponteiro para um [SYMLINEDELTA](../../../../docs/framework/unmanaged-api/diagnostics/symlinedelta-structure.md) estrutura que contém as linhas que foram alteradas.  
  
 `cDeltaLines`  
 [in] Um `ULONG` que representa o número de linhas que foram alteradas.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface ISymUnmanagedENCUpdate](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
