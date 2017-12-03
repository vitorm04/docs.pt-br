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
ms.openlocfilehash: f17b31e1dfe9ba60b2042a85a6d673d986fe0a33
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="servicemetadatabehavior"></a><span data-ttu-id="3ea35-102">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="3ea35-102">ServiceMetadataBehavior</span></span>
<span data-ttu-id="3ea35-103">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="3ea35-103">ServiceMetadataBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ea35-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3ea35-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="3ea35-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="3ea35-105">Methods</span></span>  
 <span data-ttu-id="3ea35-106">A classe de ServiceMetadataBehavior não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="3ea35-106">The ServiceMetadataBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="3ea35-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="3ea35-107">Properties</span></span>  
 <span data-ttu-id="3ea35-108">A classe de ServiceMetadataBehavior tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="3ea35-108">The ServiceMetadataBehavior class has the following properties:</span></span>  
  
### <a name="externalmetadatalocation"></a><span data-ttu-id="3ea35-109">externalMetadataLocation</span><span class="sxs-lookup"><span data-stu-id="3ea35-109">ExternalMetadataLocation</span></span>  
 <span data-ttu-id="3ea35-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="3ea35-110">Data type: string</span></span>  
  
 <span data-ttu-id="3ea35-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="3ea35-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3ea35-112">Define o local para o qual o serviço redireciona solicitações de metadados.</span><span class="sxs-lookup"><span data-stu-id="3ea35-112">Sets the location to which the service redirects metadata requests.</span></span>  
  
### <a name="httpgetenabled"></a><span data-ttu-id="3ea35-113">httpGetEnabled</span><span class="sxs-lookup"><span data-stu-id="3ea35-113">HttpGetEnabled</span></span>  
 <span data-ttu-id="3ea35-114">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="3ea35-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="3ea35-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="3ea35-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3ea35-116">Controla se o serviço publica seu WSDL no endereço controlado pelo `HttpGetUrl` atributo.</span><span class="sxs-lookup"><span data-stu-id="3ea35-116">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httpgeturl"></a><span data-ttu-id="3ea35-117">httpGetUrl</span><span class="sxs-lookup"><span data-stu-id="3ea35-117">HttpGetUrl</span></span>  
 <span data-ttu-id="3ea35-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="3ea35-118">Data type: string</span></span>  
  
 <span data-ttu-id="3ea35-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="3ea35-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3ea35-120">Define o local no qual o serviço WSDL é publicado para recuperação usando HTTP.</span><span class="sxs-lookup"><span data-stu-id="3ea35-120">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpsgetenabled"></a><span data-ttu-id="3ea35-121">httpsGetEnabled</span><span class="sxs-lookup"><span data-stu-id="3ea35-121">HttpsGetEnabled</span></span>  
 <span data-ttu-id="3ea35-122">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="3ea35-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="3ea35-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="3ea35-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3ea35-124">Controla se o serviço publica seu WSDL em HTTPS no endereço controlado pelo `HttpsGetUrl` atributo.</span><span class="sxs-lookup"><span data-stu-id="3ea35-124">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpsgeturl"></a><span data-ttu-id="3ea35-125">httpsGetUrl</span><span class="sxs-lookup"><span data-stu-id="3ea35-125">HttpsGetUrl</span></span>  
 <span data-ttu-id="3ea35-126">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="3ea35-126">Data type: string</span></span>  
  
 <span data-ttu-id="3ea35-127">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="3ea35-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3ea35-128">Define o local no qual o serviço WSDL é publicado para recuperação usando HTTPS.</span><span class="sxs-lookup"><span data-stu-id="3ea35-128">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ea35-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3ea35-129">Requirements</span></span>  
  
|<span data-ttu-id="3ea35-130">MOF</span><span class="sxs-lookup"><span data-stu-id="3ea35-130">MOF</span></span>|<span data-ttu-id="3ea35-131">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="3ea35-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="3ea35-132">Namespace</span><span class="sxs-lookup"><span data-stu-id="3ea35-132">Namespace</span></span>|<span data-ttu-id="3ea35-133">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="3ea35-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3ea35-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3ea35-134">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
