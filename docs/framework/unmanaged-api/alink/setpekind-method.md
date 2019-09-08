---
title: Método SetPEKind
ms.date: 03/30/2017
api_name:
- IALink2.SetPEKind
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetPEKind
helpviewer_keywords:
- SetPEKind method
ms.assetid: 050e77ee-3014-45c0-9e29-2ebe29347b0d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9a48dbd38d357b668c2794ae6305ceb9cad3dcf4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787199"
---
# <a name="setpekind-method"></a>Método SetPEKind
Determina o tipo de executável portátil, específico do computador ou independente do computador.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetPEKind(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwPEKind,  
    DWORD dwMachine  
) PURE;   
```  
  
## <a name="parameters"></a>Parâmetros  
 `AssemblyID`  
 ID do assembly.  
  
 `FileToken`  
 Token do arquivo para o qual o tipo PE deve ser definido. Pode ser NULL se `AssemblyID` não indicar um netmodule não associado.  
  
 `dwPEKind`  
 O tipo de PE, conforme indicado pela [Enumeração CorPEKind](../metadata/corpekind-enumeration.md).  
  
 `dwMachine`  
 A arquitetura do computador de destino, conforme indicado no cabeçalho do NT.  
  
## <a name="return-value"></a>Valor de retorno  
 Retornará S_OK se o método tiver sucesso.  
  
## <a name="requirements"></a>Requisitos  
 Requer ALink. h.  
  
## <a name="see-also"></a>Consulte também

- [Método GetPEKind](../metadata/imetadataimport2-getpekind-method.md)
- [Interface IALink2](ialink2-interface.md)
- [Interface IALink](ialink-interface.md)
- [API do ALink](index.md)
