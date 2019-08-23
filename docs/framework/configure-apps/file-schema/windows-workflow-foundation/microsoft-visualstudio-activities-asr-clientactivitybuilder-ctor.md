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
ms.openlocfilehash: 99f2eb9447bdf43cb57cfe86f35d2c09044ed470
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947621"
---
# <a name="microsoftvisualstudioactivitiesasrclientactivitybuilderctor"></a><span data-ttu-id="5efb8-102">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor</span><span class="sxs-lookup"><span data-stu-id="5efb8-102">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor</span></span>
<span data-ttu-id="5efb8-103">Cria uma instância da classe [Microsoft. VisualStudio. Activities. ASR. ClientActivityBuilder](microsoft-visualstudio-activities-asr-clientactivitybuilder.md) .</span><span class="sxs-lookup"><span data-stu-id="5efb8-103">Creates an instance of the [Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](microsoft-visualstudio-activities-asr-clientactivitybuilder.md) class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5efb8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5efb8-104">Syntax</span></span>  
  
```csharp  
public ClientActivityBuilder(OperationDescription operationDescription, string configurationName, string proxyNamespace);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5efb8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5efb8-105">Parameters</span></span>  
  
## <a name="parameter-values"></a><span data-ttu-id="5efb8-106">Valores de parâmetro</span><span class="sxs-lookup"><span data-stu-id="5efb8-106">Parameter Values</span></span>  
 <span data-ttu-id="5efb8-107">*operationDescription*</span><span class="sxs-lookup"><span data-stu-id="5efb8-107">*operationDescription*</span></span>  
  
 <span data-ttu-id="5efb8-108">Descreve a operação a ser executada na atividade de fluxo de trabalho deve ser gerada, incluindo o nome da operação, tipo de retorno e informações de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="5efb8-108">Describes the operation to be performed in the workflow activity that is to be generated, including the operation name, return type, and parameter information.</span></span> <span data-ttu-id="5efb8-109">O valor desse parâmetro não deve ser **nulo**.</span><span class="sxs-lookup"><span data-stu-id="5efb8-109">The value of this parameter must not be **null**.</span></span> <span data-ttu-id="5efb8-110">Ele deve descrever uma operação síncrona que usa um contrato de mensagem e usa um argumento com uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="5efb8-110">It should describe a synchronous operation which uses a message contract and takes an argument with one message.</span></span> <span data-ttu-id="5efb8-111">Se essas condições não forem atendidas, o resultado de tempo de execução do uso do construtor e os outros métodos dessa classe é indefinido.</span><span class="sxs-lookup"><span data-stu-id="5efb8-111">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
 <span data-ttu-id="5efb8-112">*configurationName*</span><span class="sxs-lookup"><span data-stu-id="5efb8-112">*configurationName*</span></span>  
  
 <span data-ttu-id="5efb8-113">Especifica o nome da configuração de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="5efb8-113">Specifies the endpoint configuration name.</span></span> <span data-ttu-id="5efb8-114">O valor desse parâmetro não deve ser **nulo** ou vazio.</span><span class="sxs-lookup"><span data-stu-id="5efb8-114">The value of this parameter must not be either **null** or empty.</span></span> <span data-ttu-id="5efb8-115">Se essas condições não forem atendidas, o resultado de tempo de execução do uso do construtor e os outros métodos dessa classe é indefinido.</span><span class="sxs-lookup"><span data-stu-id="5efb8-115">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
 <span data-ttu-id="5efb8-116">*proxyNamespace*</span><span class="sxs-lookup"><span data-stu-id="5efb8-116">*proxyNamespace*</span></span>  
  
 <span data-ttu-id="5efb8-117">Especifica o namespace de serviço para a operação.</span><span class="sxs-lookup"><span data-stu-id="5efb8-117">Specifies the service namespace for the operation.</span></span> <span data-ttu-id="5efb8-118">O valor desse parâmetro não deve ser **nulo** ou vazio.</span><span class="sxs-lookup"><span data-stu-id="5efb8-118">The value of this parameter must not be either **null** or empty.</span></span> <span data-ttu-id="5efb8-119">Se essas condições não forem atendidas, o resultado de tempo de execução do uso do construtor e os outros métodos dessa classe é indefinido.</span><span class="sxs-lookup"><span data-stu-id="5efb8-119">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5efb8-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5efb8-120">See also</span></span>

- [<span data-ttu-id="5efb8-121">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder</span><span class="sxs-lookup"><span data-stu-id="5efb8-121">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder</span></span>](microsoft-visualstudio-activities-asr-clientactivitybuilder.md)
