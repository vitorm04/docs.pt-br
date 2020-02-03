---
title: Função SaveToHistory – referência de API não gerenciada do WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- SaveToHistory
api_location:
- PresentationHost_v0400.dll
ms.assetid: 6dd101a3-44ad-4143-b228-772156f9b8ff
ms.openlocfilehash: 7337e5dc23a3dce5de8270902bce228c49bc6edb
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731754"
---
# <a name="savetohistory-function-wpf-unmanaged-api-reference"></a>Função SaveToHistory (referência de API não gerenciada do WPF)
Esta API dá suporte à infraestrutura do Windows Presentation Foundation (WPF) e não se destina a ser usada diretamente do seu código.  
  
 Usado pela infraestrutura do Windows Presentation Foundation (WPF) para o gerenciamento do Windows.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SaveToHistory(  
   __in_ecount(1) IStream* pHistoryStream  
)  
```  
  
## <a name="parameters"></a>Parâmetros  
 pHistoryStream  
 Um ponteiro para o fluxo de histórico.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** Consulte [.NET Framework requisitos do sistema](../../get-started/system-requirements.md).  
  
 **DLL**  
  
 No .NET Framework 3,0 e 3,5: PresentationHostDLL. dll  
  
 No .NET Framework 4 e posterior: PresentationHost_v0400. dll  
  
 **Versão do .NET Framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Referência de API não gerenciada do WPF](wpf-unmanaged-api-reference.md)
