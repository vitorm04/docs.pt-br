---
title: "Função CreateIDispatchSTAForwarder (referência de API não gerenciada WPF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
api_name: CreateIDispatchSTAForwarder
api_location: PresentationHost_v0400.dll
ms.assetid: 57a02dfa-f091-4ace-9c06-1f4ab52b3527
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5139784fdc067c09d032c0bf37114e0eb1caac33
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="createidispatchstaforwarder-function-wpf-unmanaged-api-reference"></a>Função CreateIDispatchSTAForwarder (referência de API não gerenciada WPF)
Essa API dá suporte à infraestrutura do Windows Presentation Foundation (WPF) e não se destina a ser usado diretamente no seu código.  
  
 Usado pela infraestrutura do Windows Presentation Foundation (WPF) para gerenciamento de thread e windows.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CreateIDispatchSTAForwarder(  
   __in IDispatch *pDispatchDelegate,   
   __deref_out IDispatch **ppForwarder  
)  
```  
  
#### <a name="parameters"></a>Parâmetros  
  
## <a name="property-valuereturn-value"></a>Valor da propriedade/valor de retorno  
 pDispatchDelegate  
 Um ponteiro para um `IDispatch` interface.  
  
 ppForwarder  
 Um ponteiro para o endereço de um `IDispatch` interface.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema do .NET Framework](../../../../docs/framework/get-started/system-requirements.md).  
  
 **DLL:**  
  
 No .NET Framework 3.0 e 3.5: PresentationHostDLL.dll  
  
 No .NET Framework 4 e posterior: PresentationHost_v0400.dll  
  
 **Versão do .NET framework:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de API não gerenciada do WPF](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
