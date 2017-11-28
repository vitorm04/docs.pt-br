---
title: "Função GetStartupNotificationEvent"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetStartupNotificationEvent
api_location: dbgshim.dll
api_type: COM
f1_keywords: GetStartupNotificationEvent
helpviewer_keywords:
- GetStartupNotificationEvent function
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: c94b1b61-045a-4695-bacd-0f18c5acc246
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 305350a9186c90af1e8646bc230536dcd2de47cc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="getstartupnotificationevent-function"></a>Função GetStartupNotificationEvent
Cria ou abre um identificador de evento será sinalizado após qualquer common language runtime (CLR) que está sendo carregado no processo de destino especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetStartupNotificationEvent  
    (  
    [in]  DWORD     debuggeePID,  
    [out]  HANDLE*  phStartupEvent  
    );  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `debuggeePID`  
 [in] Identificador de processo do processo de destino do qual deseja receber notificações de inicialização do CLR.  
  
 `phStartupEvent`  
 [out] Um ponteiro para um identificador que será sinalizado um CLR na inicialização.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK  
 O identificador para o evento de notificação de inicialização foi obtido com êxito.  
  
 E_INVALIDARG  
 `phStartupEvent`é nulo ou `debuggeePID` não faz referência a um processo que está sendo executado.  
  
 E_FAIL (ou outros códigos de retorno E_)  
 Não é possível obter o identificador para o evento de notificação de inicialização.  
  
## <a name="remarks"></a>Comentários  
 No sistema operacional Windows, `debuggeePID` identificador de processo é mapeado para um sistema operacional.  
  
 O evento é sinalizado antes de qualquer gerenciados código é executado pelo CLR que o evento de sinalizado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** dbgshim.h  
  
 **Biblioteca:** dbgshim.dll  
  
 **Versões do .NET framework:** 3.5 SP1
