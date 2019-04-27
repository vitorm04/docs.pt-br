---
title: 1005 - WorkflowApplicationIdled
ms.date: 03/30/2017
ms.assetid: 74d77dfa-f20d-4fe9-a6ae-e6d1b5fe4182
ms.openlocfilehash: 6bbd12e8025b6a127dbfec8e5d3690825c188c4d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008597"
---
# <a name="1005---workflowapplicationidled"></a><span data-ttu-id="54396-102">1005 - WorkflowApplicationIdled</span><span class="sxs-lookup"><span data-stu-id="54396-102">1005 - WorkflowApplicationIdled</span></span>
## <a name="properties"></a><span data-ttu-id="54396-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="54396-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="54396-104">ID</span><span class="sxs-lookup"><span data-stu-id="54396-104">ID</span></span>|<span data-ttu-id="54396-105">1005</span><span class="sxs-lookup"><span data-stu-id="54396-105">1005</span></span>|  
|<span data-ttu-id="54396-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="54396-106">Keywords</span></span>|<span data-ttu-id="54396-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="54396-107">WFRuntime</span></span>|  
|<span data-ttu-id="54396-108">Nível</span><span class="sxs-lookup"><span data-stu-id="54396-108">Level</span></span>|<span data-ttu-id="54396-109">Informações</span><span class="sxs-lookup"><span data-stu-id="54396-109">Information</span></span>|  
|<span data-ttu-id="54396-110">Canal</span><span class="sxs-lookup"><span data-stu-id="54396-110">Channel</span></span>|<span data-ttu-id="54396-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="54396-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="54396-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="54396-112">Description</span></span>  
 <span data-ttu-id="54396-113">Indica que um aplicativo de fluxo de trabalho rodou em marcha lenta.</span><span class="sxs-lookup"><span data-stu-id="54396-113">Indicates a workflow application has idled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="54396-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="54396-114">Message</span></span>  
 <span data-ttu-id="54396-115">Identificação de WorkflowApplication: “%1 " foi ociosa.</span><span class="sxs-lookup"><span data-stu-id="54396-115">WorkflowApplication Id: '%1' went idle.</span></span>  
  
## <a name="details"></a><span data-ttu-id="54396-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="54396-116">Details</span></span>  
  
|<span data-ttu-id="54396-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="54396-117">Data Item Name</span></span>|<span data-ttu-id="54396-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="54396-118">Data Item Type</span></span>|<span data-ttu-id="54396-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="54396-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="54396-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="54396-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="54396-121">A identificação do aplicativo de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="54396-121">The workflow application id</span></span>|  
|<span data-ttu-id="54396-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="54396-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="54396-123">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="54396-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
