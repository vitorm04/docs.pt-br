---
title: 1027 - StartTransactionContextWorkItem
ms.date: 03/30/2017
ms.assetid: 116ae5ec-b9d5-4231-824e-270d00eea7b8
ms.openlocfilehash: 231a7607f2ce9a38e8dd6c1486a68bc9eb459e5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510803"
---
# <a name="1027---starttransactioncontextworkitem"></a><span data-ttu-id="c2af8-102">1027 - StartTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="c2af8-102">1027 - StartTransactionContextWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="c2af8-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="c2af8-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c2af8-104">ID</span><span class="sxs-lookup"><span data-stu-id="c2af8-104">ID</span></span>|<span data-ttu-id="c2af8-105">1027</span><span class="sxs-lookup"><span data-stu-id="c2af8-105">1027</span></span>|  
|<span data-ttu-id="c2af8-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="c2af8-106">Keywords</span></span>|<span data-ttu-id="c2af8-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="c2af8-107">WFRuntime</span></span>|  
|<span data-ttu-id="c2af8-108">Nível</span><span class="sxs-lookup"><span data-stu-id="c2af8-108">Level</span></span>|<span data-ttu-id="c2af8-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="c2af8-109">Verbose</span></span>|  
|<span data-ttu-id="c2af8-110">Canal</span><span class="sxs-lookup"><span data-stu-id="c2af8-110">Channel</span></span>|<span data-ttu-id="c2af8-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="c2af8-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c2af8-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="c2af8-112">Description</span></span>  
 <span data-ttu-id="c2af8-113">Indica que um TransactionContextWorkItem está sendo a execução.</span><span class="sxs-lookup"><span data-stu-id="c2af8-113">Indicates a TransactionContextWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c2af8-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="c2af8-114">Message</span></span>  
 <span data-ttu-id="c2af8-115">Iniciar a execução de um TransactionContextWorkItem para atividades “%1 ", DisplayName: “%2", InstanceId: “%3".</span><span class="sxs-lookup"><span data-stu-id="c2af8-115">Starting execution of a TransactionContextWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c2af8-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="c2af8-116">Details</span></span>  
  
|<span data-ttu-id="c2af8-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="c2af8-117">Data Item Name</span></span>|<span data-ttu-id="c2af8-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="c2af8-118">Data Item Type</span></span>|<span data-ttu-id="c2af8-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="c2af8-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c2af8-120">Atividade</span><span class="sxs-lookup"><span data-stu-id="c2af8-120">Activity</span></span>|<span data-ttu-id="c2af8-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="c2af8-121">xs:string</span></span>|<span data-ttu-id="c2af8-122">O nome do tipo de atividade.</span><span class="sxs-lookup"><span data-stu-id="c2af8-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="c2af8-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="c2af8-123">DisplayName</span></span>|<span data-ttu-id="c2af8-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="c2af8-124">xs:string</span></span>|<span data-ttu-id="c2af8-125">O nome para exibição de atividade.</span><span class="sxs-lookup"><span data-stu-id="c2af8-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="c2af8-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="c2af8-126">InstanceId</span></span>|<span data-ttu-id="c2af8-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="c2af8-127">xs:string</span></span>|<span data-ttu-id="c2af8-128">A identificação de instância de atividade.</span><span class="sxs-lookup"><span data-stu-id="c2af8-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="c2af8-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c2af8-129">AppDomain</span></span>|<span data-ttu-id="c2af8-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="c2af8-130">xs:string</span></span>|<span data-ttu-id="c2af8-131">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="c2af8-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
