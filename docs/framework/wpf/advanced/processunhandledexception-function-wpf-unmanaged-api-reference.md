---
title: Função ProcessUnhandledException – referência de API não gerenciada do WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ProcessUnhandledException
api_location:
- PresentationHost_v0400.dll
ms.assetid: 495ce5f6-bb4d-4b30-807a-c3c35f1ca95c
ms.openlocfilehash: 757e5ac3aa2dc4c87b210b026998523bd82045c1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743925"
---
# <a name="processunhandledexception-function-wpf-unmanaged-api-reference"></a>Função ProcessUnhandledException (referência de API não gerenciada do WPF)
Esta API dá suporte à infraestrutura do Windows Presentation Foundation (WPF) e não se destina a ser usada diretamente do seu código.  
  
 Usado pela infraestrutura do Windows Presentation Foundation (WPF) para manipulação de exceção.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
void __stdcall ProcessUnhandledException(  
   __in_ecount(1) BSTR errorMsg  
)  
```  
  
## <a name="parameters"></a>Parâmetros  
 errorMsg  
 A mensagem de erro.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** Consulte [.NET Framework requisitos do sistema](../../get-started/system-requirements.md).  
  
 **DLL**  
  
 No .NET Framework 3,0 e 3,5: PresentationHostDLL. dll  
  
 No .NET Framework 4 e posterior: PresentationHost_v0400. dll  
  
 **Versão do .NET Framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Referência de API não gerenciada do WPF](wpf-unmanaged-api-reference.md)
