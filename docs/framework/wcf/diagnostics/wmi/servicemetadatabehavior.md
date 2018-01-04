---
title: ServiceMetadataBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f194476-72f1-467e-bdce-674306316e64
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c05f6be9fc0507b7e2f1de4374e3b9bbe3e2a10e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="servicemetadatabehavior"></a><span data-ttu-id="79da6-102">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="79da6-102">ServiceMetadataBehavior</span></span>
<span data-ttu-id="79da6-103">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="79da6-103">ServiceMetadataBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79da6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="79da6-104">Syntax</span></span>  
  
```  
class ServiceMetadataBehavior : Behavior  
{  
  string ExternalMetadataLocation;  
  boolean HttpGetEnabled;  
  string HttpGetUrl;  
  boolean HttpsGetEnabled;  
  string HttpsGetUrl;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="79da6-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="79da6-105">Methods</span></span>  
 <span data-ttu-id="79da6-106">A classe de ServiceMetadataBehavior não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="79da6-106">The ServiceMetadataBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="79da6-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="79da6-107">Properties</span></span>  
 <span data-ttu-id="79da6-108">A classe de ServiceMetadataBehavior tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="79da6-108">The ServiceMetadataBehavior class has the following properties:</span></span>  
  
### <a name="externalmetadatalocation"></a><span data-ttu-id="79da6-109">externalMetadataLocation</span><span class="sxs-lookup"><span data-stu-id="79da6-109">ExternalMetadataLocation</span></span>  
 <span data-ttu-id="79da6-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="79da6-110">Data type: string</span></span>  
  
 <span data-ttu-id="79da6-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="79da6-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="79da6-112">Define o local para o qual o serviço redireciona solicitações de metadados.</span><span class="sxs-lookup"><span data-stu-id="79da6-112">Sets the location to which the service redirects metadata requests.</span></span>  
  
### <a name="httpgetenabled"></a><span data-ttu-id="79da6-113">httpGetEnabled</span><span class="sxs-lookup"><span data-stu-id="79da6-113">HttpGetEnabled</span></span>  
 <span data-ttu-id="79da6-114">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="79da6-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="79da6-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="79da6-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="79da6-116">Controla se o serviço publica seu WSDL no endereço controlado pelo `HttpGetUrl` atributo.</span><span class="sxs-lookup"><span data-stu-id="79da6-116">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httpgeturl"></a><span data-ttu-id="79da6-117">httpGetUrl</span><span class="sxs-lookup"><span data-stu-id="79da6-117">HttpGetUrl</span></span>  
 <span data-ttu-id="79da6-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="79da6-118">Data type: string</span></span>  
  
 <span data-ttu-id="79da6-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="79da6-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="79da6-120">Define o local no qual o serviço WSDL é publicado para recuperação usando HTTP.</span><span class="sxs-lookup"><span data-stu-id="79da6-120">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpsgetenabled"></a><span data-ttu-id="79da6-121">httpsGetEnabled</span><span class="sxs-lookup"><span data-stu-id="79da6-121">HttpsGetEnabled</span></span>  
 <span data-ttu-id="79da6-122">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="79da6-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="79da6-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="79da6-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="79da6-124">Controla se o serviço publica seu WSDL em HTTPS no endereço controlado pelo `HttpsGetUrl` atributo.</span><span class="sxs-lookup"><span data-stu-id="79da6-124">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpsgeturl"></a><span data-ttu-id="79da6-125">httpsGetUrl</span><span class="sxs-lookup"><span data-stu-id="79da6-125">HttpsGetUrl</span></span>  
 <span data-ttu-id="79da6-126">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="79da6-126">Data type: string</span></span>  
  
 <span data-ttu-id="79da6-127">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="79da6-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="79da6-128">Define o local no qual o serviço WSDL é publicado para recuperação usando HTTPS.</span><span class="sxs-lookup"><span data-stu-id="79da6-128">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79da6-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="79da6-129">Requirements</span></span>  
  
|<span data-ttu-id="79da6-130">MOF</span><span class="sxs-lookup"><span data-stu-id="79da6-130">MOF</span></span>|<span data-ttu-id="79da6-131">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="79da6-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="79da6-132">Namespace</span><span class="sxs-lookup"><span data-stu-id="79da6-132">Namespace</span></span>|<span data-ttu-id="79da6-133">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="79da6-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="79da6-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="79da6-134">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
