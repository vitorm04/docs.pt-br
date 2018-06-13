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
ms.openlocfilehash: 4b985aeb97621e552e9e97581e67cae029d019ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405887"
---
# <a name="setpekind-method"></a>Método SetPEKind
Determina o tipo de executável portátil, específicas de computador ou máquina independente.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetPEKind(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwPEKind,  
    DWORD dwMachine  
) PURE;   
```  
  
#### <a name="parameters"></a>Parâmetros  
 `AssemblyID`  
 ID do assembly.  
  
 `FileToken`  
 Token de arquivo para o qual o tipo de PE será definido. Pode ser NULL se `AssemblyID` não indica um netmodule não associado.  
  
 `dwPEKind`  
 O tipo de PE, conforme indicado pelo [enumeração CorPEKind](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md).  
  
 `dwMachine`  
 A arquitetura da máquina de destino, conforme indicado no cabeçalho do NT.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna S_OK se o método for bem-sucedido.  
  
## <a name="requirements"></a>Requisitos  
 Requer alink.h.  
  
## <a name="see-also"></a>Consulte também  
 [Método GetPEKind](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)  
 [Interface IALink2](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [Interface IALink](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [API do ALink](../../../../docs/framework/unmanaged-api/alink/index.md)
