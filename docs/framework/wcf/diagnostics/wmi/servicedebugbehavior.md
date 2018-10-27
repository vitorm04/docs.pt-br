---
title: ServiceDebugBehavior
ms.date: 03/30/2017
ms.assetid: a5ec9061-1e95-43fb-b0d9-dbd0a7bc3c44
ms.openlocfilehash: 68b2350f257bc95d8e17f4b9049d67c7f67becae
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2018
ms.locfileid: "49452856"
---
# <a name="servicedebugbehavior"></a><span data-ttu-id="a391d-102">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="a391d-102">ServiceDebugBehavior</span></span>
<span data-ttu-id="a391d-103">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="a391d-103">ServiceDebugBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a391d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a391d-104">Syntax</span></span>  
  
```csharp
class ServiceDebugBehavior : Behavior  
{  
  boolean HttpHelpPageEnabled;  
  string HttpHelpPageUrl;  
  boolean HttpsHelpPageEnabled;  
  string HttpsHelpPageUrl;  
  boolean IncludeExceptionDetailInFaults;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="a391d-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="a391d-105">Methods</span></span>  
 <span data-ttu-id="a391d-106">A classe ServiceDebugBehavior não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="a391d-106">The ServiceDebugBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a391d-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="a391d-107">Properties</span></span>  
 <span data-ttu-id="a391d-108">A classe ServiceDebugBehavior tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="a391d-108">The ServiceDebugBehavior class has the following properties:</span></span>  
  
### <a name="httphelppageenabled"></a><span data-ttu-id="a391d-109">HttpHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="a391d-109">HttpHelpPageEnabled</span></span>  
 <span data-ttu-id="a391d-110">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="a391d-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="a391d-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="a391d-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a391d-112">Controla se o serviço publica seu WSDL no endereço controlado pela `HttpGetUrl` atributo.</span><span class="sxs-lookup"><span data-stu-id="a391d-112">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httphelppageurl"></a><span data-ttu-id="a391d-113">HttpHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="a391d-113">HttpHelpPageUrl</span></span>  
 <span data-ttu-id="a391d-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="a391d-114">Data type: string</span></span>  
  
 <span data-ttu-id="a391d-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="a391d-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a391d-116">Define o local no qual o serviço WSDL é publicado para recuperação usando HTTP.</span><span class="sxs-lookup"><span data-stu-id="a391d-116">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpshelppageenabled"></a><span data-ttu-id="a391d-117">HttpsHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="a391d-117">HttpsHelpPageEnabled</span></span>  
 <span data-ttu-id="a391d-118">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="a391d-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="a391d-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="a391d-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a391d-120">Controla se o serviço publica seu WSDL via HTTPS no endereço controlado pela `HttpsGetUrl` atributo.</span><span class="sxs-lookup"><span data-stu-id="a391d-120">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpshelppageurl"></a><span data-ttu-id="a391d-121">HttpsHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="a391d-121">HttpsHelpPageUrl</span></span>  
 <span data-ttu-id="a391d-122">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="a391d-122">Data type: string</span></span>  
  
 <span data-ttu-id="a391d-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="a391d-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a391d-124">Define o local no qual o serviço WSDL é publicado para recuperação usando HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a391d-124">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="a391d-125">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="a391d-125">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="a391d-126">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="a391d-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="a391d-127">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="a391d-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a391d-128">Especifica se deve incluir informações de exceção gerenciada nos detalhes das falhas SOAP retornadas aos clientes para fins de depuração.</span><span class="sxs-lookup"><span data-stu-id="a391d-128">Specifies whether to include managed exception information in the detail of SOAP faults returned to the clients for debugging purposes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a391d-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a391d-129">Requirements</span></span>  
  
|<span data-ttu-id="a391d-130">MOF</span><span class="sxs-lookup"><span data-stu-id="a391d-130">MOF</span></span>|<span data-ttu-id="a391d-131">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="a391d-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="a391d-132">Namespace</span><span class="sxs-lookup"><span data-stu-id="a391d-132">Namespace</span></span>|<span data-ttu-id="a391d-133">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a391d-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a391d-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a391d-134">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceDebugBehavior>
