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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5c829f68fe994b47fe880febb4d3ac2020fde2d1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="servicedebugbehavior"></a><span data-ttu-id="23ea4-102">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="23ea4-102">ServiceDebugBehavior</span></span>
<span data-ttu-id="23ea4-103">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="23ea4-103">ServiceDebugBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23ea4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="23ea4-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="23ea4-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="23ea4-105">Methods</span></span>  
 <span data-ttu-id="23ea4-106">A classe ServiceDebugBehavior não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="23ea4-106">The ServiceDebugBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="23ea4-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="23ea4-107">Properties</span></span>  
 <span data-ttu-id="23ea4-108">A classe ServiceDebugBehavior tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="23ea4-108">The ServiceDebugBehavior class has the following properties:</span></span>  
  
### <a name="httphelppageenabled"></a><span data-ttu-id="23ea4-109">httpHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="23ea4-109">HttpHelpPageEnabled</span></span>  
 <span data-ttu-id="23ea4-110">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="23ea4-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="23ea4-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="23ea4-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="23ea4-112">Controla se o serviço publica seu WSDL no endereço controlado pelo `HttpGetUrl` atributo.</span><span class="sxs-lookup"><span data-stu-id="23ea4-112">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httphelppageurl"></a><span data-ttu-id="23ea4-113">httpHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="23ea4-113">HttpHelpPageUrl</span></span>  
 <span data-ttu-id="23ea4-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="23ea4-114">Data type: string</span></span>  
  
 <span data-ttu-id="23ea4-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="23ea4-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="23ea4-116">Define o local no qual o serviço WSDL é publicado para recuperação usando HTTP.</span><span class="sxs-lookup"><span data-stu-id="23ea4-116">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpshelppageenabled"></a><span data-ttu-id="23ea4-117">httpsHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="23ea4-117">HttpsHelpPageEnabled</span></span>  
 <span data-ttu-id="23ea4-118">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="23ea4-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="23ea4-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="23ea4-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="23ea4-120">Controla se o serviço publica seu WSDL em HTTPS no endereço controlado pelo `HttpsGetUrl` atributo.</span><span class="sxs-lookup"><span data-stu-id="23ea4-120">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpshelppageurl"></a><span data-ttu-id="23ea4-121">httpsHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="23ea4-121">HttpsHelpPageUrl</span></span>  
 <span data-ttu-id="23ea4-122">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="23ea4-122">Data type: string</span></span>  
  
 <span data-ttu-id="23ea4-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="23ea4-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="23ea4-124">Define o local no qual o serviço WSDL é publicado para recuperação usando HTTPS.</span><span class="sxs-lookup"><span data-stu-id="23ea4-124">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="23ea4-125">includeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="23ea4-125">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="23ea4-126">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="23ea4-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="23ea4-127">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="23ea4-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="23ea4-128">Especifica se deve incluir informações de exceção gerenciada no detalhe de falhas SOAP retornadas aos clientes para fins de depuração.</span><span class="sxs-lookup"><span data-stu-id="23ea4-128">Specifies whether to include managed exception information in the detail of SOAP faults returned to the clients for debugging purposes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23ea4-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="23ea4-129">Requirements</span></span>  
  
|<span data-ttu-id="23ea4-130">MOF</span><span class="sxs-lookup"><span data-stu-id="23ea4-130">MOF</span></span>|<span data-ttu-id="23ea4-131">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="23ea4-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="23ea4-132">Namespace</span><span class="sxs-lookup"><span data-stu-id="23ea4-132">Namespace</span></span>|<span data-ttu-id="23ea4-133">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="23ea4-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="23ea4-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="23ea4-134">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceDebugBehavior>
