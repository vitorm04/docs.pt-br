---
title: ServiceDebugBehavior
ms.date: 03/30/2017
ms.assetid: a5ec9061-1e95-43fb-b0d9-dbd0a7bc3c44
ms.openlocfilehash: 76c4992c5364ed9800e58d120c099aceedb2799c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485675"
---
# <a name="servicedebugbehavior"></a><span data-ttu-id="aa3e2-102">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="aa3e2-102">ServiceDebugBehavior</span></span>
<span data-ttu-id="aa3e2-103">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="aa3e2-103">ServiceDebugBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa3e2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="aa3e2-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="aa3e2-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="aa3e2-105">Methods</span></span>  
 <span data-ttu-id="aa3e2-106">A classe ServiceDebugBehavior não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="aa3e2-106">The ServiceDebugBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="aa3e2-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="aa3e2-107">Properties</span></span>  
 <span data-ttu-id="aa3e2-108">A classe ServiceDebugBehavior tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="aa3e2-108">The ServiceDebugBehavior class has the following properties:</span></span>  
  
### <a name="httphelppageenabled"></a><span data-ttu-id="aa3e2-109">httpHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="aa3e2-109">HttpHelpPageEnabled</span></span>  
 <span data-ttu-id="aa3e2-110">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="aa3e2-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="aa3e2-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="aa3e2-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aa3e2-112">Controla se o serviço publica seu WSDL no endereço controlado pelo `HttpGetUrl` atributo.</span><span class="sxs-lookup"><span data-stu-id="aa3e2-112">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httphelppageurl"></a><span data-ttu-id="aa3e2-113">httpHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="aa3e2-113">HttpHelpPageUrl</span></span>  
 <span data-ttu-id="aa3e2-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="aa3e2-114">Data type: string</span></span>  
  
 <span data-ttu-id="aa3e2-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="aa3e2-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aa3e2-116">Define o local no qual o serviço WSDL é publicado para recuperação usando HTTP.</span><span class="sxs-lookup"><span data-stu-id="aa3e2-116">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpshelppageenabled"></a><span data-ttu-id="aa3e2-117">httpsHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="aa3e2-117">HttpsHelpPageEnabled</span></span>  
 <span data-ttu-id="aa3e2-118">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="aa3e2-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="aa3e2-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="aa3e2-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aa3e2-120">Controla se o serviço publica seu WSDL em HTTPS no endereço controlado pelo `HttpsGetUrl` atributo.</span><span class="sxs-lookup"><span data-stu-id="aa3e2-120">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpshelppageurl"></a><span data-ttu-id="aa3e2-121">httpsHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="aa3e2-121">HttpsHelpPageUrl</span></span>  
 <span data-ttu-id="aa3e2-122">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="aa3e2-122">Data type: string</span></span>  
  
 <span data-ttu-id="aa3e2-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="aa3e2-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aa3e2-124">Define o local no qual o serviço WSDL é publicado para recuperação usando HTTPS.</span><span class="sxs-lookup"><span data-stu-id="aa3e2-124">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="aa3e2-125">includeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="aa3e2-125">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="aa3e2-126">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="aa3e2-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="aa3e2-127">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="aa3e2-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aa3e2-128">Especifica se deve incluir informações de exceção gerenciada no detalhe de falhas SOAP retornadas aos clientes para fins de depuração.</span><span class="sxs-lookup"><span data-stu-id="aa3e2-128">Specifies whether to include managed exception information in the detail of SOAP faults returned to the clients for debugging purposes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa3e2-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="aa3e2-129">Requirements</span></span>  
  
|<span data-ttu-id="aa3e2-130">MOF</span><span class="sxs-lookup"><span data-stu-id="aa3e2-130">MOF</span></span>|<span data-ttu-id="aa3e2-131">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="aa3e2-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="aa3e2-132">Namespace</span><span class="sxs-lookup"><span data-stu-id="aa3e2-132">Namespace</span></span>|<span data-ttu-id="aa3e2-133">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="aa3e2-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="aa3e2-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aa3e2-134">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceDebugBehavior>
