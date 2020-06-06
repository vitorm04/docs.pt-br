---
title: <rsa>
ms.date: 03/30/2017
ms.assetid: ae1f2267-e40d-42ff-8abf-06ab7067bdb9
ms.openlocfilehash: 0e1651f563bdb2b2b24eacacf7bfe387e33a82c7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855050"
---
# \<rsa>
<span data-ttu-id="eb3ac-101">Um cliente WCF seguro que se conecta a um ponto de extremidade com essa identidade verifica se as declarações apresentadas pelo servidor contêm uma declaração que contém a chave pública RSA usada para construir essa identidade.</span><span class="sxs-lookup"><span data-stu-id="eb3ac-101">A secure WCF client that connects to an endpoint with this identity verifies that the claims presented by the server contain a claim that contains the RSA public key used to construct this identity.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<rsa>**  
  
## <a name="syntax"></a><span data-ttu-id="eb3ac-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eb3ac-102">Syntax</span></span>  
  
```xml  
<rsa value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eb3ac-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="eb3ac-103">Attributes and Elements</span></span>  
 <span data-ttu-id="eb3ac-104">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="eb3ac-104">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eb3ac-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="eb3ac-105">Attributes</span></span>  
  
|<span data-ttu-id="eb3ac-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="eb3ac-106">Attribute</span></span>|<span data-ttu-id="eb3ac-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="eb3ac-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="eb3ac-108">value</span><span class="sxs-lookup"><span data-stu-id="eb3ac-108">value</span></span>|<span data-ttu-id="eb3ac-109">Cadeia de caracteres opcional.</span><span class="sxs-lookup"><span data-stu-id="eb3ac-109">Optional String.</span></span> <span data-ttu-id="eb3ac-110">O valor da chave pública RSA a ser comparado no cliente.</span><span class="sxs-lookup"><span data-stu-id="eb3ac-110">The RSA public key value to be compared with on the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eb3ac-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="eb3ac-111">Child Elements</span></span>  
 <span data-ttu-id="eb3ac-112">Nenhum</span><span class="sxs-lookup"><span data-stu-id="eb3ac-112">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="eb3ac-113">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="eb3ac-113">Parent Elements</span></span>  
  
|<span data-ttu-id="eb3ac-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="eb3ac-114">Element</span></span>|<span data-ttu-id="eb3ac-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="eb3ac-115">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="eb3ac-116">Especifica a identidade do serviço a ser autenticado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="eb3ac-116">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb3ac-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="eb3ac-117">Remarks</span></span>  
 <span data-ttu-id="eb3ac-118">Uma verificação RSA permite restringir especificamente a autenticação a um único certificado com base em sua chave RSA ou gerar seu próprio valor de chave RSA.</span><span class="sxs-lookup"><span data-stu-id="eb3ac-118">A RSA check enables you to specifically restrict authentication to a single certificate based upon its RSA key or generated your own RSA key value.</span></span> <span data-ttu-id="eb3ac-119">Isso permite a autenticação mais estrita de uma chave RSA específica na despesa do serviço que não está mais funcionando com os clientes existentes se o valor da chave RSA for alterado.</span><span class="sxs-lookup"><span data-stu-id="eb3ac-119">This enables stricter authentication of a specific RSA key at the expense of the service no longer working with existing clients if the RSA key value is changed.</span></span>  
  
 <span data-ttu-id="eb3ac-120">Para obter mais informações sobre como usar a identidade para validar um serviço para um cliente, consulte [identidade e autenticação de serviço](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="eb3ac-120">For more information about using identity to validate a service to a client, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb3ac-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="eb3ac-121">Example</span></span>  
 <span data-ttu-id="eb3ac-122">O código de configuração a seguir especifica o valor de chave pública de um certificado X. 509 que é usado para autenticar um servidor.</span><span class="sxs-lookup"><span data-stu-id="eb3ac-122">The following configuration code specifies the public key value of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <rsa value="0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="eb3ac-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="eb3ac-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.RsaEndpointIdentity>
- [<span data-ttu-id="eb3ac-124">Identidade e autenticação de serviço</span><span class="sxs-lookup"><span data-stu-id="eb3ac-124">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
