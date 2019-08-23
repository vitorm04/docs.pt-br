---
title: Elemento <httpDigest>
ms.date: 03/30/2017
ms.assetid: 3da4f276-dfd9-4247-8c07-01d83618727c
ms.openlocfilehash: 2ceefdd7fab82025e89ad08d8423d57524c2e4d8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925557"
---
# <a name="httpdigest-element"></a><span data-ttu-id="211f4-102">\<Elemento de > httpDigest</span><span class="sxs-lookup"><span data-stu-id="211f4-102">\<httpDigest> Element</span></span>
<span data-ttu-id="211f4-103">Especifica uma credencial de tipo Digest usada ao autenticar o cliente para um serviço.</span><span class="sxs-lookup"><span data-stu-id="211f4-103">Specifies a digest type credential used when authenticating the client to a service.</span></span>  
  
 <span data-ttu-id="211f4-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="211f4-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="211f4-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="211f4-105">\<behaviors></span></span>  
<span data-ttu-id="211f4-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="211f4-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="211f4-107">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="211f4-107">\<behavior></span></span>  
<span data-ttu-id="211f4-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="211f4-108">\<clientCredentials></span></span>  
<span data-ttu-id="211f4-109">\<httpDigest></span><span class="sxs-lookup"><span data-stu-id="211f4-109">\<httpDigest></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="211f4-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="211f4-110">Syntax</span></span>  
  
```xml  
<digest impersonationLevel="Identification/Impersonation/Delegation/Anonymous/None" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="211f4-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="211f4-111">Attributes and Elements</span></span>  
 <span data-ttu-id="211f4-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="211f4-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="211f4-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="211f4-113">Attributes</span></span>  
  
|<span data-ttu-id="211f4-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="211f4-114">Attribute</span></span>|<span data-ttu-id="211f4-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="211f4-115">Description</span></span>|  
|---------------|-----------------|  
|`impersonationLevel`|<span data-ttu-id="211f4-116">Define a preferência de representação que o cliente se comunica com o servidor.</span><span class="sxs-lookup"><span data-stu-id="211f4-116">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="211f4-117">O modo de representação que o cliente seleciona não é imposto no servidor.</span><span class="sxs-lookup"><span data-stu-id="211f4-117">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="211f4-118">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="211f4-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="211f4-119">ID O servidor pode obter a identidade e os privilégios do cliente, mas não pode representar o cliente.</span><span class="sxs-lookup"><span data-stu-id="211f4-119">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="211f4-120">Representação O servidor pode representar o contexto de segurança do cliente no sistema local.</span><span class="sxs-lookup"><span data-stu-id="211f4-120">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="211f4-121">Delegação O servidor pode representar o contexto de segurança do cliente em sistemas remotos.</span><span class="sxs-lookup"><span data-stu-id="211f4-121">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="211f4-122">Modo O servidor não pode representar ou identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="211f4-122">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="211f4-123">None Não há um nível de representação atribuído.</span><span class="sxs-lookup"><span data-stu-id="211f4-123">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="211f4-124">O padrão é identificação.</span><span class="sxs-lookup"><span data-stu-id="211f4-124">The default is Identification.</span></span> <span data-ttu-id="211f4-125">Esse atributo é do tipo <xref:System.Security.Principal.TokenImpersonationLevel>.</span><span class="sxs-lookup"><span data-stu-id="211f4-125">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="211f4-126">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="211f4-126">Child Elements</span></span>  
 <span data-ttu-id="211f4-127">Nenhum</span><span class="sxs-lookup"><span data-stu-id="211f4-127">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="211f4-128">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="211f4-128">Parent Elements</span></span>  
  
|<span data-ttu-id="211f4-129">Elemento</span><span class="sxs-lookup"><span data-stu-id="211f4-129">Element</span></span>|<span data-ttu-id="211f4-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="211f4-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="211f4-131">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="211f4-131">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="211f4-132">Especifica as credenciais usadas para autenticar um cliente para um serviço.</span><span class="sxs-lookup"><span data-stu-id="211f4-132">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="211f4-133">Comentários</span><span class="sxs-lookup"><span data-stu-id="211f4-133">Remarks</span></span>  
 <span data-ttu-id="211f4-134">Um resumo é um hash determinado pelo uso de um algoritmo e um conjunto de entradas.</span><span class="sxs-lookup"><span data-stu-id="211f4-134">A digest is a hash determined by using an algorithm and a set of inputs.</span></span> <span data-ttu-id="211f4-135">O autenticador e o concorda autenticado sobre um algoritmo e trocam os dados usados como entradas.</span><span class="sxs-lookup"><span data-stu-id="211f4-135">The authenticator and the authenticated agree upon an algorithm and exchange the data used as inputs.</span></span> <span data-ttu-id="211f4-136">O cliente pode calcular o hash e enviá-lo para o serviço.</span><span class="sxs-lookup"><span data-stu-id="211f4-136">The client can calculate the hash and send it to the service.</span></span> <span data-ttu-id="211f4-137">O serviço também calcula o hash e compara os valores.</span><span class="sxs-lookup"><span data-stu-id="211f4-137">The service also calculates the hash and compares the values.</span></span> <span data-ttu-id="211f4-138">Uma correspondência valida o cliente.</span><span class="sxs-lookup"><span data-stu-id="211f4-138">A match validates the client.</span></span>  
  
 <span data-ttu-id="211f4-139">Esse recurso deve ser habilitado com Active Directory no Windows e no Serviços de Informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="211f4-139">This feature must be enabled with Active Directory on Windows and Internet Information Services (IIS).</span></span> <span data-ttu-id="211f4-140">Para obter mais informações, consulte [autenticação Digest no IIS 6,0](https://go.microsoft.com/fwlink/?LinkId=88443).</span><span class="sxs-lookup"><span data-stu-id="211f4-140">For more information, see [Digest Authentication in IIS 6.0](https://go.microsoft.com/fwlink/?LinkId=88443).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="211f4-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="211f4-141">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.HttpDigest%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>
- <xref:System.ServiceModel.Configuration.HttpDigestClientElement>
- <xref:System.ServiceModel.Security.HttpDigestClientCredential>
- [<span data-ttu-id="211f4-142">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="211f4-142">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="211f4-143">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="211f4-143">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="211f4-144">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="211f4-144">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="211f4-145">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="211f4-145">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
