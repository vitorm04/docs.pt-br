---
title: 4208 - RetryingSqlCommandDueToSqlError
ms.date: 03/30/2017
ms.assetid: a8e6483a-a6e4-4bbf-82ec-cd8b6e711aad
ms.openlocfilehash: a97336f12ccfe041b79328bcb48f4e7214a05b63
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33511583"
---
# <a name="4208---retryingsqlcommandduetosqlerror"></a><span data-ttu-id="32e5b-102">4208 - RetryingSqlCommandDueToSqlError</span><span class="sxs-lookup"><span data-stu-id="32e5b-102">4208 - RetryingSqlCommandDueToSqlError</span></span>
## <a name="properties"></a><span data-ttu-id="32e5b-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="32e5b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="32e5b-104">ID</span><span class="sxs-lookup"><span data-stu-id="32e5b-104">ID</span></span>|<span data-ttu-id="32e5b-105">4208</span><span class="sxs-lookup"><span data-stu-id="32e5b-105">4208</span></span>|  
|<span data-ttu-id="32e5b-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="32e5b-106">Keywords</span></span>|<span data-ttu-id="32e5b-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="32e5b-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="32e5b-108">Nível</span><span class="sxs-lookup"><span data-stu-id="32e5b-108">Level</span></span>|<span data-ttu-id="32e5b-109">Informações</span><span class="sxs-lookup"><span data-stu-id="32e5b-109">Information</span></span>|  
|<span data-ttu-id="32e5b-110">Canal</span><span class="sxs-lookup"><span data-stu-id="32e5b-110">Channel</span></span>|<span data-ttu-id="32e5b-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="32e5b-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="32e5b-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="32e5b-112">Description</span></span>  
 <span data-ttu-id="32e5b-113">Indica que o provedor SQL é experimentando de novo um comando SQL devido a um erro SQL.</span><span class="sxs-lookup"><span data-stu-id="32e5b-113">Indicates the SQL provider is retrying a SQL command due to a SQL error.</span></span>  
  
## <a name="message"></a><span data-ttu-id="32e5b-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="32e5b-114">Message</span></span>  
 <span data-ttu-id="32e5b-115">Experimentando de novo um comando SQL por causa do erro número %1. SQL.</span><span class="sxs-lookup"><span data-stu-id="32e5b-115">Retrying a SQL command due to SQL error number %1.</span></span>  
  
## <a name="details"></a><span data-ttu-id="32e5b-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="32e5b-116">Details</span></span>  
  
|<span data-ttu-id="32e5b-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="32e5b-117">Data Item Name</span></span>|<span data-ttu-id="32e5b-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="32e5b-118">Data Item Type</span></span>|<span data-ttu-id="32e5b-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="32e5b-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="32e5b-120">ErrorNumber</span><span class="sxs-lookup"><span data-stu-id="32e5b-120">ErrorNumber</span></span>|<span data-ttu-id="32e5b-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="32e5b-121">xs:string</span></span>|<span data-ttu-id="32e5b-122">O número do erro SQL.</span><span class="sxs-lookup"><span data-stu-id="32e5b-122">The SQL error number.</span></span>|  
|<span data-ttu-id="32e5b-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="32e5b-123">AppDomain</span></span>|<span data-ttu-id="32e5b-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="32e5b-124">xs:string</span></span>|<span data-ttu-id="32e5b-125">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="32e5b-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
