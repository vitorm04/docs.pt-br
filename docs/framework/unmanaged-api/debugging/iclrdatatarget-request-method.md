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
ms.openlocfilehash: b913affb4728dc80ba67438384cbeac87265f76d
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860546"
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
 O `Request` método facilita a adição de operações personalizadas não especificadas. Ou seja, esse método fornece extensibilidade sem exigir a revisão da definição da interface.  
  
 Este método é implementado pelo autor do aplicativo de depuração.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** ClrData. idl, ClrData. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICLRDataTarget](iclrdatatarget-interface.md)
