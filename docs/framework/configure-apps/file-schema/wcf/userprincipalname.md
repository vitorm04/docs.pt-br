---
title: <userPrincipalName>
ms.date: 03/30/2017
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
ms.openlocfilehash: 299af8c4a013d17d7c5b7285f6fb89892c4164a8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854827"
---
# \<userPrincipalName>
<span data-ttu-id="2a516-101">Especifica o nome principal do usuário (UPN) de um serviço a ser autenticado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="2a516-101">Specifies the User Principal Name (UPN) of a service to be authenticated by the client.</span></span>  
  
<span data-ttu-id="2a516-102">Para obter mais informações sobre como definir o UPN, consulte [identidade de serviço e autenticação](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="2a516-102">For more information about setting the UPN, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userPrincipalName>**  
  
## <a name="syntax"></a><span data-ttu-id="2a516-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2a516-103">Syntax</span></span>  
  
```xml  
<userPrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2a516-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2a516-104">Attributes and Elements</span></span>  
 <span data-ttu-id="2a516-105">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="2a516-105">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2a516-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="2a516-106">Attributes</span></span>  
  
|<span data-ttu-id="2a516-107">Atributo</span><span class="sxs-lookup"><span data-stu-id="2a516-107">Attribute</span></span>|<span data-ttu-id="2a516-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="2a516-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2a516-109">value</span><span class="sxs-lookup"><span data-stu-id="2a516-109">value</span></span>|<span data-ttu-id="2a516-110">Um nome de conta de usuário (às vezes chamado de nome de logon do usuário) e um nome de domínio que identifica o domínio no qual a conta de usuário está localizada.</span><span class="sxs-lookup"><span data-stu-id="2a516-110">A user account name (sometimes referred to as the user logon name) and a domain name identifying the domain in which the user account is located.</span></span> <span data-ttu-id="2a516-111">Esse é o uso padrão para fazer logon em um domínio do Windows.</span><span class="sxs-lookup"><span data-stu-id="2a516-111">This is the standard usage for logging on to a Windows domain.</span></span> <span data-ttu-id="2a516-112">O formato é: someone@example.com (como para um endereço de email).</span><span class="sxs-lookup"><span data-stu-id="2a516-112">The format is: someone@example.com (as for an email address).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2a516-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2a516-113">Child Elements</span></span>  
 <span data-ttu-id="2a516-114">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="2a516-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2a516-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2a516-115">Parent Elements</span></span>  
  
|<span data-ttu-id="2a516-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="2a516-116">Element</span></span>|<span data-ttu-id="2a516-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="2a516-117">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="2a516-118">Especifica a identidade do serviço a ser autenticado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="2a516-118">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a516-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="2a516-119">Remarks</span></span>  
 <span data-ttu-id="2a516-120">Um cliente de Windows Communication Foundation seguro (WCF) que se conecta a um ponto de extremidade com essa identidade usa o UPN ao executar a autenticação SSPI com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="2a516-120">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the UPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a516-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2a516-121">Example</span></span>  
 <span data-ttu-id="2a516-122">O código de configuração a seguir especifica o UPN do serviço a ser autenticado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="2a516-122">The following configuration code specifies the UPN of the service to be authenticated by the client.</span></span>  
  
```xml  
<identity>
  <userPrincipalName value="someone@cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="2a516-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="2a516-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.UpnEndpointIdentity>
- [<span data-ttu-id="2a516-124">Identidade e autenticação de serviço</span><span class="sxs-lookup"><span data-stu-id="2a516-124">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
