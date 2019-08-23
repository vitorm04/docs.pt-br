---
title: <windows>do <clientCredentials> elemento
ms.date: 03/30/2017
ms.assetid: 793e41c2-31ea-4159-abbc-2123bf097233
ms.openlocfilehash: e9f0ed9879cc42ea25b83e6b626139a40a593112
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940304"
---
# <a name="windows-of-clientcredentials-element"></a><span data-ttu-id="f1049-102">\<> do Windows \<do elemento > ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="f1049-102">\<windows> of \<clientCredentials> Element</span></span>
<span data-ttu-id="f1049-103">Especifica as configurações para uma credencial do Windows a ser usada para representar o cliente.</span><span class="sxs-lookup"><span data-stu-id="f1049-103">Specifies the settings for a Windows credential to be used to represent the client.</span></span>  
  
 <span data-ttu-id="f1049-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f1049-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f1049-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="f1049-105">\<behaviors></span></span>  
<span data-ttu-id="f1049-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="f1049-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="f1049-107">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="f1049-107">\<behavior></span></span>  
<span data-ttu-id="f1049-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="f1049-108">\<clientCredentials></span></span>  
<span data-ttu-id="f1049-109">\<windows></span><span class="sxs-lookup"><span data-stu-id="f1049-109">\<windows></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1049-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f1049-110">Syntax</span></span>  
  
```xml  
<windows allowedImpersonationLevel="Identification/Impersonation/Delegation/Anonymous/None"
         allowNtlm="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f1049-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f1049-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f1049-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f1049-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f1049-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="f1049-113">Attributes</span></span>  
  
|<span data-ttu-id="f1049-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="f1049-114">Attribute</span></span>|<span data-ttu-id="f1049-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="f1049-115">Description</span></span>|  
|---------------|-----------------|  
|`allowedImpersonationLevel`|<span data-ttu-id="f1049-116">Define a preferência de representação que o cliente se comunica com o servidor.</span><span class="sxs-lookup"><span data-stu-id="f1049-116">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="f1049-117">O modo de representação que o cliente seleciona não é imposto no servidor.</span><span class="sxs-lookup"><span data-stu-id="f1049-117">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="f1049-118">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f1049-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f1049-119">ID O servidor pode obter a identidade e os privilégios do cliente, mas não pode representar o cliente.</span><span class="sxs-lookup"><span data-stu-id="f1049-119">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="f1049-120">Representação O servidor pode representar o contexto de segurança do cliente no sistema local.</span><span class="sxs-lookup"><span data-stu-id="f1049-120">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="f1049-121">Delegação O servidor pode representar o contexto de segurança do cliente em sistemas remotos.</span><span class="sxs-lookup"><span data-stu-id="f1049-121">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="f1049-122">Modo O servidor não pode representar ou identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="f1049-122">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="f1049-123">None Não há um nível de representação atribuído.</span><span class="sxs-lookup"><span data-stu-id="f1049-123">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="f1049-124">O padrão é identificação.</span><span class="sxs-lookup"><span data-stu-id="f1049-124">The default is Identification.</span></span> <span data-ttu-id="f1049-125">Esse atributo é do tipo <xref:System.Security.Principal.TokenImpersonationLevel>.</span><span class="sxs-lookup"><span data-stu-id="f1049-125">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
|`allowNtlm`|<span data-ttu-id="f1049-126">Definir essa propriedade como `true` permite que a autenticação faça downgrade para NTLM se o Kerberos não estiver disponível.</span><span class="sxs-lookup"><span data-stu-id="f1049-126">Setting this property to `true` allows authentication to downgrade to NTLM if Kerberos is not available.</span></span><br /><br /> <span data-ttu-id="f1049-127">Definir essa propriedade como `false` faz com que o Windows Communication Foundation (WCF) faça um melhor esforço para gerar uma exceção se o NTLM for usado.</span><span class="sxs-lookup"><span data-stu-id="f1049-127">Setting this property to `false` causes Windows Communication Foundation (WCF) to make a best-effort to throw an exception if NTLM is used.</span></span> <span data-ttu-id="f1049-128">Observe que a definição dessa propriedade `false` como pode não impedir que credenciais NTLM sejam enviadas pela conexão.</span><span class="sxs-lookup"><span data-stu-id="f1049-128">Note that setting this property to `false` may not prevent NTLM credentials from being sent over the wire.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f1049-129">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f1049-129">Child Elements</span></span>  
 <span data-ttu-id="f1049-130">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="f1049-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f1049-131">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f1049-131">Parent Elements</span></span>  
  
|<span data-ttu-id="f1049-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="f1049-132">Element</span></span>|<span data-ttu-id="f1049-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="f1049-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f1049-134">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="f1049-134">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="f1049-135">Especifica as credenciais usadas para autenticar o cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="f1049-135">Specifies the credentials used to authenticate the client to the service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f1049-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f1049-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.WindowsClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Windows%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- [<span data-ttu-id="f1049-137">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="f1049-137">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="f1049-138">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="f1049-138">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="f1049-139">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="f1049-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
