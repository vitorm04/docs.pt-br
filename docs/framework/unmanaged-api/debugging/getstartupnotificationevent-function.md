---
title: Função GetStartupNotificationEvent
ms.date: 03/30/2017
api_name:
- GetStartupNotificationEvent
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- GetStartupNotificationEvent
helpviewer_keywords:
- GetStartupNotificationEvent function
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: c94b1b61-045a-4695-bacd-0f18c5acc246
topic_type:
- apiref
ms.openlocfilehash: fb158b35165fb229fc78169e2508679b6749752e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122945"
---
# <a name="getstartupnotificationevent-function"></a>Função GetStartupNotificationEvent
Cria ou abre um identificador de evento que será sinalizado por qualquer Common Language Runtime (CLR) que esteja carregando no processo de destino especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetStartupNotificationEvent  
    (  
    [in]  DWORD     debuggeePID,  
    [out]  HANDLE*  phStartupEvent  
    );  
```  
  
## <a name="parameters"></a>Parâmetros  
 `debuggeePID`  
 no Identificador de processo do processo de destino do qual receber notificações de inicialização do CLR.  
  
 `phStartupEvent`  
 fora Um ponteiro para um identificador que será sinalizado por um CLR na inicialização.  
  
## <a name="return-value"></a>Valor retornado  
 S_OK  
 O identificador para o evento de notificação de inicialização foi obtido com êxito.  
  
 E_INVALIDARG  
 `phStartupEvent` é nulo ou `debuggeePID` não se refere a um processo em execução no momento.  
  
 E_FAIL (ou outros códigos de retorno de E_)  
 Não é possível obter o identificador para o evento de notificação de inicialização.  
  
## <a name="remarks"></a>Comentários  
 No sistema operacional Windows, o `debuggeePID` é mapeado para um identificador de processo do sistema operacional.  
  
 O evento é sinalizado antes que qualquer código gerenciado seja executado pelo CLR que sinalizou o evento.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** dbgshim. h  
  
 **Biblioteca:** dbgshim. dll  
  
 **Versões do .NET Framework:** 3,5 SP1
