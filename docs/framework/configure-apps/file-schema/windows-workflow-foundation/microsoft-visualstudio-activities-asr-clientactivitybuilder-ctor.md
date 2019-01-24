---
title: Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor
ms.date: 03/30/2017
ms.topic: reference
api_name:
- Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor
api_location:
- Microsoft.VisualStudio.Activities.dll
api_type:
- Assembly
ms.assetid: 6b44b13c-7a23-4df2-8f9f-45e2b1430002
ms.openlocfilehash: b63f8917d7af21c165a16bd45a83e774bcec6e1c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54551599"
---
# <a name="microsoftvisualstudioactivitiesasrclientactivitybuilderctor"></a>Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor
Cria uma instância de [Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md) classe.  
  
## <a name="syntax"></a>Sintaxe  
  
```csharp  
public ClientActivityBuilder(OperationDescription operationDescription, string configurationName, string proxyNamespace);  
```  
  
#### <a name="parameters"></a>Parâmetros  
  
## <a name="parameter-values"></a>Valores de parâmetro  
 *operationDescription*  
  
 Descreve a operação a ser executada na atividade de fluxo de trabalho deve ser gerada, incluindo o nome da operação, tipo de retorno e informações de parâmetro. O valor desse parâmetro não deve ser **nulo**. Ele deve descrever uma operação síncrona que usa um contrato de mensagem e usa um argumento com uma mensagem. Se essas condições não forem atendidas, o resultado de tempo de execução do uso do construtor e os outros métodos dessa classe é indefinido.  
  
 *configurationName*  
  
 Especifica o nome da configuração de ponto de extremidade. O valor desse parâmetro não deve ser **nulo** ou está vazio. Se essas condições não forem atendidas, o resultado de tempo de execução do uso do construtor e os outros métodos dessa classe é indefinido.  
  
 *proxyNamespace*  
  
 Especifica o namespace de serviço para a operação. O valor desse parâmetro não deve ser **nulo** ou está vazio. Se essas condições não forem atendidas, o resultado de tempo de execução do uso do construtor e os outros métodos dessa classe é indefinido.  
  
## <a name="see-also"></a>Consulte também
- [Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md)
