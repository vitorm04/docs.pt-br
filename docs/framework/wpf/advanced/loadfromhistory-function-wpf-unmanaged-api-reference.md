---
title: Função LoadFromHistory - Referência de API não gerenciada do WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- LoadFromHistory
api_location:
- PresentationHost_v0400.dll
ms.assetid: d037c062-a911-4949-b251-ccd3e48b1d17
ms.openlocfilehash: be9b8658614e678b4370044a753554859d230fed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141569"
---
# <a name="loadfromhistory-function-wpf-unmanaged-api-reference"></a>Função LoadFromHistory (referência de API não gerenciada WPF)
Esta API suporta a infra-estrutura do Windows Presentation Foundation (WPF) e não se destina a ser usada diretamente do seu código.  
  
 Usado pela infra-estrutura do Windows Presentation Foundation (WPF) para gerenciamento de janelas.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT LoadFromHistory_export(  
        IStream* pHistoryStream,
        IBindCtx* pBindCtx  
)  
```  
  
## <a name="parameters"></a>parâmetros  
 pHistoryStream  
 Um ponteiro para um fluxo de informações históricas.  
  
 pBindCtx  
 Um ponteiro para um contexto de ligação.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Consulte [os requisitos do sistema de estrutura .NET](../../get-started/system-requirements.md).  
  
 **Dll:**  
  
 No quadro .NET 3.0 e 3.5: PresentationHostDLL.dll  
  
 No Quadro .NET 4 e posteriores: PresentationHost_v0400.dll  
  
 **.NET Framework Version:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Referência de API não gerenciada do WPF](wpf-unmanaged-api-reference.md)
