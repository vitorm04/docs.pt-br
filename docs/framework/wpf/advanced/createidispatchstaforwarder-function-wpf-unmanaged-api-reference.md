---
title: Função CreateIDispatchSTAForwarder – referência de API não gerenciada do WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CreateIDispatchSTAForwarder
api_location:
- PresentationHost_v0400.dll
ms.assetid: 57a02dfa-f091-4ace-9c06-1f4ab52b3527
ms.openlocfilehash: 67f2542733fb9c6af197c99ede2bd097ce876b5d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738034"
---
# <a name="createidispatchstaforwarder-function-wpf-unmanaged-api-reference"></a>Função CreateIDispatchSTAForwarder (referência de API não gerenciada do WPF)
Esta API dá suporte à infraestrutura do Windows Presentation Foundation (WPF) e não se destina a ser usada diretamente do seu código.  
  
 Usado pela infraestrutura de Windows Presentation Foundation (WPF) para gerenciamento de threads e do Windows.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CreateIDispatchSTAForwarder(  
   __in IDispatch *pDispatchDelegate,   
   __deref_out IDispatch **ppForwarder  
)  
```  
  
## <a name="parameters"></a>Parâmetros  
  
## <a name="property-valuereturn-value"></a>Valor da propriedade/Valor do retorno  
 pDispatchDelegate  
 Um ponteiro para uma interface `IDispatch`.  
  
 ppForwarder  
 Um ponteiro para o endereço de uma interface de `IDispatch`.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** Consulte [.NET Framework requisitos do sistema](../../get-started/system-requirements.md).  
  
 **DLL**  
  
 No .NET Framework 3,0 e 3,5: PresentationHostDLL. dll  
  
 No .NET Framework 4 e posterior: PresentationHost_v0400. dll  
  
 **Versão do .NET Framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Referência de API não gerenciada do WPF](wpf-unmanaged-api-reference.md)
