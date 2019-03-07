---
title: 1004 - WorkflowInstanceAborted
ms.date: 03/30/2017
ms.assetid: edb9ab8c-0b9a-488d-aa96-9c8c7984b53c
ms.openlocfilehash: d34f6f1ab6af8e06a0f28fb043faf9fe16a8b211
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485181"
---
# <a name="1004---workflowinstanceaborted"></a><span data-ttu-id="28dc4-102">1004 - WorkflowInstanceAborted</span><span class="sxs-lookup"><span data-stu-id="28dc4-102">1004 - WorkflowInstanceAborted</span></span>

## <a name="properties"></a><span data-ttu-id="28dc4-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="28dc4-103">Properties</span></span>

|||
|-|-|
|<span data-ttu-id="28dc4-104">ID</span><span class="sxs-lookup"><span data-stu-id="28dc4-104">ID</span></span>|<span data-ttu-id="28dc4-105">1004</span><span class="sxs-lookup"><span data-stu-id="28dc4-105">1004</span></span>|
|<span data-ttu-id="28dc4-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="28dc4-106">Keywords</span></span>|<span data-ttu-id="28dc4-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="28dc4-107">WFRuntime</span></span>|
|<span data-ttu-id="28dc4-108">Nível</span><span class="sxs-lookup"><span data-stu-id="28dc4-108">Level</span></span>|<span data-ttu-id="28dc4-109">Informações</span><span class="sxs-lookup"><span data-stu-id="28dc4-109">Information</span></span>|
|<span data-ttu-id="28dc4-110">Canal</span><span class="sxs-lookup"><span data-stu-id="28dc4-110">Channel</span></span>|<span data-ttu-id="28dc4-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="28dc4-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|

## <a name="description"></a><span data-ttu-id="28dc4-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="28dc4-112">Description</span></span>

<span data-ttu-id="28dc4-113">Indica que uma instância de fluxo de trabalho foi anulado com uma exceção.</span><span class="sxs-lookup"><span data-stu-id="28dc4-113">Indicates a workflow instance has aborted with an exception.</span></span>

## <a name="message"></a><span data-ttu-id="28dc4-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="28dc4-114">Message</span></span>

<span data-ttu-id="28dc4-115">Identificação de WorkflowInstance: “%1 " foi anuladas com uma exceção.</span><span class="sxs-lookup"><span data-stu-id="28dc4-115">WorkflowInstance Id: '%1' was aborted with an exception.</span></span>

## <a name="details"></a><span data-ttu-id="28dc4-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="28dc4-116">Details</span></span>

|<span data-ttu-id="28dc4-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="28dc4-117">Data Item Name</span></span>|<span data-ttu-id="28dc4-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="28dc4-118">Data Item Type</span></span>|<span data-ttu-id="28dc4-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="28dc4-119">Description</span></span>|
|--------------------|--------------------|-----------------|
|<span data-ttu-id="28dc4-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="28dc4-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="28dc4-121">A identificação de instância para o fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="28dc4-121">The instance id for the workflow</span></span>|
|<span data-ttu-id="28dc4-122">Exceção</span><span class="sxs-lookup"><span data-stu-id="28dc4-122">Exception</span></span>|`xs:string`|<span data-ttu-id="28dc4-123">Os detalhes de exceção para a exceção</span><span class="sxs-lookup"><span data-stu-id="28dc4-123">The exception details for the exception</span></span>|
|<span data-ttu-id="28dc4-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="28dc4-124">AppDomain</span></span>|`xs:string`|<span data-ttu-id="28dc4-125">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="28dc4-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
