---
title: Instâncias
ms.date: 03/30/2017
ms.assetid: c8cf3460-0ca1-4411-8262-e9ecaf7f0a31
ms.openlocfilehash: 668cfb3026b9ab7259665f5e53873a512b1e2238
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916390"
---
# <a name="instances"></a>Instâncias
Nome do contador: instâncias.  
  
## <a name="description"></a>Descrição  
 Número de contextos de instância que o serviço contém no momento.  
  
 Na maioria das vezes, o número de contextos de instância é idêntico ao número de instâncias. No entanto, os seguintes cenários são a exceção a essa regra.  
  
- Chama um método de serviço a <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> método explicitamente.  
  
- Um <xref:System.ServiceModel.ReleaseInstanceMode> é aplicado a um <xref:System.ServiceModel.OperationBehaviorAttribute> instância.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.OperationBehaviorAttribute>
