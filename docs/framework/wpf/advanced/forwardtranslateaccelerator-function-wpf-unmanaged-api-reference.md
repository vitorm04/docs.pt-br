---
title: Função ForwardTranslateAccelerator – referência de API não gerenciada do WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ForwardTranslateAccelerator
api_location:
- PresentationHost_v0400.dll
ms.assetid: fff47a86-9d9f-4176-9530-10e1876e393f
ms.openlocfilehash: f6e8208ffe2c186234f30f31e346ca6b1d0be4c0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747042"
---
# <a name="forwardtranslateaccelerator-function-wpf-unmanaged-api-reference"></a>Função ForwardTranslateAccelerator (referência de API não gerenciada do WPF)
Esta API dá suporte à infraestrutura do Windows Presentation Foundation (WPF) e não se destina a ser usada diretamente do seu código.  
  
 Usado pela infraestrutura do Windows Presentation Foundation (WPF) para o gerenciamento do Windows.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT ForwardTranslateAccelerator(  
   MSG* pMsg,   
   VARIANT_BOOL appUnhandled  
)  
```  
  
## <a name="parameters"></a>Parâmetros  
 pMsg  
 Um ponteiro para uma mensagem.  
  
 appUnhandled  
 `true` quando o aplicativo já tem a oportunidade de lidar com a mensagem de entrada, mas não a tratou; caso contrário, `false`.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** Consulte [.NET Framework requisitos do sistema](../../get-started/system-requirements.md).  
  
 **DLL:**  
  
 No .NET Framework 3,0 e 3,5: PresentationHostDLL. dll  
  
 No .NET Framework 4 e posterior: PresentationHost_v0400. dll  
  
 **Versão do .NET Framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Referência de API não gerenciada do WPF](wpf-unmanaged-api-reference.md)
