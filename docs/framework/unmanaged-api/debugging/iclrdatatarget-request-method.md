---
title: "Método ICLRDataTarget::Request"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget.Request
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget::Request
helpviewer_keywords:
- ICLRDataTarget::Request method [.NET Framework debugging]
- Request method [.NET Framework debugging]
ms.assetid: 4723bd1c-eddb-4ed2-897a-010024a47e01
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0e0ce905ea21267419e6a68e73f918de8fc364f3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="iclrdatatargetrequest-method"></a>Método ICLRDataTarget::Request
Chamado pelos comuns language runtime (CLR) dados serviços de acesso para uma operação de solicitação, conforme definido pela implementação.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT Request (  
    [in] ULONG32            reqCode,  
    [in] ULONG32            inBufferSize,  
    [in, size_is(inBufferSize)]   
        BYTE                *inBuffer,  
    [in] ULONG32            outBufferSize,  
    [out, size_is(outBufferSize)]   
        BYTE                *outBuffer  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `reqCode`  
 [in] Definido pelo usuário.  
  
 `inBufferSize`  
 [in] O tamanho do buffer de entrada, que é usado para a solicitação de entrada.  
  
 `inBuffer`  
 [in] Um buffer que contém a solicitação.  
  
 `outBufferSize`  
 [in] O tamanho do buffer de saída, que é usado para a resposta.  
  
 `outBuffer`  
 [out] Um Buffer que contém a resposta.  
  
## <a name="remarks"></a>Comentários  
 O `Request` método facilita a adição de operações personalizadas não especificadas. Ou seja, esse método fornece extensibilidade sem a necessidade de revisão da definição da interface.  
  
 Este método é implementado pelo autor do aplicativo de depuração.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** ClrData.idl, ClrData.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
