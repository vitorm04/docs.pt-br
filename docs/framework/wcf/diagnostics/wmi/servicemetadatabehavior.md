---
title: ServiceMetadataBehavior
ms.date: 03/30/2017
ms.assetid: 0f194476-72f1-467e-bdce-674306316e64
ms.openlocfilehash: 1d99af064205447c2f11f6f19258551c1e88d386
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59976125"
---
# <a name="servicemetadatabehavior"></a><span data-ttu-id="a4ada-102">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="a4ada-102">ServiceMetadataBehavior</span></span>
<span data-ttu-id="a4ada-103">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="a4ada-103">ServiceMetadataBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4ada-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a4ada-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="a4ada-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="a4ada-105">Methods</span></span>  
 <span data-ttu-id="a4ada-106">A classe ServiceMetadataBehavior não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="a4ada-106">The ServiceMetadataBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a4ada-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="a4ada-107">Properties</span></span>  
 <span data-ttu-id="a4ada-108">A classe ServiceMetadataBehavior tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="a4ada-108">The ServiceMetadataBehavior class has the following properties:</span></span>  
  
### <a name="externalmetadatalocation"></a><span data-ttu-id="a4ada-109">ExternalMetadataLocation</span><span class="sxs-lookup"><span data-stu-id="a4ada-109">ExternalMetadataLocation</span></span>  
 <span data-ttu-id="a4ada-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="a4ada-110">Data type: string</span></span>  
  
 <span data-ttu-id="a4ada-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="a4ada-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a4ada-112">Define o local para o qual o serviço redireciona solicitações de metadados.</span><span class="sxs-lookup"><span data-stu-id="a4ada-112">Sets the location to which the service redirects metadata requests.</span></span>  
  
### <a name="httpgetenabled"></a><span data-ttu-id="a4ada-113">HttpGetEnabled</span><span class="sxs-lookup"><span data-stu-id="a4ada-113">HttpGetEnabled</span></span>  
 <span data-ttu-id="a4ada-114">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="a4ada-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="a4ada-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="a4ada-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a4ada-116">Controla se o serviço publica seu WSDL no endereço controlado pela `HttpGetUrl` atributo.</span><span class="sxs-lookup"><span data-stu-id="a4ada-116">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httpgeturl"></a><span data-ttu-id="a4ada-117">HttpGetUrl</span><span class="sxs-lookup"><span data-stu-id="a4ada-117">HttpGetUrl</span></span>  
 <span data-ttu-id="a4ada-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="a4ada-118">Data type: string</span></span>  
  
 <span data-ttu-id="a4ada-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="a4ada-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a4ada-120">Define o local no qual o serviço WSDL é publicado para recuperação usando HTTP.</span><span class="sxs-lookup"><span data-stu-id="a4ada-120">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpsgetenabled"></a><span data-ttu-id="a4ada-121">HttpsGetEnabled</span><span class="sxs-lookup"><span data-stu-id="a4ada-121">HttpsGetEnabled</span></span>  
 <span data-ttu-id="a4ada-122">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="a4ada-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="a4ada-123">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="a4ada-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a4ada-124">Controla se o serviço publica seu WSDL via HTTPS no endereço controlado pela `HttpsGetUrl` atributo.</span><span class="sxs-lookup"><span data-stu-id="a4ada-124">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpsgeturl"></a><span data-ttu-id="a4ada-125">HttpsGetUrl</span><span class="sxs-lookup"><span data-stu-id="a4ada-125">HttpsGetUrl</span></span>  
 <span data-ttu-id="a4ada-126">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="a4ada-126">Data type: string</span></span>  
  
 <span data-ttu-id="a4ada-127">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="a4ada-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a4ada-128">Define o local no qual o serviço WSDL é publicado para recuperação usando HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a4ada-128">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4ada-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a4ada-129">Requirements</span></span>  
  
|<span data-ttu-id="a4ada-130">MOF</span><span class="sxs-lookup"><span data-stu-id="a4ada-130">MOF</span></span>|<span data-ttu-id="a4ada-131">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="a4ada-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="a4ada-132">Namespace</span><span class="sxs-lookup"><span data-stu-id="a4ada-132">Namespace</span></span>|<span data-ttu-id="a4ada-133">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a4ada-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a4ada-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a4ada-134">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
