---
title: ServiceMetadataBehavior
ms.date: 03/30/2017
ms.assetid: 0f194476-72f1-467e-bdce-674306316e64
ms.openlocfilehash: 19a04b6432f1ecc38a3b906b7e677175863134db
ms.sourcegitcommit: e42d09e5966dd9fd02847d3e7eeb4ec0877069f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2018
ms.locfileid: "49374814"
---
# <a name="servicemetadatabehavior"></a><span data-ttu-id="4496f-102">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="4496f-102">ServiceMetadataBehavior</span></span>
<span data-ttu-id="4496f-103">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="4496f-103">ServiceMetadataBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4496f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4496f-104">Syntax</span></span>  
  
```csharp
class ServiceMetadataBehavior : Behavior  
{  
  string ExternalMetadataLocation;  
  boolean HttpGetEnabled;  
  string HttpGetUrl;  
  boolean HttpsGetEnabled;  
  string HttpsGetUrl;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="4496f-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="4496f-105">Methods</span></span>  
 <span data-ttu-id="4496f-106">A classe ServiceMetadataBehavior não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="4496f-106">The ServiceMetadataBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="4496f-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="4496f-107">Properties</span></span>  
 <span data-ttu-id="4496f-108">A classe ServiceMetadataBehavior tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="4496f-108">The ServiceMetadataBehavior class has the following properties:</span></span>  
  
### <a name="externalmetadatalocation"></a><span data-ttu-id="4496f-109">externalMetadataLocation</span><span class="sxs-lookup"><span data-stu-id="4496f-109">ExternalMetadataLocation</span></span>  
 <span data-ttu-id="4496f-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="4496f-110">Data type: string</span></span>  
  
 <span data-ttu-id="4496f-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="4496f-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4496f-112">Define o local para o qual o serviço redireciona solicitações de metadados.</span><span class="sxs-lookup"><span data-stu-id="4496f-112">Sets the location to which the service redirects metadata requests.</span></span>  
  
### <a name="httpgetenabled"></a><span data-ttu-id="4496f-113">httpGetEnabled</span><span class="sxs-lookup"><span data-stu-id="4496f-113">HttpGetEnabled</span></span>  
 <span data-ttu-id="4496f-114">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="4496f-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="4496f-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="4496f-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4496f-116">Controla se o serviço publica seu WSDL no endereço controlado pela `HttpGetUrl` atributo.</span><span class="sxs-lookup"><span data-stu-id="4496f-116">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httpgeturl"></a><span data-ttu-id="4496f-117">httpGetUrl</span><span class="sxs-lookup"><span data-stu-id="4496f-117">HttpGetUrl</span></span>  
 <span data-ttu-id="4496f-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="4496f-118">Data type: string</span></span>  
  
 <span data-ttu-id="4496f-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="4496f-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4496f-120">Define o local no qual o serviço WSDL é publicado para recuperação usando HTTP.</span><span class="sxs-lookup"><span data-stu-id="4496f-120">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpsgetenabled"></a><span data-ttu-id="4496f-121">httpsGetEnabled</span><span class="sxs-lookup"><span data-stu-id="4496f-121">HttpsGetEnabled</span></span>  
 <span data-ttu-id="4496f-122">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="4496f-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="4496f-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="4496f-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4496f-124">Controla se o serviço publica seu WSDL via HTTPS no endereço controlado pela `HttpsGetUrl` atributo.</span><span class="sxs-lookup"><span data-stu-id="4496f-124">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpsgeturl"></a><span data-ttu-id="4496f-125">httpsGetUrl</span><span class="sxs-lookup"><span data-stu-id="4496f-125">HttpsGetUrl</span></span>  
 <span data-ttu-id="4496f-126">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="4496f-126">Data type: string</span></span>  
  
 <span data-ttu-id="4496f-127">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="4496f-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4496f-128">Define o local no qual o serviço WSDL é publicado para recuperação usando HTTPS.</span><span class="sxs-lookup"><span data-stu-id="4496f-128">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4496f-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4496f-129">Requirements</span></span>  
  
|<span data-ttu-id="4496f-130">MOF</span><span class="sxs-lookup"><span data-stu-id="4496f-130">MOF</span></span>|<span data-ttu-id="4496f-131">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="4496f-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="4496f-132">Namespace</span><span class="sxs-lookup"><span data-stu-id="4496f-132">Namespace</span></span>|<span data-ttu-id="4496f-133">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4496f-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4496f-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4496f-134">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
