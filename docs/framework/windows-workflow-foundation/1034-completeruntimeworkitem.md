---
title: 1034 - CompleteRuntimeWorkItem
ms.date: 03/30/2017
ms.assetid: 45620011-8b04-4f87-ab5a-65b24145e17d
ms.openlocfilehash: bd49c608a8f6a6caab6975850507a00a2c0edb03
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924547"
---
# <a name="1034---completeruntimeworkitem"></a><span data-ttu-id="32bcd-102">1034 - CompleteRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="32bcd-102">1034 - CompleteRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="32bcd-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="32bcd-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="32bcd-104">ID</span><span class="sxs-lookup"><span data-stu-id="32bcd-104">ID</span></span>|<span data-ttu-id="32bcd-105">1034</span><span class="sxs-lookup"><span data-stu-id="32bcd-105">1034</span></span>|  
|<span data-ttu-id="32bcd-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="32bcd-106">Keywords</span></span>|<span data-ttu-id="32bcd-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="32bcd-107">WFRuntime</span></span>|  
|<span data-ttu-id="32bcd-108">Nível</span><span class="sxs-lookup"><span data-stu-id="32bcd-108">Level</span></span>|<span data-ttu-id="32bcd-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="32bcd-109">Verbose</span></span>|  
|<span data-ttu-id="32bcd-110">Canal</span><span class="sxs-lookup"><span data-stu-id="32bcd-110">Channel</span></span>|<span data-ttu-id="32bcd-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="32bcd-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="32bcd-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="32bcd-112">Description</span></span>  
 <span data-ttu-id="32bcd-113">Indica que um RuntimeWorkItem terminado.</span><span class="sxs-lookup"><span data-stu-id="32bcd-113">Indicates a RuntimeWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="32bcd-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="32bcd-114">Message</span></span>  
 <span data-ttu-id="32bcd-115">Um item de trabalho de tempo de execução concluiu para atividades “%1 ", DisplayName: “%2", InstanceId: “%3".</span><span class="sxs-lookup"><span data-stu-id="32bcd-115">A runtime work item has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="32bcd-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="32bcd-116">Details</span></span>  
  
|<span data-ttu-id="32bcd-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="32bcd-117">Data Item Name</span></span>|<span data-ttu-id="32bcd-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="32bcd-118">Data Item Type</span></span>|<span data-ttu-id="32bcd-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="32bcd-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="32bcd-120">Atividade</span><span class="sxs-lookup"><span data-stu-id="32bcd-120">Activity</span></span>|<span data-ttu-id="32bcd-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="32bcd-121">xs:string</span></span>|<span data-ttu-id="32bcd-122">O nome do tipo de atividade.</span><span class="sxs-lookup"><span data-stu-id="32bcd-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="32bcd-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="32bcd-123">DisplayName</span></span>|<span data-ttu-id="32bcd-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="32bcd-124">xs:string</span></span>|<span data-ttu-id="32bcd-125">O nome para exibição de atividade.</span><span class="sxs-lookup"><span data-stu-id="32bcd-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="32bcd-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="32bcd-126">InstanceId</span></span>|<span data-ttu-id="32bcd-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="32bcd-127">xs:string</span></span>|<span data-ttu-id="32bcd-128">A identificação de instância de atividade.</span><span class="sxs-lookup"><span data-stu-id="32bcd-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="32bcd-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="32bcd-129">AppDomain</span></span>|<span data-ttu-id="32bcd-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="32bcd-130">xs:string</span></span>|<span data-ttu-id="32bcd-131">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="32bcd-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
