---
title: ServiceDebugBehavior
ms.date: 03/30/2017
ms.assetid: a5ec9061-1e95-43fb-b0d9-dbd0a7bc3c44
ms.openlocfilehash: 2e38eb2c2d42ffc5436562b254a42215ccabbab2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59090908"
---
# <a name="servicedebugbehavior"></a><span data-ttu-id="11d06-102">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="11d06-102">ServiceDebugBehavior</span></span>
<span data-ttu-id="11d06-103">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="11d06-103">ServiceDebugBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11d06-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="11d06-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="11d06-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="11d06-105">Methods</span></span>  
 <span data-ttu-id="11d06-106">A classe ServiceDebugBehavior não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="11d06-106">The ServiceDebugBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="11d06-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="11d06-107">Properties</span></span>  
 <span data-ttu-id="11d06-108">A classe ServiceDebugBehavior tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="11d06-108">The ServiceDebugBehavior class has the following properties:</span></span>  
  
### <a name="httphelppageenabled"></a><span data-ttu-id="11d06-109">HttpHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="11d06-109">HttpHelpPageEnabled</span></span>  
 <span data-ttu-id="11d06-110">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="11d06-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="11d06-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="11d06-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="11d06-112">Controla se o serviço publica seu WSDL no endereço controlado pela `HttpGetUrl` atributo.</span><span class="sxs-lookup"><span data-stu-id="11d06-112">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httphelppageurl"></a><span data-ttu-id="11d06-113">HttpHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="11d06-113">HttpHelpPageUrl</span></span>  
 <span data-ttu-id="11d06-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="11d06-114">Data type: string</span></span>  
  
 <span data-ttu-id="11d06-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="11d06-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="11d06-116">Define o local no qual o serviço WSDL é publicado para recuperação usando HTTP.</span><span class="sxs-lookup"><span data-stu-id="11d06-116">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpshelppageenabled"></a><span data-ttu-id="11d06-117">HttpsHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="11d06-117">HttpsHelpPageEnabled</span></span>  
 <span data-ttu-id="11d06-118">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="11d06-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="11d06-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="11d06-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="11d06-120">Controla se o serviço publica seu WSDL via HTTPS no endereço controlado pela `HttpsGetUrl` atributo.</span><span class="sxs-lookup"><span data-stu-id="11d06-120">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpshelppageurl"></a><span data-ttu-id="11d06-121">HttpsHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="11d06-121">HttpsHelpPageUrl</span></span>  
 <span data-ttu-id="11d06-122">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="11d06-122">Data type: string</span></span>  
  
 <span data-ttu-id="11d06-123">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="11d06-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="11d06-124">Define o local no qual o serviço WSDL é publicado para recuperação usando HTTPS.</span><span class="sxs-lookup"><span data-stu-id="11d06-124">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="11d06-125">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="11d06-125">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="11d06-126">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="11d06-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="11d06-127">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="11d06-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="11d06-128">Especifica se deve incluir informações de exceção gerenciada nos detalhes das falhas SOAP retornadas aos clientes para fins de depuração.</span><span class="sxs-lookup"><span data-stu-id="11d06-128">Specifies whether to include managed exception information in the detail of SOAP faults returned to the clients for debugging purposes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11d06-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="11d06-129">Requirements</span></span>  
  
|<span data-ttu-id="11d06-130">MOF</span><span class="sxs-lookup"><span data-stu-id="11d06-130">MOF</span></span>|<span data-ttu-id="11d06-131">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="11d06-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="11d06-132">Namespace</span><span class="sxs-lookup"><span data-stu-id="11d06-132">Namespace</span></span>|<span data-ttu-id="11d06-133">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="11d06-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="11d06-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="11d06-134">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceDebugBehavior>
