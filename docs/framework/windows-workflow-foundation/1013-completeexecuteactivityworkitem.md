---
title: 1013 - CompleteExecuteActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 31fc57b3-ef2f-48f0-a5de-b4e2c5c9ded7
ms.openlocfilehash: c1ff62bb4143bb798ea7adb7c3fee539ef68bc37
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61925184"
---
# <a name="1013---completeexecuteactivityworkitem"></a><span data-ttu-id="4bae0-102">1013 - CompleteExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="4bae0-102">1013 - CompleteExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="4bae0-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="4bae0-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4bae0-104">ID</span><span class="sxs-lookup"><span data-stu-id="4bae0-104">ID</span></span>|<span data-ttu-id="4bae0-105">1013</span><span class="sxs-lookup"><span data-stu-id="4bae0-105">1013</span></span>|  
|<span data-ttu-id="4bae0-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="4bae0-106">Keywords</span></span>|<span data-ttu-id="4bae0-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="4bae0-107">WFRuntime</span></span>|  
|<span data-ttu-id="4bae0-108">Nível</span><span class="sxs-lookup"><span data-stu-id="4bae0-108">Level</span></span>|<span data-ttu-id="4bae0-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="4bae0-109">Verbose</span></span>|  
|<span data-ttu-id="4bae0-110">Canal</span><span class="sxs-lookup"><span data-stu-id="4bae0-110">Channel</span></span>|<span data-ttu-id="4bae0-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="4bae0-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4bae0-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="4bae0-112">Description</span></span>  
 <span data-ttu-id="4bae0-113">Indica que um ExecuteActivityWorkItem concluiu</span><span class="sxs-lookup"><span data-stu-id="4bae0-113">Indicates an ExecuteActivityWorkItem has completed</span></span>  
  
## <a name="message"></a><span data-ttu-id="4bae0-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="4bae0-114">Message</span></span>  
 <span data-ttu-id="4bae0-115">Um ExecuteActivityWorkItem concluiu para atividades “%1 ", DisplayName: “%2", InstanceId: “%3".</span><span class="sxs-lookup"><span data-stu-id="4bae0-115">An ExecuteActivityWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="4bae0-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="4bae0-116">Details</span></span>  
  
|<span data-ttu-id="4bae0-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="4bae0-117">Data Item Name</span></span>|<span data-ttu-id="4bae0-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="4bae0-118">Data Item Type</span></span>|<span data-ttu-id="4bae0-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="4bae0-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4bae0-120">Atividade</span><span class="sxs-lookup"><span data-stu-id="4bae0-120">Activity</span></span>|<span data-ttu-id="4bae0-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="4bae0-121">xs:string</span></span>|<span data-ttu-id="4bae0-122">O nome do tipo de atividade.</span><span class="sxs-lookup"><span data-stu-id="4bae0-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="4bae0-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="4bae0-123">DisplayName</span></span>|<span data-ttu-id="4bae0-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="4bae0-124">xs:string</span></span>|<span data-ttu-id="4bae0-125">O nome para exibição de atividade.</span><span class="sxs-lookup"><span data-stu-id="4bae0-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="4bae0-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="4bae0-126">InstanceId</span></span>|<span data-ttu-id="4bae0-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="4bae0-127">xs:string</span></span>|<span data-ttu-id="4bae0-128">A identificação de instância de atividade.</span><span class="sxs-lookup"><span data-stu-id="4bae0-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="4bae0-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="4bae0-129">AppDomain</span></span>|<span data-ttu-id="4bae0-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="4bae0-130">xs:string</span></span>|<span data-ttu-id="4bae0-131">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="4bae0-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
