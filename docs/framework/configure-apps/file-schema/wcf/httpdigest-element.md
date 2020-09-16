---
title: Elemento <httpDigest>
ms.date: 03/30/2017
ms.assetid: 3da4f276-dfd9-4247-8c07-01d83618727c
ms.openlocfilehash: 0ffaba218d31a77407c598f8b7fa0260daa4e39c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556896"
---
# <a name="httpdigest-element"></a><span data-ttu-id="b1af0-102">Elemento \<httpDigest></span><span class="sxs-lookup"><span data-stu-id="b1af0-102">\<httpDigest> Element</span></span>
<span data-ttu-id="b1af0-103">Especifica uma credencial de tipo Digest usada ao autenticar o cliente para um serviço.</span><span class="sxs-lookup"><span data-stu-id="b1af0-103">Specifies a digest type credential used when authenticating the client to a service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpDigest>**  
  
## <a name="syntax"></a><span data-ttu-id="b1af0-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="b1af0-104">Syntax</span></span>  
  
```xml  
<httpDigest impersonationLevel="Identification/Impersonation/Delegation/Anonymous/None" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b1af0-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b1af0-105">Attributes and Elements</span></span>  
 <span data-ttu-id="b1af0-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b1af0-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b1af0-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="b1af0-107">Attributes</span></span>  
  
|<span data-ttu-id="b1af0-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="b1af0-108">Attribute</span></span>|<span data-ttu-id="b1af0-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="b1af0-109">Description</span></span>|  
|---------------|-----------------|  
|`impersonationLevel`|<span data-ttu-id="b1af0-110">Define a preferência de representação que o cliente se comunica com o servidor.</span><span class="sxs-lookup"><span data-stu-id="b1af0-110">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="b1af0-111">O modo de representação que o cliente seleciona não é imposto no servidor.</span><span class="sxs-lookup"><span data-stu-id="b1af0-111">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="b1af0-112">Os valores válidos incluem os seguintes:</span><span class="sxs-lookup"><span data-stu-id="b1af0-112">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="b1af0-113">-Identificação: o servidor pode obter a identidade e os privilégios do cliente, mas não pode representar o cliente.</span><span class="sxs-lookup"><span data-stu-id="b1af0-113">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="b1af0-114">-Impersonation: o servidor pode representar o contexto de segurança do cliente no sistema local.</span><span class="sxs-lookup"><span data-stu-id="b1af0-114">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="b1af0-115">-Delegation: o servidor pode representar o contexto de segurança do cliente em sistemas remotos.</span><span class="sxs-lookup"><span data-stu-id="b1af0-115">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="b1af0-116">-Anônimo: o servidor não pode representar ou identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="b1af0-116">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="b1af0-117">-Nenhum: um nível de representação não é atribuído.</span><span class="sxs-lookup"><span data-stu-id="b1af0-117">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="b1af0-118">O padrão é identificação.</span><span class="sxs-lookup"><span data-stu-id="b1af0-118">The default is Identification.</span></span> <span data-ttu-id="b1af0-119">Esse atributo é do tipo <xref:System.Security.Principal.TokenImpersonationLevel> .</span><span class="sxs-lookup"><span data-stu-id="b1af0-119">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b1af0-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b1af0-120">Child Elements</span></span>  
 <span data-ttu-id="b1af0-121">Nenhum</span><span class="sxs-lookup"><span data-stu-id="b1af0-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b1af0-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b1af0-122">Parent Elements</span></span>  
  
|<span data-ttu-id="b1af0-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="b1af0-123">Element</span></span>|<span data-ttu-id="b1af0-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="b1af0-124">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="b1af0-125">Especifica as credenciais usadas para autenticar um cliente para um serviço.</span><span class="sxs-lookup"><span data-stu-id="b1af0-125">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1af0-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="b1af0-126">Remarks</span></span>  
 <span data-ttu-id="b1af0-127">Um resumo é um hash determinado pelo uso de um algoritmo e um conjunto de entradas.</span><span class="sxs-lookup"><span data-stu-id="b1af0-127">A digest is a hash determined by using an algorithm and a set of inputs.</span></span> <span data-ttu-id="b1af0-128">O autenticador e o concorda autenticado sobre um algoritmo e trocam os dados usados como entradas.</span><span class="sxs-lookup"><span data-stu-id="b1af0-128">The authenticator and the authenticated agree upon an algorithm and exchange the data used as inputs.</span></span> <span data-ttu-id="b1af0-129">O cliente pode calcular o hash e enviá-lo para o serviço.</span><span class="sxs-lookup"><span data-stu-id="b1af0-129">The client can calculate the hash and send it to the service.</span></span> <span data-ttu-id="b1af0-130">O serviço também calcula o hash e compara os valores.</span><span class="sxs-lookup"><span data-stu-id="b1af0-130">The service also calculates the hash and compares the values.</span></span> <span data-ttu-id="b1af0-131">Uma correspondência valida o cliente.</span><span class="sxs-lookup"><span data-stu-id="b1af0-131">A match validates the client.</span></span>  
  
 <span data-ttu-id="b1af0-132">Esse recurso deve ser habilitado com Active Directory no Windows e no Serviços de Informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="b1af0-132">This feature must be enabled with Active Directory on Windows and Internet Information Services (IIS).</span></span> <span data-ttu-id="b1af0-133">Para obter mais informações, consulte [autenticação Digest no IIS 6,0](/previous-versions/windows/it-pro/windows-server-2003/cc782661(v=ws.10)).</span><span class="sxs-lookup"><span data-stu-id="b1af0-133">For more information, see [Digest Authentication in IIS 6.0](/previous-versions/windows/it-pro/windows-server-2003/cc782661(v=ws.10)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1af0-134">Confira também</span><span class="sxs-lookup"><span data-stu-id="b1af0-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.HttpDigest%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>
- <xref:System.ServiceModel.Configuration.HttpDigestClientElement>
- <xref:System.ServiceModel.Security.HttpDigestClientCredential>
- [<span data-ttu-id="b1af0-135">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="b1af0-135">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="b1af0-136">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="b1af0-136">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="b1af0-137">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="b1af0-137">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="b1af0-138">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="b1af0-138">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
