---
title: '&lt;windows&gt; do elemento &lt;clientCredentials&gt;'
ms.date: 03/30/2017
ms.assetid: 793e41c2-31ea-4159-abbc-2123bf097233
ms.openlocfilehash: 9badcfafff4bc09a16b0b9a565a9ea5c01e26bb5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32767057"
---
# <a name="ltwindowsgt-of-ltclientcredentialsgt-element"></a><span data-ttu-id="72a5e-102">&lt;windows&gt; do elemento &lt;clientCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="72a5e-102">&lt;windows&gt; of &lt;clientCredentials&gt; Element</span></span>
<span data-ttu-id="72a5e-103">Especifica as configurações para uma credencial do Windows a ser usado para representar o cliente.</span><span class="sxs-lookup"><span data-stu-id="72a5e-103">Specifies the settings for a Windows credential to be used to represent the client.</span></span>  
  
 <span data-ttu-id="72a5e-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="72a5e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="72a5e-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="72a5e-105">\<behaviors></span></span>  
<span data-ttu-id="72a5e-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="72a5e-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="72a5e-107">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="72a5e-107">\<behavior></span></span>  
<span data-ttu-id="72a5e-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="72a5e-108">\<clientCredentials></span></span>  
<span data-ttu-id="72a5e-109">\<Windows ></span><span class="sxs-lookup"><span data-stu-id="72a5e-109">\<windows></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72a5e-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="72a5e-110">Syntax</span></span>  
  
```xml  
<windows   
    allowedImpersonationLevel="Identification/Impersonation/Delegation/Anonymous/None"  
        allowNtlm="Boolean"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="72a5e-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="72a5e-111">Attributes and Elements</span></span>  
 <span data-ttu-id="72a5e-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="72a5e-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="72a5e-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="72a5e-113">Attributes</span></span>  
  
|<span data-ttu-id="72a5e-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="72a5e-114">Attribute</span></span>|<span data-ttu-id="72a5e-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="72a5e-115">Description</span></span>|  
|---------------|-----------------|  
|`allowedImpersonationLevel`|<span data-ttu-id="72a5e-116">Define a preferência de representação que o cliente se comunica com o servidor.</span><span class="sxs-lookup"><span data-stu-id="72a5e-116">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="72a5e-117">O modo de representação que o cliente seleciona não é imposto no servidor.</span><span class="sxs-lookup"><span data-stu-id="72a5e-117">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="72a5e-118">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="72a5e-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="72a5e-119">-Identificação: O servidor pode obter a identidade e os privilégios do cliente, mas não é possível representar o cliente.</span><span class="sxs-lookup"><span data-stu-id="72a5e-119">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="72a5e-120">-Representação: O servidor pode representar o contexto de segurança do cliente no sistema local.</span><span class="sxs-lookup"><span data-stu-id="72a5e-120">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="72a5e-121">-Delegação: O servidor pode representar o contexto de segurança do cliente em sistemas remotos.</span><span class="sxs-lookup"><span data-stu-id="72a5e-121">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="72a5e-122">-Anônima: O servidor não pode representar ou identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="72a5e-122">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="72a5e-123">-Nenhum: Um nível de representação não está atribuído.</span><span class="sxs-lookup"><span data-stu-id="72a5e-123">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="72a5e-124">O padrão é a identificação.</span><span class="sxs-lookup"><span data-stu-id="72a5e-124">The default is Identification.</span></span> <span data-ttu-id="72a5e-125">Esse atributo é do tipo <xref:System.Security.Principal.TokenImpersonationLevel>.</span><span class="sxs-lookup"><span data-stu-id="72a5e-125">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
|`allowNtlm`|<span data-ttu-id="72a5e-126">Definir essa propriedade como `true` permite que a autenticação rebaixar para NTLM se Kerberos não estiver disponível.</span><span class="sxs-lookup"><span data-stu-id="72a5e-126">Setting this property to `true` allows authentication to downgrade to NTLM if Kerberos is not available.</span></span><br /><br /> <span data-ttu-id="72a5e-127">Definir essa propriedade como `false` faz com que o Windows Communication Foundation (WCF) para fazer um esforço para lançar uma exceção se NTLM é usado.</span><span class="sxs-lookup"><span data-stu-id="72a5e-127">Setting this property to `false` causes Windows Communication Foundation (WCF) to make a best-effort to throw an exception if NTLM is used.</span></span> <span data-ttu-id="72a5e-128">Observe que a definição dessa propriedade `false` talvez não impeçam que as credenciais do NTLM seja enviado pela conexão.</span><span class="sxs-lookup"><span data-stu-id="72a5e-128">Note that setting this property to `false` may not prevent NTLM credentials from being sent over the wire.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="72a5e-129">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="72a5e-129">Child Elements</span></span>  
 <span data-ttu-id="72a5e-130">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="72a5e-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="72a5e-131">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="72a5e-131">Parent Elements</span></span>  
  
|<span data-ttu-id="72a5e-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="72a5e-132">Element</span></span>|<span data-ttu-id="72a5e-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="72a5e-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="72a5e-134">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="72a5e-134">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="72a5e-135">Especifica as credenciais usadas para autenticar o cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="72a5e-135">Specifies the credentials used to authenticate the client to the service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="72a5e-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="72a5e-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WindowsClientElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Windows%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>  
 <xref:System.ServiceModel.Security.WindowsClientCredential>  
 [<span data-ttu-id="72a5e-137">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="72a5e-137">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="72a5e-138">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="72a5e-138">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="72a5e-139">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="72a5e-139">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
