---
title: 1033 - StartRuntimeWorkItem
ms.date: 03/30/2017
ms.assetid: 172b5346-9f3b-46ae-bc06-39872022376a
ms.openlocfilehash: c7192ed7c5fb43fe6f65b47b8cebde3cf4aed32c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510060"
---
# <a name="1033---startruntimeworkitem"></a><span data-ttu-id="3cab3-102">1033 - StartRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="3cab3-102">1033 - StartRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="3cab3-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="3cab3-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3cab3-104">ID</span><span class="sxs-lookup"><span data-stu-id="3cab3-104">ID</span></span>|<span data-ttu-id="3cab3-105">1033</span><span class="sxs-lookup"><span data-stu-id="3cab3-105">1033</span></span>|  
|<span data-ttu-id="3cab3-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="3cab3-106">Keywords</span></span>|<span data-ttu-id="3cab3-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="3cab3-107">WFRuntime</span></span>|  
|<span data-ttu-id="3cab3-108">Nível</span><span class="sxs-lookup"><span data-stu-id="3cab3-108">Level</span></span>|<span data-ttu-id="3cab3-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="3cab3-109">Verbose</span></span>|  
|<span data-ttu-id="3cab3-110">Canal</span><span class="sxs-lookup"><span data-stu-id="3cab3-110">Channel</span></span>|<span data-ttu-id="3cab3-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="3cab3-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3cab3-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="3cab3-112">Description</span></span>  
 <span data-ttu-id="3cab3-113">Indica que um RuntimeWorkItem está sendo a execução.</span><span class="sxs-lookup"><span data-stu-id="3cab3-113">Indicates a RuntimeWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3cab3-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="3cab3-114">Message</span></span>  
 <span data-ttu-id="3cab3-115">Iniciar a execução de um item de trabalho de tempo de execução para atividades “%1 ", DisplayName: “%2", InstanceId: “%3".</span><span class="sxs-lookup"><span data-stu-id="3cab3-115">Starting execution of a runtime work item for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3cab3-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="3cab3-116">Details</span></span>  
  
|<span data-ttu-id="3cab3-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="3cab3-117">Data Item Name</span></span>|<span data-ttu-id="3cab3-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="3cab3-118">Data Item Type</span></span>|<span data-ttu-id="3cab3-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="3cab3-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3cab3-120">Atividade</span><span class="sxs-lookup"><span data-stu-id="3cab3-120">Activity</span></span>|<span data-ttu-id="3cab3-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="3cab3-121">xs:string</span></span>|<span data-ttu-id="3cab3-122">O nome do tipo de atividade.</span><span class="sxs-lookup"><span data-stu-id="3cab3-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="3cab3-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="3cab3-123">DisplayName</span></span>|<span data-ttu-id="3cab3-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="3cab3-124">xs:string</span></span>|<span data-ttu-id="3cab3-125">O nome para exibição de atividade.</span><span class="sxs-lookup"><span data-stu-id="3cab3-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="3cab3-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="3cab3-126">InstanceId</span></span>|<span data-ttu-id="3cab3-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="3cab3-127">xs:string</span></span>|<span data-ttu-id="3cab3-128">A identificação de instância de atividade.</span><span class="sxs-lookup"><span data-stu-id="3cab3-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="3cab3-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="3cab3-129">AppDomain</span></span>|<span data-ttu-id="3cab3-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="3cab3-130">xs:string</span></span>|<span data-ttu-id="3cab3-131">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="3cab3-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
