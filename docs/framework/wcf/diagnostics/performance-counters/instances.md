---
title: Instâncias
ms.date: 03/30/2017
ms.assetid: c8cf3460-0ca1-4411-8262-e9ecaf7f0a31
ms.openlocfilehash: 1b2801b5df3a5d2ca6d7fd03299ecdf4b7df426a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54520250"
---
# <a name="instances"></a>Instâncias
Nome do contador: instâncias.  
  
## <a name="description"></a>Descrição  
 Número de contextos de instância que o serviço contém no momento.  
  
 Na maioria das vezes, o número de contextos de instância é idêntico ao número de instâncias. No entanto, os seguintes cenários são a exceção a essa regra.  
  
-   Chama um método de serviço a <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> método explicitamente.  
  
-   Um <xref:System.ServiceModel.ReleaseInstanceMode> é aplicado a um <xref:System.ServiceModel.OperationBehaviorAttribute> instância.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.ServiceModel.OperationBehaviorAttribute>
