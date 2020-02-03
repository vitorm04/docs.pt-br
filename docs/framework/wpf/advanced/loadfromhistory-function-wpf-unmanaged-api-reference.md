---
title: Função LoadFromHistory – referência de API não gerenciada do WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- LoadFromHistory
api_location:
- PresentationHost_v0400.dll
ms.assetid: d037c062-a911-4949-b251-ccd3e48b1d17
ms.openlocfilehash: 7807e073d1f09ac6a6213aee6d86d53cc75a3c56
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76727936"
---
# <a name="loadfromhistory-function-wpf-unmanaged-api-reference"></a>Função LoadFromHistory (referência de API não gerenciada do WPF)
Esta API dá suporte à infraestrutura do Windows Presentation Foundation (WPF) e não se destina a ser usada diretamente do seu código.  
  
 Usado pela infraestrutura do Windows Presentation Foundation (WPF) para o gerenciamento do Windows.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT LoadFromHistory_export(  
        IStream* pHistoryStream,   
        IBindCtx* pBindCtx  
)  
```  
  
## <a name="parameters"></a>Parâmetros  
 pHistoryStream  
 Um ponteiro para um fluxo de informações de histórico.  
  
 pBindCtx  
 Um ponteiro para um contexto de associação.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** Consulte [.NET Framework requisitos do sistema](../../get-started/system-requirements.md).  
  
 **DLL**  
  
 No .NET Framework 3,0 e 3,5: PresentationHostDLL. dll  
  
 No .NET Framework 4 e posterior: PresentationHost_v0400. dll  
  
 **Versão do .NET Framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Referência de API não gerenciada do WPF](wpf-unmanaged-api-reference.md)
