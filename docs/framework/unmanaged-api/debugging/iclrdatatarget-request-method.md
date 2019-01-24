---
title: Método ICLRDataTarget::Request
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.Request
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::Request
helpviewer_keywords:
- ICLRDataTarget::Request method [.NET Framework debugging]
- Request method [.NET Framework debugging]
ms.assetid: 4723bd1c-eddb-4ed2-897a-010024a47e01
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 77bd3bc239d0101f02cd515b0ec2a8bec3372882
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54596898"
---
# <a name="iclrdatatargetrequest-method"></a>Método ICLRDataTarget::Request
Chamado pelo serviço common language runtime (CLR) dados acesso para solicitar uma operação, conforme definido pela implementação.  
  
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
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** ClrData.idl, ClrData.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
