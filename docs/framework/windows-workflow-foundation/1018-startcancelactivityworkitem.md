---
title: 1018 - StartCancelActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 68b4fa1d-eee6-4a2a-8c16-7e9d89f08ab9
ms.openlocfilehash: 8d7045b0a7f31ecfd5dd90f319192bd202804353
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510647"
---
# <a name="1018---startcancelactivityworkitem"></a><span data-ttu-id="54c77-102">1018 - StartCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="54c77-102">1018 - StartCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="54c77-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="54c77-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="54c77-104">ID</span><span class="sxs-lookup"><span data-stu-id="54c77-104">ID</span></span>|<span data-ttu-id="54c77-105">1018</span><span class="sxs-lookup"><span data-stu-id="54c77-105">1018</span></span>|  
|<span data-ttu-id="54c77-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="54c77-106">Keywords</span></span>|<span data-ttu-id="54c77-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="54c77-107">WFRuntime</span></span>|  
|<span data-ttu-id="54c77-108">Nível</span><span class="sxs-lookup"><span data-stu-id="54c77-108">Level</span></span>|<span data-ttu-id="54c77-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="54c77-109">Verbose</span></span>|  
|<span data-ttu-id="54c77-110">Canal</span><span class="sxs-lookup"><span data-stu-id="54c77-110">Channel</span></span>|<span data-ttu-id="54c77-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="54c77-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="54c77-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="54c77-112">Description</span></span>  
 <span data-ttu-id="54c77-113">Indica que um CancelActivityWorkItem está sendo a execução.</span><span class="sxs-lookup"><span data-stu-id="54c77-113">Indicates a CancelActivityWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="54c77-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="54c77-114">Message</span></span>  
 <span data-ttu-id="54c77-115">Iniciar a execução de um CancelActivityWorkItem para atividades “%1 ", DisplayName: “%2", InstanceId: “%3".</span><span class="sxs-lookup"><span data-stu-id="54c77-115">Starting execution of a CancelActivityWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="54c77-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="54c77-116">Details</span></span>  
  
|<span data-ttu-id="54c77-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="54c77-117">Data Item Name</span></span>|<span data-ttu-id="54c77-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="54c77-118">Data Item Type</span></span>|<span data-ttu-id="54c77-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="54c77-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="54c77-120">Atividade</span><span class="sxs-lookup"><span data-stu-id="54c77-120">Activity</span></span>|<span data-ttu-id="54c77-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="54c77-121">xs:string</span></span>|<span data-ttu-id="54c77-122">O nome do tipo de atividade.</span><span class="sxs-lookup"><span data-stu-id="54c77-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="54c77-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="54c77-123">DisplayName</span></span>|<span data-ttu-id="54c77-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="54c77-124">xs:string</span></span>|<span data-ttu-id="54c77-125">O nome para exibição de atividade.</span><span class="sxs-lookup"><span data-stu-id="54c77-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="54c77-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="54c77-126">InstanceId</span></span>|<span data-ttu-id="54c77-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="54c77-127">xs:string</span></span>|<span data-ttu-id="54c77-128">A identificação de instância de atividade.</span><span class="sxs-lookup"><span data-stu-id="54c77-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="54c77-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="54c77-129">AppDomain</span></span>|<span data-ttu-id="54c77-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="54c77-130">xs:string</span></span>|<span data-ttu-id="54c77-131">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="54c77-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
