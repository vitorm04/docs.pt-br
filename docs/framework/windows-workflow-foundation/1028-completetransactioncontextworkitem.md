---
title: 1028 - CompleteTransactionContextWorkItem
ms.date: 03/30/2017
ms.assetid: 95423f9d-d29a-460e-bcd8-096e80af5bd0
ms.openlocfilehash: 806a437822cef8802a2bef6a54f924f84c88ef60
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008805"
---
# <a name="1028---completetransactioncontextworkitem"></a><span data-ttu-id="c85b8-102">1028 - CompleteTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="c85b8-102">1028 - CompleteTransactionContextWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="c85b8-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="c85b8-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c85b8-104">ID</span><span class="sxs-lookup"><span data-stu-id="c85b8-104">ID</span></span>|<span data-ttu-id="c85b8-105">1028</span><span class="sxs-lookup"><span data-stu-id="c85b8-105">1028</span></span>|  
|<span data-ttu-id="c85b8-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="c85b8-106">Keywords</span></span>|<span data-ttu-id="c85b8-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="c85b8-107">WFRuntime</span></span>|  
|<span data-ttu-id="c85b8-108">Nível</span><span class="sxs-lookup"><span data-stu-id="c85b8-108">Level</span></span>|<span data-ttu-id="c85b8-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="c85b8-109">Verbose</span></span>|  
|<span data-ttu-id="c85b8-110">Canal</span><span class="sxs-lookup"><span data-stu-id="c85b8-110">Channel</span></span>|<span data-ttu-id="c85b8-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="c85b8-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c85b8-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="c85b8-112">Description</span></span>  
 <span data-ttu-id="c85b8-113">Indica que um TransactionContextWorkItem terminado.</span><span class="sxs-lookup"><span data-stu-id="c85b8-113">Indicates a TransactionContextWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c85b8-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="c85b8-114">Message</span></span>  
 <span data-ttu-id="c85b8-115">Um TransactionContextWorkItem concluiu para atividades “%1 ", DisplayName: “%2", InstanceId: “%3".</span><span class="sxs-lookup"><span data-stu-id="c85b8-115">A TransactionContextWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c85b8-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="c85b8-116">Details</span></span>  
  
|<span data-ttu-id="c85b8-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="c85b8-117">Data Item Name</span></span>|<span data-ttu-id="c85b8-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="c85b8-118">Data Item Type</span></span>|<span data-ttu-id="c85b8-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="c85b8-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c85b8-120">Atividade</span><span class="sxs-lookup"><span data-stu-id="c85b8-120">Activity</span></span>|<span data-ttu-id="c85b8-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="c85b8-121">xs:string</span></span>|<span data-ttu-id="c85b8-122">O nome do tipo de atividade.</span><span class="sxs-lookup"><span data-stu-id="c85b8-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="c85b8-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="c85b8-123">DisplayName</span></span>|<span data-ttu-id="c85b8-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="c85b8-124">xs:string</span></span>|<span data-ttu-id="c85b8-125">O nome para exibição de atividade.</span><span class="sxs-lookup"><span data-stu-id="c85b8-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="c85b8-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="c85b8-126">InstanceId</span></span>|<span data-ttu-id="c85b8-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="c85b8-127">xs:string</span></span>|<span data-ttu-id="c85b8-128">A identificação de instância de atividade.</span><span class="sxs-lookup"><span data-stu-id="c85b8-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="c85b8-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c85b8-129">AppDomain</span></span>|<span data-ttu-id="c85b8-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="c85b8-130">xs:string</span></span>|<span data-ttu-id="c85b8-131">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="c85b8-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
