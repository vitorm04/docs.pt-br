---
title: <userPrincipalName>
ms.date: 03/30/2017
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
ms.openlocfilehash: 299af8c4a013d17d7c5b7285f6fb89892c4164a8
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854827"
---
# <a name="userprincipalname"></a><span data-ttu-id="a8e26-101">\<userPrincipalName></span><span class="sxs-lookup"><span data-stu-id="a8e26-101">\<userPrincipalName></span></span>
<span data-ttu-id="a8e26-102">Especifica o nome principal do usuário (UPN) de um serviço a ser autenticado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="a8e26-102">Specifies the User Principal Name (UPN) of a service to be authenticated by the client.</span></span>  
  
<span data-ttu-id="a8e26-103">Para obter mais informações sobre como definir o UPN, consulte [identidade de serviço e autenticação](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="a8e26-103">For more information about setting the UPN, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
<span data-ttu-id="a8e26-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a8e26-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a8e26-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="a8e26-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a8e26-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> do cliente**](client.md)</span><span class="sxs-lookup"><span data-stu-id="a8e26-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="a8e26-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> do ponto de extremidade**](endpoint-of-client.md)</span><span class="sxs-lookup"><span data-stu-id="a8e26-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)</span></span>\
<span data-ttu-id="a8e26-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de identidade**](identity.md)</span><span class="sxs-lookup"><span data-stu-id="a8e26-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)</span></span>\
<span data-ttu-id="a8e26-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> userPrincipalName**</span><span class="sxs-lookup"><span data-stu-id="a8e26-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userPrincipalName>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8e26-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a8e26-110">Syntax</span></span>  
  
```xml  
<userPrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a8e26-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a8e26-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a8e26-112">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="a8e26-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a8e26-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="a8e26-113">Attributes</span></span>  
  
|<span data-ttu-id="a8e26-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="a8e26-114">Attribute</span></span>|<span data-ttu-id="a8e26-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="a8e26-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a8e26-116">value</span><span class="sxs-lookup"><span data-stu-id="a8e26-116">value</span></span>|<span data-ttu-id="a8e26-117">Um nome de conta de usuário (às vezes chamado de nome de logon do usuário) e um nome de domínio que identifica o domínio no qual a conta de usuário está localizada.</span><span class="sxs-lookup"><span data-stu-id="a8e26-117">A user account name (sometimes referred to as the user logon name) and a domain name identifying the domain in which the user account is located.</span></span> <span data-ttu-id="a8e26-118">Esse é o uso padrão para fazer logon em um domínio do Windows.</span><span class="sxs-lookup"><span data-stu-id="a8e26-118">This is the standard usage for logging on to a Windows domain.</span></span> <span data-ttu-id="a8e26-119">O formato é: someone@example.com (como para um endereço de email).</span><span class="sxs-lookup"><span data-stu-id="a8e26-119">The format is: someone@example.com (as for an email address).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a8e26-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a8e26-120">Child Elements</span></span>  
 <span data-ttu-id="a8e26-121">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="a8e26-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a8e26-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a8e26-122">Parent Elements</span></span>  
  
|<span data-ttu-id="a8e26-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="a8e26-123">Element</span></span>|<span data-ttu-id="a8e26-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="a8e26-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a8e26-125">\<identity></span><span class="sxs-lookup"><span data-stu-id="a8e26-125">\<identity></span></span>](identity.md)|<span data-ttu-id="a8e26-126">Especifica a identidade do serviço a ser autenticado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="a8e26-126">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a8e26-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="a8e26-127">Remarks</span></span>  
 <span data-ttu-id="a8e26-128">Um cliente de Windows Communication Foundation seguro (WCF) que se conecta a um ponto de extremidade com essa identidade usa o UPN ao executar a autenticação SSPI com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="a8e26-128">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the UPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8e26-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a8e26-129">Example</span></span>  
 <span data-ttu-id="a8e26-130">O código de configuração a seguir especifica o UPN do serviço a ser autenticado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="a8e26-130">The following configuration code specifies the UPN of the service to be authenticated by the client.</span></span>  
  
```xml  
<identity>
  <userPrincipalName value="someone@cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="a8e26-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a8e26-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.UpnEndpointIdentity>
- [<span data-ttu-id="a8e26-132">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="a8e26-132">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="a8e26-133">\<identity></span><span class="sxs-lookup"><span data-stu-id="a8e26-133">\<identity></span></span>](identity.md)
