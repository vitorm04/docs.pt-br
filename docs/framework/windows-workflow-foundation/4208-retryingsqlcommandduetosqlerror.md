---
title: 4208 - RetryingSqlCommandDueToSqlError
ms.date: 03/30/2017
ms.assetid: a8e6483a-a6e4-4bbf-82ec-cd8b6e711aad
ms.openlocfilehash: a97336f12ccfe041b79328bcb48f4e7214a05b63
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774290"
---
# <a name="4208---retryingsqlcommandduetosqlerror"></a><span data-ttu-id="ff984-102">4208 - RetryingSqlCommandDueToSqlError</span><span class="sxs-lookup"><span data-stu-id="ff984-102">4208 - RetryingSqlCommandDueToSqlError</span></span>
## <a name="properties"></a><span data-ttu-id="ff984-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="ff984-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ff984-104">ID</span><span class="sxs-lookup"><span data-stu-id="ff984-104">ID</span></span>|<span data-ttu-id="ff984-105">4208</span><span class="sxs-lookup"><span data-stu-id="ff984-105">4208</span></span>|  
|<span data-ttu-id="ff984-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="ff984-106">Keywords</span></span>|<span data-ttu-id="ff984-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="ff984-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="ff984-108">Nível</span><span class="sxs-lookup"><span data-stu-id="ff984-108">Level</span></span>|<span data-ttu-id="ff984-109">Informações</span><span class="sxs-lookup"><span data-stu-id="ff984-109">Information</span></span>|  
|<span data-ttu-id="ff984-110">Canal</span><span class="sxs-lookup"><span data-stu-id="ff984-110">Channel</span></span>|<span data-ttu-id="ff984-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="ff984-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ff984-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="ff984-112">Description</span></span>  
 <span data-ttu-id="ff984-113">Indica que o provedor SQL é experimentando de novo um comando SQL devido a um erro SQL.</span><span class="sxs-lookup"><span data-stu-id="ff984-113">Indicates the SQL provider is retrying a SQL command due to a SQL error.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ff984-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="ff984-114">Message</span></span>  
 <span data-ttu-id="ff984-115">Experimentando de novo um comando SQL por causa do erro número %1. SQL.</span><span class="sxs-lookup"><span data-stu-id="ff984-115">Retrying a SQL command due to SQL error number %1.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ff984-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="ff984-116">Details</span></span>  
  
|<span data-ttu-id="ff984-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="ff984-117">Data Item Name</span></span>|<span data-ttu-id="ff984-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="ff984-118">Data Item Type</span></span>|<span data-ttu-id="ff984-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="ff984-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ff984-120">ErrorNumber</span><span class="sxs-lookup"><span data-stu-id="ff984-120">ErrorNumber</span></span>|<span data-ttu-id="ff984-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="ff984-121">xs:string</span></span>|<span data-ttu-id="ff984-122">O número do erro SQL.</span><span class="sxs-lookup"><span data-stu-id="ff984-122">The SQL error number.</span></span>|  
|<span data-ttu-id="ff984-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ff984-123">AppDomain</span></span>|<span data-ttu-id="ff984-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="ff984-124">xs:string</span></span>|<span data-ttu-id="ff984-125">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="ff984-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
