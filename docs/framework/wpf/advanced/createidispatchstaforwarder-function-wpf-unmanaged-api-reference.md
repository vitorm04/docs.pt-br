---
title: Função CreateIDispatchSTAForwarder - Referência de API não gerenciada do WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CreateIDispatchSTAForwarder
api_location:
- PresentationHost_v0400.dll
ms.assetid: 57a02dfa-f091-4ace-9c06-1f4ab52b3527
ms.openlocfilehash: e151ffa6eb5f1dc7479c699e0d7f9f3f57833ebd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174713"
---
# <a name="createidispatchstaforwarder-function-wpf-unmanaged-api-reference"></a>Função CreateIDispatchSTAForwarder (referência de API não gerenciada WPF)
Esta API suporta a infra-estrutura do Windows Presentation Foundation (WPF) e não se destina a ser usada diretamente do seu código.  
  
 Usado pela infra-estrutura do Windows Presentation Foundation (WPF) para gerenciamento de threads e janelas.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CreateIDispatchSTAForwarder(  
   __in IDispatch *pDispatchDelegate,
   __deref_out IDispatch **ppForwarder  
)  
```  
  
## <a name="parameters"></a>parâmetros  
  
## <a name="property-valuereturn-value"></a>Valor da propriedade/Valor do retorno  
 pDispatchDelegate  
 Um ponteiro `IDispatch` para uma interface.  
  
 ppForwarder  
 Um ponteiro para o `IDispatch` endereço de uma interface.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Consulte [os requisitos do sistema de estrutura .NET](../../get-started/system-requirements.md).  
  
 **Dll:**  
  
 No quadro .NET 3.0 e 3.5: PresentationHostDLL.dll  
  
 No Quadro .NET 4 e posteriores: PresentationHost_v0400.dll  
  
 **.NET Framework Version:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Referência de API não gerenciada do WPF](wpf-unmanaged-api-reference.md)
