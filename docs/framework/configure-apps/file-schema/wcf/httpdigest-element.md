---
title: '&lt;httpDigest&gt; Element'
ms.date: 03/30/2017
ms.assetid: 3da4f276-dfd9-4247-8c07-01d83618727c
ms.openlocfilehash: 146260a8f4b51ec51e749408b8351c7e71debab1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54510605"
---
# <a name="lthttpdigestgt-element"></a><span data-ttu-id="3a429-102">&lt;httpDigest&gt; Element</span><span class="sxs-lookup"><span data-stu-id="3a429-102">&lt;httpDigest&gt; Element</span></span>
<span data-ttu-id="3a429-103">Especifica um resumo de tipo de credencial usada para autenticar o cliente a um serviço.</span><span class="sxs-lookup"><span data-stu-id="3a429-103">Specifies a digest type credential used when authenticating the client to a service.</span></span>  
  
 <span data-ttu-id="3a429-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3a429-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="3a429-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="3a429-105">\<behaviors></span></span>  
<span data-ttu-id="3a429-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="3a429-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="3a429-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="3a429-107">\<behavior></span></span>  
<span data-ttu-id="3a429-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="3a429-108">\<clientCredentials></span></span>  
<span data-ttu-id="3a429-109">\<httpDigest></span><span class="sxs-lookup"><span data-stu-id="3a429-109">\<httpDigest></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a429-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3a429-110">Syntax</span></span>  
  
```xml  
<digest impersonationLevel="Identification/Impersonation/Delegation/Anonymous/None" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3a429-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3a429-111">Attributes and Elements</span></span>  
 <span data-ttu-id="3a429-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3a429-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3a429-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="3a429-113">Attributes</span></span>  
  
|<span data-ttu-id="3a429-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="3a429-114">Attribute</span></span>|<span data-ttu-id="3a429-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="3a429-115">Description</span></span>|  
|---------------|-----------------|  
|`impersonationLevel`|<span data-ttu-id="3a429-116">Define a preferência de representação que o cliente se comunica com o servidor.</span><span class="sxs-lookup"><span data-stu-id="3a429-116">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="3a429-117">O modo de representação que o cliente seleciona não é imposto no servidor.</span><span class="sxs-lookup"><span data-stu-id="3a429-117">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="3a429-118">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="3a429-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="3a429-119">-Identificação: O servidor pode obter a identidade e os privilégios do cliente, mas não pode representar o cliente.</span><span class="sxs-lookup"><span data-stu-id="3a429-119">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="3a429-120">-Representação: O servidor pode representar o contexto de segurança do cliente no sistema local.</span><span class="sxs-lookup"><span data-stu-id="3a429-120">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="3a429-121">-Delegação: O servidor pode representar o contexto de segurança do cliente em sistemas remotos.</span><span class="sxs-lookup"><span data-stu-id="3a429-121">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="3a429-122">-Anônimo: O servidor não pode representar ou identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="3a429-122">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="3a429-123">-None: Não há um nível de representação atribuído.</span><span class="sxs-lookup"><span data-stu-id="3a429-123">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="3a429-124">O padrão é a identificação.</span><span class="sxs-lookup"><span data-stu-id="3a429-124">The default is Identification.</span></span> <span data-ttu-id="3a429-125">Esse atributo é do tipo <xref:System.Security.Principal.TokenImpersonationLevel>.</span><span class="sxs-lookup"><span data-stu-id="3a429-125">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3a429-126">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3a429-126">Child Elements</span></span>  
 <span data-ttu-id="3a429-127">Nenhum</span><span class="sxs-lookup"><span data-stu-id="3a429-127">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3a429-128">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3a429-128">Parent Elements</span></span>  
  
|<span data-ttu-id="3a429-129">Elemento</span><span class="sxs-lookup"><span data-stu-id="3a429-129">Element</span></span>|<span data-ttu-id="3a429-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="3a429-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3a429-131">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="3a429-131">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="3a429-132">Especifica as credenciais usadas para autenticar um cliente para um serviço.</span><span class="sxs-lookup"><span data-stu-id="3a429-132">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a429-133">Comentários</span><span class="sxs-lookup"><span data-stu-id="3a429-133">Remarks</span></span>  
 <span data-ttu-id="3a429-134">Um resumo é um hash determinado por meio de um algoritmo e um conjunto de entradas.</span><span class="sxs-lookup"><span data-stu-id="3a429-134">A digest is a hash determined by using an algorithm and a set of inputs.</span></span> <span data-ttu-id="3a429-135">O autenticador e o autenticado concordem com um algoritmo e os dados usados como entradas do exchange.</span><span class="sxs-lookup"><span data-stu-id="3a429-135">The authenticator and the authenticated agree upon an algorithm and exchange the data used as inputs.</span></span> <span data-ttu-id="3a429-136">O cliente pode calcular o hash e enviá-lo para o serviço.</span><span class="sxs-lookup"><span data-stu-id="3a429-136">The client can calculate the hash and send it to the service.</span></span> <span data-ttu-id="3a429-137">O serviço também calcula o hash e compara os valores.</span><span class="sxs-lookup"><span data-stu-id="3a429-137">The service also calculates the hash and compares the values.</span></span> <span data-ttu-id="3a429-138">Uma correspondência valida o cliente.</span><span class="sxs-lookup"><span data-stu-id="3a429-138">A match validates the client.</span></span>  
  
 <span data-ttu-id="3a429-139">Esse recurso deve ser habilitado com o Active Directory no Windows e serviços de informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="3a429-139">This feature must be enabled with Active Directory on Windows and Internet Information Services (IIS).</span></span> <span data-ttu-id="3a429-140">Para obter mais informações, consulte [a autenticação Digest no IIS 6.0](https://go.microsoft.com/fwlink/?LinkId=88443).</span><span class="sxs-lookup"><span data-stu-id="3a429-140">For more information, see [Digest Authentication in IIS 6.0](https://go.microsoft.com/fwlink/?LinkId=88443).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a429-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3a429-141">See also</span></span>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.HttpDigest%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>
- <xref:System.ServiceModel.Configuration.HttpDigestClientElement>
- <xref:System.ServiceModel.Security.HttpDigestClientCredential>
- [<span data-ttu-id="3a429-142">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="3a429-142">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="3a429-143">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="3a429-143">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="3a429-144">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="3a429-144">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="3a429-145">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="3a429-145">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
