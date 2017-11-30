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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9d10fdd9e33b078fa392e0ef359372913f9ba133
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="servicemetadatabehavior"></a><span data-ttu-id="3e5be-102">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="3e5be-102">ServiceMetadataBehavior</span></span>
<span data-ttu-id="3e5be-103">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="3e5be-103">ServiceMetadataBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e5be-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3e5be-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="3e5be-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="3e5be-105">Methods</span></span>  
 <span data-ttu-id="3e5be-106">A classe de ServiceMetadataBehavior não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="3e5be-106">The ServiceMetadataBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="3e5be-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="3e5be-107">Properties</span></span>  
 <span data-ttu-id="3e5be-108">A classe de ServiceMetadataBehavior tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="3e5be-108">The ServiceMetadataBehavior class has the following properties:</span></span>  
  
### <a name="externalmetadatalocation"></a><span data-ttu-id="3e5be-109">externalMetadataLocation</span><span class="sxs-lookup"><span data-stu-id="3e5be-109">ExternalMetadataLocation</span></span>  
 <span data-ttu-id="3e5be-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="3e5be-110">Data type: string</span></span>  
  
 <span data-ttu-id="3e5be-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="3e5be-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3e5be-112">Define o local para o qual o serviço redireciona solicitações de metadados.</span><span class="sxs-lookup"><span data-stu-id="3e5be-112">Sets the location to which the service redirects metadata requests.</span></span>  
  
### <a name="httpgetenabled"></a><span data-ttu-id="3e5be-113">httpGetEnabled</span><span class="sxs-lookup"><span data-stu-id="3e5be-113">HttpGetEnabled</span></span>  
 <span data-ttu-id="3e5be-114">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="3e5be-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="3e5be-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="3e5be-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3e5be-116">Controla se o serviço publica seu WSDL no endereço controlado pelo `HttpGetUrl` atributo.</span><span class="sxs-lookup"><span data-stu-id="3e5be-116">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httpgeturl"></a><span data-ttu-id="3e5be-117">httpGetUrl</span><span class="sxs-lookup"><span data-stu-id="3e5be-117">HttpGetUrl</span></span>  
 <span data-ttu-id="3e5be-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="3e5be-118">Data type: string</span></span>  
  
 <span data-ttu-id="3e5be-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="3e5be-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3e5be-120">Define o local no qual o serviço WSDL é publicado para recuperação usando HTTP.</span><span class="sxs-lookup"><span data-stu-id="3e5be-120">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpsgetenabled"></a><span data-ttu-id="3e5be-121">httpsGetEnabled</span><span class="sxs-lookup"><span data-stu-id="3e5be-121">HttpsGetEnabled</span></span>  
 <span data-ttu-id="3e5be-122">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="3e5be-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="3e5be-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="3e5be-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3e5be-124">Controla se o serviço publica seu WSDL em HTTPS no endereço controlado pelo `HttpsGetUrl` atributo.</span><span class="sxs-lookup"><span data-stu-id="3e5be-124">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpsgeturl"></a><span data-ttu-id="3e5be-125">httpsGetUrl</span><span class="sxs-lookup"><span data-stu-id="3e5be-125">HttpsGetUrl</span></span>  
 <span data-ttu-id="3e5be-126">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="3e5be-126">Data type: string</span></span>  
  
 <span data-ttu-id="3e5be-127">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="3e5be-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3e5be-128">Define o local no qual o serviço WSDL é publicado para recuperação usando HTTPS.</span><span class="sxs-lookup"><span data-stu-id="3e5be-128">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e5be-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3e5be-129">Requirements</span></span>  
  
|<span data-ttu-id="3e5be-130">MOF</span><span class="sxs-lookup"><span data-stu-id="3e5be-130">MOF</span></span>|<span data-ttu-id="3e5be-131">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="3e5be-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="3e5be-132">Namespace</span><span class="sxs-lookup"><span data-stu-id="3e5be-132">Namespace</span></span>|<span data-ttu-id="3e5be-133">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="3e5be-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3e5be-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3e5be-134">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
