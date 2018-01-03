---
title: Gerenciamento de cache para aplicativos de rede
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cache [.NET Framework], network applications
- network resources, caching
- Internet, caching
ms.assetid: fc258a40-f370-434f-ae09-4a8cb11ddaeb
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 458a1e67e9ca4ff3a36f1b0c69fcc4bdc00be3e4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="cache-management-for-network-applications"></a><span data-ttu-id="3a37a-102">Gerenciamento de cache para aplicativos de rede</span><span class="sxs-lookup"><span data-stu-id="3a37a-102">Cache Management for Network Applications</span></span>
<span data-ttu-id="3a37a-103">Este tópico e seus subtópicos relacionados descrevem o cache para recursos obtidos usando as classes <xref:System.Net.WebClient>, <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest> e <xref:System.Net.FtpWebRequest>.</span><span class="sxs-lookup"><span data-stu-id="3a37a-103">This topic and its related subtopics describe caching for resources obtained using the <xref:System.Net.WebClient>, <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, and <xref:System.Net.FtpWebRequest> classes.</span></span>  
  
 <span data-ttu-id="3a37a-104">Um cache fornece armazenamento temporário de recursos que foram solicitados por um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3a37a-104">A cache provides temporary storage of resources that have been requested by an application.</span></span> <span data-ttu-id="3a37a-105">Se um aplicativo solicitar o mesmo recurso mais de uma vez, o recurso poderá ser retornado do cache, evitando a sobrecarga de solicitá-lo novamente ao servidor.</span><span class="sxs-lookup"><span data-stu-id="3a37a-105">If an application requests the same resource more than once, the resource can be returned from the cache, avoiding the overhead of re-requesting it from the server.</span></span> <span data-ttu-id="3a37a-106">O cache pode melhorar o desempenho do aplicativo reduzindo o tempo necessário para obter um recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="3a37a-106">Caching can improve application performance by reducing the time required to get a requested resource.</span></span> <span data-ttu-id="3a37a-107">O cache também pode diminuir o tráfego de rede reduzindo o número de viagens ao servidor.</span><span class="sxs-lookup"><span data-stu-id="3a37a-107">Caching can also decrease network traffic by reducing the number of trips to the server.</span></span> <span data-ttu-id="3a37a-108">Embora o cache melhore o desempenho, ele aumenta o risco de que o recurso retornado para o aplicativo seja obsoleto, o que significa que ele não é idêntico ao recurso que seria enviado pelo servidor se o cache não estivesse em uso.</span><span class="sxs-lookup"><span data-stu-id="3a37a-108">While caching improves performance, it increases the risk that the resource returned to the application is stale, meaning that it is not identical to the resource that would have been sent by the server if caching were not in use.</span></span>  
  
 <span data-ttu-id="3a37a-109">O cache pode permitir que usuários ou processos não autorizados leiam dados confidenciais.</span><span class="sxs-lookup"><span data-stu-id="3a37a-109">Caching may allow unauthorized users or processes to read sensitive data.</span></span> <span data-ttu-id="3a37a-110">Uma resposta autenticada que é armazenada em cache pode ser recuperada do cache sem uma autorização adicional.</span><span class="sxs-lookup"><span data-stu-id="3a37a-110">An authenticated response that is cached may be retrieved from the cache without an additional authorization.</span></span> <span data-ttu-id="3a37a-111">Se o cache estiver habilitado, altere para <xref:System.Net.WebRequest.CachePolicy%2A>, <xref:System.Net.Cache.RequestCacheLevel.BypassCache> ou <xref:System.Net.Cache.RequestCacheLevel.NoCacheNoStore> para desabilitar o cache nessa solicitação.</span><span class="sxs-lookup"><span data-stu-id="3a37a-111">If caching is enabled, change to <xref:System.Net.WebRequest.CachePolicy%2A> to <xref:System.Net.Cache.RequestCacheLevel.BypassCache> or <xref:System.Net.Cache.RequestCacheLevel.NoCacheNoStore> to disable caching for this request.</span></span>  
  
 <span data-ttu-id="3a37a-112">Devido a preocupações de segurança, o cache **não** é recomendado para cenários de camada intermediária.</span><span class="sxs-lookup"><span data-stu-id="3a37a-112">Due to security concerns, caching is **not** recommended for middle tier scenarios.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3a37a-113">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="3a37a-113">In This Section</span></span>  
 [<span data-ttu-id="3a37a-114">Política de cache</span><span class="sxs-lookup"><span data-stu-id="3a37a-114">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)  
 <span data-ttu-id="3a37a-115">Explica o que é uma política de cache e como definir uma.</span><span class="sxs-lookup"><span data-stu-id="3a37a-115">Explains what a cache policy is and how to define one.</span></span>  
  
 [<span data-ttu-id="3a37a-116">Políticas de cache baseadas na localização</span><span class="sxs-lookup"><span data-stu-id="3a37a-116">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 <span data-ttu-id="3a37a-117">Define cada tipo de política de cache baseada na localização disponível para os recursos do protocolo HTTP (http e https).</span><span class="sxs-lookup"><span data-stu-id="3a37a-117">Defines each type of location-based cache policy available for Hypertext Transfer Protocol (http and https) resources.</span></span>  
  
 [<span data-ttu-id="3a37a-118">Políticas de cache baseadas em tempo</span><span class="sxs-lookup"><span data-stu-id="3a37a-118">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 <span data-ttu-id="3a37a-119">Descreve os critérios que podem ser usados para personalizar uma política de cache baseada em tempo.</span><span class="sxs-lookup"><span data-stu-id="3a37a-119">Describes the criteria that can be used to customize a time-based cache policy.</span></span>  
  
 [<span data-ttu-id="3a37a-120">Configurando o cache em aplicativos de rede</span><span class="sxs-lookup"><span data-stu-id="3a37a-120">Configuring Caching in Network Applications</span></span>](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 <span data-ttu-id="3a37a-121">Descreve como criar políticas de cache e solicitações que usam o cache de forma programática.</span><span class="sxs-lookup"><span data-stu-id="3a37a-121">Describes how to programmatically create cache policies and requests that use caching.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="3a37a-122">Referência</span><span class="sxs-lookup"><span data-stu-id="3a37a-122">Reference</span></span>  
 <xref:System.Net.Cache>  
 <span data-ttu-id="3a37a-123">Define os tipos e as enumerações usados para definir políticas de cache para os recursos obtidos usando as classes <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest> e <xref:System.Net.FtpWebRequest>.</span><span class="sxs-lookup"><span data-stu-id="3a37a-123">Defines the types and enumerations used to define cache policies for resources obtained using the <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, and <xref:System.Net.FtpWebRequest> classes.</span></span>
