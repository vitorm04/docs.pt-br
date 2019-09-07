---
title: Elemento <httpDigest>
ms.date: 03/30/2017
ms.assetid: 3da4f276-dfd9-4247-8c07-01d83618727c
ms.openlocfilehash: f392ebf4eeb6a008952fd4d5ef4e301e57f6eb31
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397988"
---
# <a name="httpdigest-element"></a><span data-ttu-id="8f98b-102">\<Elemento de > httpDigest</span><span class="sxs-lookup"><span data-stu-id="8f98b-102">\<httpDigest> Element</span></span>
<span data-ttu-id="8f98b-103">Especifica uma credencial de tipo Digest usada ao autenticar o cliente para um serviço.</span><span class="sxs-lookup"><span data-stu-id="8f98b-103">Specifies a digest type credential used when authenticating the client to a service.</span></span>  
  
<span data-ttu-id="8f98b-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8f98b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8f98b-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="8f98b-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="8f98b-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="8f98b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="8f98b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> endpointBehaviors**](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="8f98b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="8f98b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="8f98b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="8f98b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="8f98b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="8f98b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> httpDigest**</span><span class="sxs-lookup"><span data-stu-id="8f98b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpDigest>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f98b-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8f98b-111">Syntax</span></span>  
  
```xml  
<digest impersonationLevel="Identification/Impersonation/Delegation/Anonymous/None" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8f98b-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8f98b-112">Attributes and Elements</span></span>  
 <span data-ttu-id="8f98b-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8f98b-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8f98b-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="8f98b-114">Attributes</span></span>  
  
|<span data-ttu-id="8f98b-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="8f98b-115">Attribute</span></span>|<span data-ttu-id="8f98b-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="8f98b-116">Description</span></span>|  
|---------------|-----------------|  
|`impersonationLevel`|<span data-ttu-id="8f98b-117">Define a preferência de representação que o cliente se comunica com o servidor.</span><span class="sxs-lookup"><span data-stu-id="8f98b-117">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="8f98b-118">O modo de representação que o cliente seleciona não é imposto no servidor.</span><span class="sxs-lookup"><span data-stu-id="8f98b-118">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="8f98b-119">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="8f98b-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="8f98b-120">ID O servidor pode obter a identidade e os privilégios do cliente, mas não pode representar o cliente.</span><span class="sxs-lookup"><span data-stu-id="8f98b-120">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="8f98b-121">Representação O servidor pode representar o contexto de segurança do cliente no sistema local.</span><span class="sxs-lookup"><span data-stu-id="8f98b-121">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="8f98b-122">Delegação O servidor pode representar o contexto de segurança do cliente em sistemas remotos.</span><span class="sxs-lookup"><span data-stu-id="8f98b-122">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="8f98b-123">Modo O servidor não pode representar ou identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="8f98b-123">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="8f98b-124">None Não há um nível de representação atribuído.</span><span class="sxs-lookup"><span data-stu-id="8f98b-124">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="8f98b-125">O padrão é identificação.</span><span class="sxs-lookup"><span data-stu-id="8f98b-125">The default is Identification.</span></span> <span data-ttu-id="8f98b-126">Esse atributo é do tipo <xref:System.Security.Principal.TokenImpersonationLevel>.</span><span class="sxs-lookup"><span data-stu-id="8f98b-126">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8f98b-127">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8f98b-127">Child Elements</span></span>  
 <span data-ttu-id="8f98b-128">Nenhum</span><span class="sxs-lookup"><span data-stu-id="8f98b-128">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8f98b-129">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8f98b-129">Parent Elements</span></span>  
  
|<span data-ttu-id="8f98b-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="8f98b-130">Element</span></span>|<span data-ttu-id="8f98b-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="8f98b-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8f98b-132">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="8f98b-132">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="8f98b-133">Especifica as credenciais usadas para autenticar um cliente para um serviço.</span><span class="sxs-lookup"><span data-stu-id="8f98b-133">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8f98b-134">Comentários</span><span class="sxs-lookup"><span data-stu-id="8f98b-134">Remarks</span></span>  
 <span data-ttu-id="8f98b-135">Um resumo é um hash determinado pelo uso de um algoritmo e um conjunto de entradas.</span><span class="sxs-lookup"><span data-stu-id="8f98b-135">A digest is a hash determined by using an algorithm and a set of inputs.</span></span> <span data-ttu-id="8f98b-136">O autenticador e o concorda autenticado sobre um algoritmo e trocam os dados usados como entradas.</span><span class="sxs-lookup"><span data-stu-id="8f98b-136">The authenticator and the authenticated agree upon an algorithm and exchange the data used as inputs.</span></span> <span data-ttu-id="8f98b-137">O cliente pode calcular o hash e enviá-lo para o serviço.</span><span class="sxs-lookup"><span data-stu-id="8f98b-137">The client can calculate the hash and send it to the service.</span></span> <span data-ttu-id="8f98b-138">O serviço também calcula o hash e compara os valores.</span><span class="sxs-lookup"><span data-stu-id="8f98b-138">The service also calculates the hash and compares the values.</span></span> <span data-ttu-id="8f98b-139">Uma correspondência valida o cliente.</span><span class="sxs-lookup"><span data-stu-id="8f98b-139">A match validates the client.</span></span>  
  
 <span data-ttu-id="8f98b-140">Esse recurso deve ser habilitado com Active Directory no Windows e no Serviços de Informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="8f98b-140">This feature must be enabled with Active Directory on Windows and Internet Information Services (IIS).</span></span> <span data-ttu-id="8f98b-141">Para obter mais informações, consulte [autenticação Digest no IIS 6,0](https://go.microsoft.com/fwlink/?LinkId=88443).</span><span class="sxs-lookup"><span data-stu-id="8f98b-141">For more information, see [Digest Authentication in IIS 6.0](https://go.microsoft.com/fwlink/?LinkId=88443).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f98b-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8f98b-142">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.HttpDigest%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>
- <xref:System.ServiceModel.Configuration.HttpDigestClientElement>
- <xref:System.ServiceModel.Security.HttpDigestClientCredential>
- [<span data-ttu-id="8f98b-143">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="8f98b-143">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="8f98b-144">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="8f98b-144">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="8f98b-145">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="8f98b-145">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="8f98b-146">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="8f98b-146">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
