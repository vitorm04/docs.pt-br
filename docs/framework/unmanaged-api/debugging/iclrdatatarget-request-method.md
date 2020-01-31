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
ms.openlocfilehash: 0a7e764d89dd42bcaf81da5cf6a16991b6b8a16e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793700"
---
# <a name="iclrdatatargetrequest-method"></a>Método ICLRDataTarget::Request
Chamado pelos serviços de acesso a dados do Common Language Runtime (CLR) para solicitar uma operação, conforme definido pela implementação.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
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
  
## <a name="parameters"></a>Parâmetros  
 `reqCode`  
 no Definido pelo usuário.  
  
 `inBufferSize`  
 no O tamanho do buffer de entrada, que é usado para a solicitação de entrada.  
  
 `inBuffer`  
 no Um buffer que contém a solicitação.  
  
 `outBufferSize`  
 no O tamanho do buffer de saída, que é usado para a resposta.  
  
 `outBuffer`  
 fora Um buffer que contém a resposta.  
  
## <a name="remarks"></a>Comentários  
 O método `Request` facilita a adição de operações personalizadas não especificadas. Ou seja, esse método fornece extensibilidade sem exigir a revisão da definição da interface.  
  
 Este método é implementado pelo autor do aplicativo de depuração.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** ClrData. idl, ClrData. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICLRDataTarget](iclrdatatarget-interface.md)
