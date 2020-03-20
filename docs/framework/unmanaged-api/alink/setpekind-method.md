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
ms.openlocfilehash: 5a8442b1f0869e1592a05dfeeb0f5e6d583f3ea8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179383"
---
# <a name="setpekind-method"></a>Método SetPEKind
Determina o tipo executável portátil, específico da máquina ou agnóstico da máquina.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetPEKind(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwPEKind,  
    DWORD dwMachine  
) PURE;
```  
  
## <a name="parameters"></a>parâmetros  
 `AssemblyID`  
 ID da assembléia.  
  
 `FileToken`  
 Token de arquivo para o qual o tipo PE deve ser definido. Pode ser `AssemblyID` NULO se não indicar um módulo de rede não vinculado.  
  
 `dwPEKind`  
 O tipo de PE, conforme indicado pela [Enumeração CorPEKind](../metadata/corpekind-enumeration.md).  
  
 `dwMachine`  
 A arquitetura da máquina de destino, conforme indicado no cabeçalho NT.  
  
## <a name="return-value"></a>Valor retornado  
 Retorna S_OK se o método for bem sucedido.  
  
## <a name="requirements"></a>Requisitos  
 Requer alink.h.  
  
## <a name="see-also"></a>Confira também

- [Método GetPEKind](../metadata/imetadataimport2-getpekind-method.md)
- [Interface IALink2](ialink2-interface.md)
- [Interface IALink](ialink-interface.md)
- [API do ALink](index.md)
