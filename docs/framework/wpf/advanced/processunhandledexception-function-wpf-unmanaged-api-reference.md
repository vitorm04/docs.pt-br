---
title: "Função ProcessUnhandledException (referência de API não gerenciada WPF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
api_name: ProcessUnhandledException
api_location: PresentationHost_v0400.dll
ms.assetid: 495ce5f6-bb4d-4b30-807a-c3c35f1ca95c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9bc43b42c2e671e13076ba87ce72e054bd65d107
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="processunhandledexception-function-wpf-unmanaged-api-reference"></a>Função ProcessUnhandledException (referência de API não gerenciada WPF)
Essa API dá suporte à infraestrutura do Windows Presentation Foundation (WPF) e não se destina a ser usado diretamente no seu código.  
  
 Usado pela infraestrutura do Windows Presentation Foundation (WPF) para manipulação de exceção.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
void __stdcall ProcessUnhandledException(  
   __in_ecount(1) BSTR errorMsg  
)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 errorMsg  
 A mensagem de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema do .NET Framework](../../../../docs/framework/get-started/system-requirements.md).  
  
 **DLL:**  
  
 No .NET Framework 3.0 e 3.5: PresentationHostDLL.dll  
  
 No .NET Framework 4 e posterior: PresentationHost_v0400.dll  
  
 **Versão do .NET framework:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de API não gerenciada do WPF](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
