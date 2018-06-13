---
title: 1002 - WorkflowApplicationTerminated
ms.date: 03/30/2017
ms.assetid: 4e8b111f-79dc-4898-bb4a-e9b36f69420f
ms.openlocfilehash: 01c9aba6e863e07a1a999a28fccefbab95a34d5b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510073"
---
# <a name="1002---workflowapplicationterminated"></a><span data-ttu-id="a724a-102">1002 - WorkflowApplicationTerminated</span><span class="sxs-lookup"><span data-stu-id="a724a-102">1002 - WorkflowApplicationTerminated</span></span>
## <a name="properties"></a><span data-ttu-id="a724a-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="a724a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a724a-104">ID</span><span class="sxs-lookup"><span data-stu-id="a724a-104">ID</span></span>|<span data-ttu-id="a724a-105">1002</span><span class="sxs-lookup"><span data-stu-id="a724a-105">1002</span></span>|  
|<span data-ttu-id="a724a-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="a724a-106">Keywords</span></span>|<span data-ttu-id="a724a-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="a724a-107">WFRuntime</span></span>|  
|<span data-ttu-id="a724a-108">Nível</span><span class="sxs-lookup"><span data-stu-id="a724a-108">Level</span></span>|<span data-ttu-id="a724a-109">Informações</span><span class="sxs-lookup"><span data-stu-id="a724a-109">Information</span></span>|  
|<span data-ttu-id="a724a-110">Canal</span><span class="sxs-lookup"><span data-stu-id="a724a-110">Channel</span></span>|<span data-ttu-id="a724a-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="a724a-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a724a-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="a724a-112">Description</span></span>  
 <span data-ttu-id="a724a-113">Indica que um aplicativo de fluxo de trabalho foi finalizado no estado criticado com uma exceção.</span><span class="sxs-lookup"><span data-stu-id="a724a-113">Indicates a workflow application has terminated in the Faulted state with an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a724a-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="a724a-114">Message</span></span>  
 <span data-ttu-id="a724a-115">Identificação de WorkflowApplication: “%1 " foi encerrado.</span><span class="sxs-lookup"><span data-stu-id="a724a-115">WorkflowApplication Id: '%1' was terminated.</span></span> <span data-ttu-id="a724a-116">Foi concluído em estado Faulted (com falha) com uma exceção.</span><span class="sxs-lookup"><span data-stu-id="a724a-116">It has completed in the Faulted state with an exception.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a724a-117">Detalhes</span><span class="sxs-lookup"><span data-stu-id="a724a-117">Details</span></span>  
  
|<span data-ttu-id="a724a-118">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="a724a-118">Data Item Name</span></span>|<span data-ttu-id="a724a-119">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="a724a-119">Data Item Type</span></span>|<span data-ttu-id="a724a-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="a724a-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a724a-121">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="a724a-121">WorkflowApplicationId</span></span>|`xs:string`|<span data-ttu-id="a724a-122">A identificação do aplicativo de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="a724a-122">The workflow application id</span></span>|  
|<span data-ttu-id="a724a-123">Exceção</span><span class="sxs-lookup"><span data-stu-id="a724a-123">Exception</span></span>|`xs:string`|<span data-ttu-id="a724a-124">Os detalhes de exceção para a exceção</span><span class="sxs-lookup"><span data-stu-id="a724a-124">The exception details for the exception</span></span>|  
|<span data-ttu-id="a724a-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a724a-125">AppDomain</span></span>|`xs:string`|<span data-ttu-id="a724a-126">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="a724a-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
