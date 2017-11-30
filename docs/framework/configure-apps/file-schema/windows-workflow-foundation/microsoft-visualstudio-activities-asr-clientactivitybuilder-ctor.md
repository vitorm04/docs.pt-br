---
title: Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder... construtor
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
api_name: Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor
api_location: Microsoft.VisualStudio.Activities.dll
api_type: Assembly
ms.assetid: 6b44b13c-7a23-4df2-8f9f-45e2b1430002
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7b73274a09ae748cdf1ee33c885de86b1f52c105
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="microsoftvisualstudioactivitiesasrclientactivitybuilderctor"></a><span data-ttu-id="b9e94-102">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder... construtor</span><span class="sxs-lookup"><span data-stu-id="b9e94-102">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor</span></span>
<span data-ttu-id="b9e94-103">Cria uma instância de [Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md) classe.</span><span class="sxs-lookup"><span data-stu-id="b9e94-103">Creates an instance of the [Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md) class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9e94-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b9e94-104">Syntax</span></span>  
  
```csharp  
public ClientActivityBuilder(OperationDescription operationDescription, string configurationName, string proxyNamespace);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b9e94-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b9e94-105">Parameters</span></span>  
  
## <a name="parameter-values"></a><span data-ttu-id="b9e94-106">Valores de parâmetro</span><span class="sxs-lookup"><span data-stu-id="b9e94-106">Parameter Values</span></span>  
 <span data-ttu-id="b9e94-107">*operationDescription*</span><span class="sxs-lookup"><span data-stu-id="b9e94-107">*operationDescription*</span></span>  
  
 <span data-ttu-id="b9e94-108">Descreve a operação a ser executada na atividade de fluxo de trabalho deve ser gerada, incluindo o nome da operação, tipo de retorno e informações de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="b9e94-108">Describes the operation to be performed in the workflow activity that is to be generated, including the operation name, return type, and parameter information.</span></span> <span data-ttu-id="b9e94-109">O valor desse parâmetro deve não ser **nulo**.</span><span class="sxs-lookup"><span data-stu-id="b9e94-109">The value of this parameter must not be **null**.</span></span> <span data-ttu-id="b9e94-110">Ele deve descrever uma operação síncrona que usa um contrato de mensagem e usa um argumento com uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="b9e94-110">It should describe a synchronous operation which uses a message contract and takes an argument with one message.</span></span> <span data-ttu-id="b9e94-111">Se essas condições não forem atendidas, o resultado de tempo de execução do uso do construtor e os outros métodos dessa classe é indefinido.</span><span class="sxs-lookup"><span data-stu-id="b9e94-111">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
 <span data-ttu-id="b9e94-112">*configurationName*</span><span class="sxs-lookup"><span data-stu-id="b9e94-112">*configurationName*</span></span>  
  
 <span data-ttu-id="b9e94-113">Especifica o nome da configuração de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="b9e94-113">Specifies the endpoint configuration name.</span></span> <span data-ttu-id="b9e94-114">O valor desse parâmetro deve não ser **nulo** ou vazio.</span><span class="sxs-lookup"><span data-stu-id="b9e94-114">The value of this parameter must not be either **null** or empty.</span></span> <span data-ttu-id="b9e94-115">Se essas condições não forem atendidas, o resultado de tempo de execução do uso do construtor e os outros métodos dessa classe é indefinido.</span><span class="sxs-lookup"><span data-stu-id="b9e94-115">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
 <span data-ttu-id="b9e94-116">*proxyNamespace*</span><span class="sxs-lookup"><span data-stu-id="b9e94-116">*proxyNamespace*</span></span>  
  
 <span data-ttu-id="b9e94-117">Especifica o namespace de serviço para a operação.</span><span class="sxs-lookup"><span data-stu-id="b9e94-117">Specifies the service namespace for the operation.</span></span> <span data-ttu-id="b9e94-118">O valor desse parâmetro deve não ser **nulo** ou vazio.</span><span class="sxs-lookup"><span data-stu-id="b9e94-118">The value of this parameter must not be either **null** or empty.</span></span> <span data-ttu-id="b9e94-119">Se essas condições não forem atendidas, o resultado de tempo de execução do uso do construtor e os outros métodos dessa classe é indefinido.</span><span class="sxs-lookup"><span data-stu-id="b9e94-119">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9e94-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b9e94-120">See Also</span></span>  
 [<span data-ttu-id="b9e94-121">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder</span><span class="sxs-lookup"><span data-stu-id="b9e94-121">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder</span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md)
