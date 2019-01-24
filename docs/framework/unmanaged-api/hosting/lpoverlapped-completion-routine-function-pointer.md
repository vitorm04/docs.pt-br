---
title: Ponteiro de função LPOVERLAPPED_COMPLETION_ROUTINE
ms.date: 03/30/2017
api_name:
- LPOVERLAPPED_COMPLETION_ROUTINE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- LPOVERLAPPED_COMPLETION_ROUTINE
helpviewer_keywords:
- LPOVERLAPPED_COMPLETION_ROUTINE function pointer [.NET Framework hosting]
ms.assetid: 5fb645d9-b818-401c-8c2c-c30d86de58ba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c2c3040adddabee716976d778c29d1f6729efc39
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54576922"
---
# <a name="lpoverlappedcompletionroutine-function-pointer"></a>Ponteiro de função LPOVERLAPPED_COMPLETION_ROUTINE
Aponta para uma função que notifica o host quando um sobreposta (ou seja, assíncrona) e/s para um dispositivo foi concluída.  
  
 Esse ponteiro de função foi preterido no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef VOID (*LPOVERLAPPED_COMPLETION_ROUTINE) (  
    [in] DWORD  dwErrorCode,  
    [in] DWORD  dwNumberOfBytesTransfered,  
    [in] LPVOID lpOverlapped  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwErrorCode`  
 [in] Um valor que é um código de erro se o dispositivo foi fechado; Caso contrário, esse valor é zero.  
  
 Fechar um dispositivo faz com que todas as pendentes de e/s para o dispositivo para ser concluída imediatamente.  
  
 `dwNumberOfBytesTransfered`  
 [in] O número de bytes transferidos pela operação de e/s.  
  
 `lpOverlapped`  
 [in] Um ponteiro para uma estrutura que contém as informações a serem usadas para concluir a solicitação de e/s.  
  
## <a name="remarks"></a>Comentários  
 A função à qual `LPOVERLAPPED_COMPLETION_ROUTINE` pontos é uma função de retorno de chamada e devem ser implementados pelo gravador do aplicativo host. A função de retorno de chamada permite que o host processar a solicitação de e/s concluída.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** MSCorWks.dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Funções de hospedagem CLR preteridas](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
