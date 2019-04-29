---
title: 2577 - TryCatchExceptionDuringCancelation
ms.date: 03/30/2017
ms.assetid: 35ee9f55-227f-4566-bcb4-4c7c75dea85b
ms.openlocfilehash: c272dd91249dfc90e6f4c38a7339919a5a6446e5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755617"
---
# <a name="2577---trycatchexceptionduringcancelation"></a><span data-ttu-id="2c9d6-102">2577 - TryCatchExceptionDuringCancelation</span><span class="sxs-lookup"><span data-stu-id="2c9d6-102">2577 - TryCatchExceptionDuringCancelation</span></span>
## <a name="properties"></a><span data-ttu-id="2c9d6-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="2c9d6-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2c9d6-104">ID</span><span class="sxs-lookup"><span data-stu-id="2c9d6-104">ID</span></span>|<span data-ttu-id="2c9d6-105">2577</span><span class="sxs-lookup"><span data-stu-id="2c9d6-105">2577</span></span>|  
|<span data-ttu-id="2c9d6-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="2c9d6-106">Keywords</span></span>|<span data-ttu-id="2c9d6-107">WFActivities</span><span class="sxs-lookup"><span data-stu-id="2c9d6-107">WFActivities</span></span>|  
|<span data-ttu-id="2c9d6-108">Nível</span><span class="sxs-lookup"><span data-stu-id="2c9d6-108">Level</span></span>|<span data-ttu-id="2c9d6-109">Aviso</span><span class="sxs-lookup"><span data-stu-id="2c9d6-109">Warning</span></span>|  
|<span data-ttu-id="2c9d6-110">Canal</span><span class="sxs-lookup"><span data-stu-id="2c9d6-110">Channel</span></span>|<span data-ttu-id="2c9d6-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="2c9d6-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2c9d6-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="2c9d6-112">Description</span></span>  
 <span data-ttu-id="2c9d6-113">Indica que uma atividade filho de atividade de TryCatch apresentou uma exceção durante o cancelar.</span><span class="sxs-lookup"><span data-stu-id="2c9d6-113">Indicates a child activity of the TryCatch activity has thrown an exception during cancelation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2c9d6-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="2c9d6-114">Message</span></span>  
 <span data-ttu-id="2c9d6-115">Uma atividade filho da atividade “%1 " de TryCatch apresentou uma exceção durante o cancelar.</span><span class="sxs-lookup"><span data-stu-id="2c9d6-115">A child activity of the TryCatch activity '%1' has thrown an exception during cancelation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2c9d6-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="2c9d6-116">Details</span></span>  
  
|<span data-ttu-id="2c9d6-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="2c9d6-117">Data Item Name</span></span>|<span data-ttu-id="2c9d6-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="2c9d6-118">Data Item Type</span></span>|<span data-ttu-id="2c9d6-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="2c9d6-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2c9d6-120">DisplayName</span><span class="sxs-lookup"><span data-stu-id="2c9d6-120">DisplayName</span></span>|<span data-ttu-id="2c9d6-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="2c9d6-121">xs:string</span></span>|<span data-ttu-id="2c9d6-122">O nome para exibição de atividade.</span><span class="sxs-lookup"><span data-stu-id="2c9d6-122">The display name of the activity.</span></span>|  
|<span data-ttu-id="2c9d6-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2c9d6-123">AppDomain</span></span>|<span data-ttu-id="2c9d6-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="2c9d6-124">xs:string</span></span>|<span data-ttu-id="2c9d6-125">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="2c9d6-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
