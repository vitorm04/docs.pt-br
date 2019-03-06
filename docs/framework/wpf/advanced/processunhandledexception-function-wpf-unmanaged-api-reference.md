---
title: Função ProcessUnhandledException (referência de API não gerenciada WPF)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ProcessUnhandledException
api_location:
- PresentationHost_v0400.dll
ms.assetid: 495ce5f6-bb4d-4b30-807a-c3c35f1ca95c
ms.openlocfilehash: c3997415c19483a69e66d8fe68c6ec9241f7ad0d
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57356189"
---
# <a name="processunhandledexception-function-wpf-unmanaged-api-reference"></a>Função ProcessUnhandledException (referência de API não gerenciada WPF)
Essa API dá suporte à infraestrutura do Windows Presentation Foundation (WPF) e não se destina a ser usado diretamente do seu código.  
  
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
 **Plataformas:** Ver [requisitos de sistema do .NET Framework](../../get-started/system-requirements.md).  
  
 **DLL:**  
  
 No .NET Framework 3.0 e 3.5: PresentationHostDLL.dll  
  
 No .NET Framework 4 e posterior: PresentationHost_v0400.dll  
  
 **Versão do .NET framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Referência de API não gerenciada do WPF](wpf-unmanaged-api-reference.md)
