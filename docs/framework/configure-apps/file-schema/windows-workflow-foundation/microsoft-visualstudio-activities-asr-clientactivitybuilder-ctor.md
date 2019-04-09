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
ms.openlocfilehash: 0ce9be30182f9181bcb6449529d9b9796aadbc2b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59133528"
---
# <a name="microsoftvisualstudioactivitiesasrclientactivitybuilderctor"></a><span data-ttu-id="f125c-102">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor</span><span class="sxs-lookup"><span data-stu-id="f125c-102">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor</span></span>
<span data-ttu-id="f125c-103">Cria uma instância de [Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md) classe.</span><span class="sxs-lookup"><span data-stu-id="f125c-103">Creates an instance of the [Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md) class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f125c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f125c-104">Syntax</span></span>  
  
```csharp  
public ClientActivityBuilder(OperationDescription operationDescription, string configurationName, string proxyNamespace);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f125c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f125c-105">Parameters</span></span>  
  
## <a name="parameter-values"></a><span data-ttu-id="f125c-106">Valores de parâmetro</span><span class="sxs-lookup"><span data-stu-id="f125c-106">Parameter Values</span></span>  
 *<span data-ttu-id="f125c-107">operationDescription</span><span class="sxs-lookup"><span data-stu-id="f125c-107">operationDescription</span></span>*  
  
 <span data-ttu-id="f125c-108">Descreve a operação a ser executada na atividade de fluxo de trabalho deve ser gerada, incluindo o nome da operação, tipo de retorno e informações de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="f125c-108">Describes the operation to be performed in the workflow activity that is to be generated, including the operation name, return type, and parameter information.</span></span> <span data-ttu-id="f125c-109">O valor desse parâmetro não deve ser **nulo**.</span><span class="sxs-lookup"><span data-stu-id="f125c-109">The value of this parameter must not be **null**.</span></span> <span data-ttu-id="f125c-110">Ele deve descrever uma operação síncrona que usa um contrato de mensagem e usa um argumento com uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="f125c-110">It should describe a synchronous operation which uses a message contract and takes an argument with one message.</span></span> <span data-ttu-id="f125c-111">Se essas condições não forem atendidas, o resultado de tempo de execução do uso do construtor e os outros métodos dessa classe é indefinido.</span><span class="sxs-lookup"><span data-stu-id="f125c-111">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
 *<span data-ttu-id="f125c-112">configurationName</span><span class="sxs-lookup"><span data-stu-id="f125c-112">configurationName</span></span>*  
  
 <span data-ttu-id="f125c-113">Especifica o nome da configuração de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="f125c-113">Specifies the endpoint configuration name.</span></span> <span data-ttu-id="f125c-114">O valor desse parâmetro não deve ser **nulo** ou está vazio.</span><span class="sxs-lookup"><span data-stu-id="f125c-114">The value of this parameter must not be either **null** or empty.</span></span> <span data-ttu-id="f125c-115">Se essas condições não forem atendidas, o resultado de tempo de execução do uso do construtor e os outros métodos dessa classe é indefinido.</span><span class="sxs-lookup"><span data-stu-id="f125c-115">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
 *<span data-ttu-id="f125c-116">proxyNamespace</span><span class="sxs-lookup"><span data-stu-id="f125c-116">proxyNamespace</span></span>*  
  
 <span data-ttu-id="f125c-117">Especifica o namespace de serviço para a operação.</span><span class="sxs-lookup"><span data-stu-id="f125c-117">Specifies the service namespace for the operation.</span></span> <span data-ttu-id="f125c-118">O valor desse parâmetro não deve ser **nulo** ou está vazio.</span><span class="sxs-lookup"><span data-stu-id="f125c-118">The value of this parameter must not be either **null** or empty.</span></span> <span data-ttu-id="f125c-119">Se essas condições não forem atendidas, o resultado de tempo de execução do uso do construtor e os outros métodos dessa classe é indefinido.</span><span class="sxs-lookup"><span data-stu-id="f125c-119">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f125c-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f125c-120">See also</span></span>

- [<span data-ttu-id="f125c-121">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder</span><span class="sxs-lookup"><span data-stu-id="f125c-121">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder</span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md)
