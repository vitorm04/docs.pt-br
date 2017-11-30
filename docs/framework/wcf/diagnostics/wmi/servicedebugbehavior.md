---
title: ServiceDebugBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a5ec9061-1e95-43fb-b0d9-dbd0a7bc3c44
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2d6b866c90e3e6c6e72dc75f230bcf7b4e03a6bb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="servicedebugbehavior"></a><span data-ttu-id="cb38d-102">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="cb38d-102">ServiceDebugBehavior</span></span>
<span data-ttu-id="cb38d-103">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="cb38d-103">ServiceDebugBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb38d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cb38d-104">Syntax</span></span>  
  
```  
class ServiceDebugBehavior : Behavior  
{  
  boolean HttpHelpPageEnabled;  
  string HttpHelpPageUrl;  
  boolean HttpsHelpPageEnabled;  
  string HttpsHelpPageUrl;  
  boolean IncludeExceptionDetailInFaults;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="cb38d-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="cb38d-105">Methods</span></span>  
 <span data-ttu-id="cb38d-106">A classe ServiceDebugBehavior não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="cb38d-106">The ServiceDebugBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="cb38d-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="cb38d-107">Properties</span></span>  
 <span data-ttu-id="cb38d-108">A classe ServiceDebugBehavior tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="cb38d-108">The ServiceDebugBehavior class has the following properties:</span></span>  
  
### <a name="httphelppageenabled"></a><span data-ttu-id="cb38d-109">httpHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="cb38d-109">HttpHelpPageEnabled</span></span>  
 <span data-ttu-id="cb38d-110">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="cb38d-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="cb38d-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="cb38d-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cb38d-112">Controla se o serviço publica seu WSDL no endereço controlado pelo `HttpGetUrl` atributo.</span><span class="sxs-lookup"><span data-stu-id="cb38d-112">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httphelppageurl"></a><span data-ttu-id="cb38d-113">httpHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="cb38d-113">HttpHelpPageUrl</span></span>  
 <span data-ttu-id="cb38d-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="cb38d-114">Data type: string</span></span>  
  
 <span data-ttu-id="cb38d-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="cb38d-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cb38d-116">Define o local no qual o serviço WSDL é publicado para recuperação usando HTTP.</span><span class="sxs-lookup"><span data-stu-id="cb38d-116">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpshelppageenabled"></a><span data-ttu-id="cb38d-117">httpsHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="cb38d-117">HttpsHelpPageEnabled</span></span>  
 <span data-ttu-id="cb38d-118">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="cb38d-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="cb38d-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="cb38d-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cb38d-120">Controla se o serviço publica seu WSDL em HTTPS no endereço controlado pelo `HttpsGetUrl` atributo.</span><span class="sxs-lookup"><span data-stu-id="cb38d-120">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpshelppageurl"></a><span data-ttu-id="cb38d-121">httpsHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="cb38d-121">HttpsHelpPageUrl</span></span>  
 <span data-ttu-id="cb38d-122">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="cb38d-122">Data type: string</span></span>  
  
 <span data-ttu-id="cb38d-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="cb38d-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cb38d-124">Define o local no qual o serviço WSDL é publicado para recuperação usando HTTPS.</span><span class="sxs-lookup"><span data-stu-id="cb38d-124">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="cb38d-125">includeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="cb38d-125">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="cb38d-126">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="cb38d-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="cb38d-127">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="cb38d-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cb38d-128">Especifica se deve incluir informações de exceção gerenciada no detalhe de falhas SOAP retornadas aos clientes para fins de depuração.</span><span class="sxs-lookup"><span data-stu-id="cb38d-128">Specifies whether to include managed exception information in the detail of SOAP faults returned to the clients for debugging purposes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb38d-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cb38d-129">Requirements</span></span>  
  
|<span data-ttu-id="cb38d-130">MOF</span><span class="sxs-lookup"><span data-stu-id="cb38d-130">MOF</span></span>|<span data-ttu-id="cb38d-131">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="cb38d-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="cb38d-132">Namespace</span><span class="sxs-lookup"><span data-stu-id="cb38d-132">Namespace</span></span>|<span data-ttu-id="cb38d-133">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="cb38d-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cb38d-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cb38d-134">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceDebugBehavior>
