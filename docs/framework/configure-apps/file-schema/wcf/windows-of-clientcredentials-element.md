---
title: '&lt;windows&gt; do elemento &lt;clientCredentials&gt;'
ms.date: 03/30/2017
ms.assetid: 793e41c2-31ea-4159-abbc-2123bf097233
ms.openlocfilehash: 780d73b747feae5495ad08cb2324e7d8f8de0d7d
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147467"
---
# <a name="ltwindowsgt-of-ltclientcredentialsgt-element"></a><span data-ttu-id="9589d-102">&lt;windows&gt; do elemento &lt;clientCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="9589d-102">&lt;windows&gt; of &lt;clientCredentials&gt; Element</span></span>
<span data-ttu-id="9589d-103">Especifica as configurações para uma credencial do Windows a ser usado para representar o cliente.</span><span class="sxs-lookup"><span data-stu-id="9589d-103">Specifies the settings for a Windows credential to be used to represent the client.</span></span>  
  
 <span data-ttu-id="9589d-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9589d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="9589d-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="9589d-105">\<behaviors></span></span>  
<span data-ttu-id="9589d-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="9589d-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="9589d-107">\<comportamento de ></span><span class="sxs-lookup"><span data-stu-id="9589d-107">\<behavior></span></span>  
<span data-ttu-id="9589d-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="9589d-108">\<clientCredentials></span></span>  
<span data-ttu-id="9589d-109">\<Windows ></span><span class="sxs-lookup"><span data-stu-id="9589d-109">\<windows></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9589d-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9589d-110">Syntax</span></span>  
  
```xml  
<windows allowedImpersonationLevel="Identification/Impersonation/Delegation/Anonymous/None"
         allowNtlm="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9589d-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9589d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="9589d-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9589d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9589d-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="9589d-113">Attributes</span></span>  
  
|<span data-ttu-id="9589d-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="9589d-114">Attribute</span></span>|<span data-ttu-id="9589d-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="9589d-115">Description</span></span>|  
|---------------|-----------------|  
|`allowedImpersonationLevel`|<span data-ttu-id="9589d-116">Define a preferência de representação que o cliente se comunica com o servidor.</span><span class="sxs-lookup"><span data-stu-id="9589d-116">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="9589d-117">O modo de representação que o cliente seleciona não é imposto no servidor.</span><span class="sxs-lookup"><span data-stu-id="9589d-117">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="9589d-118">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="9589d-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="9589d-119">-Identificação: O servidor pode obter a identidade e os privilégios do cliente, mas não pode representar o cliente.</span><span class="sxs-lookup"><span data-stu-id="9589d-119">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="9589d-120">-Representação: O servidor pode representar o contexto de segurança do cliente no sistema local.</span><span class="sxs-lookup"><span data-stu-id="9589d-120">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="9589d-121">-Delegação: O servidor pode representar o contexto de segurança do cliente em sistemas remotos.</span><span class="sxs-lookup"><span data-stu-id="9589d-121">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="9589d-122">-Anônimo: O servidor não pode representar ou identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="9589d-122">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="9589d-123">-None: Não há um nível de representação atribuído.</span><span class="sxs-lookup"><span data-stu-id="9589d-123">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="9589d-124">O padrão é a identificação.</span><span class="sxs-lookup"><span data-stu-id="9589d-124">The default is Identification.</span></span> <span data-ttu-id="9589d-125">Esse atributo é do tipo <xref:System.Security.Principal.TokenImpersonationLevel>.</span><span class="sxs-lookup"><span data-stu-id="9589d-125">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
|`allowNtlm`|<span data-ttu-id="9589d-126">Definir essa propriedade como `true` permite a autenticação rebaixar para NTLM se Kerberos não estiver disponível.</span><span class="sxs-lookup"><span data-stu-id="9589d-126">Setting this property to `true` allows authentication to downgrade to NTLM if Kerberos is not available.</span></span><br /><br /> <span data-ttu-id="9589d-127">Definir essa propriedade como `false` faz com que o Windows Communication Foundation (WCF) para fazer um esforço para lançar uma exceção se NTLM for usado.</span><span class="sxs-lookup"><span data-stu-id="9589d-127">Setting this property to `false` causes Windows Communication Foundation (WCF) to make a best-effort to throw an exception if NTLM is used.</span></span> <span data-ttu-id="9589d-128">Observe que a definição dessa propriedade `false` talvez não impeçam que as credenciais do NTLM sejam enviados durante a transmissão.</span><span class="sxs-lookup"><span data-stu-id="9589d-128">Note that setting this property to `false` may not prevent NTLM credentials from being sent over the wire.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9589d-129">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9589d-129">Child Elements</span></span>  
 <span data-ttu-id="9589d-130">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="9589d-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9589d-131">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9589d-131">Parent Elements</span></span>  
  
|<span data-ttu-id="9589d-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="9589d-132">Element</span></span>|<span data-ttu-id="9589d-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="9589d-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9589d-134">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="9589d-134">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="9589d-135">Especifica as credenciais usadas para autenticar o cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="9589d-135">Specifies the credentials used to authenticate the client to the service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9589d-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9589d-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WindowsClientElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Windows%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>  
 <xref:System.ServiceModel.Security.WindowsClientCredential>  
 [<span data-ttu-id="9589d-137">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="9589d-137">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="9589d-138">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="9589d-138">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="9589d-139">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="9589d-139">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
