---
title: Método GetResolutionScope
ms.date: 03/30/2017
api_name:
- IALink.GetResolutionScope
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetResolutionScope
helpviewer_keywords:
- GetResolutionScope method
ms.assetid: 5b48ca60-dacd-44b2-9979-4a5122f00812
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f8d230d5396c5a088fa76a7ca145b4a22d1e1d07
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54543351"
---
# <a name="getresolutionscope-method"></a>Método GetResolutionScope
Recupera o escopo de um determinado tipo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetResolutionScope(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    mdToken     TargetFile,  
    mdToken*    pScope  
) PURE;  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `AssemblyID`  
 ID do assembly.  
  
 `FileToken`  
 Arquivo que é a necessidade de uma referência.  
  
 `TargetFile`  
 Token de arquivo desse tipo é definido no, geralmente são recuperadas com [método ImportFile](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).  
  
 `pScope`  
 Recebe o assembly ou uma referência de módulo.  
  
## <a name="return-value"></a>Valor de retorno  
 Se o método for bem-sucedido, retornará S_OK.  
  
## <a name="requirements"></a>Requisitos  
 Requer alink.h.  
  
## <a name="see-also"></a>Consulte também
- [Interface IALink](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [Interface IALink2](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [API do ALink](../../../../docs/framework/unmanaged-api/alink/index.md)
