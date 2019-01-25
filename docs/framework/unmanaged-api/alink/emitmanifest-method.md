---
title: Método EmitManifest
ms.date: 03/30/2017
api_name:
- EmitManifest
- IALink.EmitManifest
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitManifest
helpviewer_keywords:
- EmitManifest method
ms.assetid: fdebc1f3-b62e-4d9e-b775-8ccaa8ecb250
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9217a045a8ddf6ad41adcc71a9568a05fe3fb334
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54565534"
---
# <a name="emitmanifest-method"></a>Método EmitManifest
Emite o manifesto final. Chame esse método depois de importar todos os outros arquivos e definir todas as opções. Não chame este método para módulos não associados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT EmitManifest(  
    mdAssembly   AssemblyID,  
    DWORD*       pdwReserveSize,  
    mdAssembly*  ptkManifest  
) PURE;  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `AssemblyID`  
 ID do assembly.  
  
 `pdwReserveSize`  
 Recebe o tamanho para reservar no arquivo de assembly, recuperadas do [função StrongNameSignatureSize](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md).  
  
 `ptkManifest`  
 Opcionalmente, recebe o token de manifesto do assembly.  
  
## <a name="return-value"></a>Valor de retorno  
 Se o método for bem-sucedido, retornará S_OK.  
  
## <a name="requirements"></a>Requisitos  
 Requer alink.h.  
  
## <a name="see-also"></a>Consulte também
- [Interface IALink](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [Interface IALink2](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [API do ALink](../../../../docs/framework/unmanaged-api/alink/index.md)
