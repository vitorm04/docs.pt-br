---
title: <windows>do <clientCredentials> elemento
ms.date: 03/30/2017
ms.assetid: 793e41c2-31ea-4159-abbc-2123bf097233
ms.openlocfilehash: 61ca99213f0b83a5af5df0184a8c1de405366288
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399124"
---
# <a name="windows-of-clientcredentials-element"></a><span data-ttu-id="c64ad-102">\<> do Windows \<do elemento > ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="c64ad-102">\<windows> of \<clientCredentials> Element</span></span>
<span data-ttu-id="c64ad-103">Especifica as configurações para uma credencial do Windows a ser usada para representar o cliente.</span><span class="sxs-lookup"><span data-stu-id="c64ad-103">Specifies the settings for a Windows credential to be used to represent the client.</span></span>  
  
<span data-ttu-id="c64ad-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c64ad-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c64ad-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="c64ad-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c64ad-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="c64ad-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="c64ad-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> endpointBehaviors**](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="c64ad-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="c64ad-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="c64ad-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="c64ad-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="c64ad-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="c64ad-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> do Windows**</span><span class="sxs-lookup"><span data-stu-id="c64ad-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<windows>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c64ad-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c64ad-111">Syntax</span></span>  
  
```xml  
<windows allowedImpersonationLevel="Identification/Impersonation/Delegation/Anonymous/None"
         allowNtlm="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c64ad-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c64ad-112">Attributes and Elements</span></span>  
 <span data-ttu-id="c64ad-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c64ad-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c64ad-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="c64ad-114">Attributes</span></span>  
  
|<span data-ttu-id="c64ad-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="c64ad-115">Attribute</span></span>|<span data-ttu-id="c64ad-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="c64ad-116">Description</span></span>|  
|---------------|-----------------|  
|`allowedImpersonationLevel`|<span data-ttu-id="c64ad-117">Define a preferência de representação que o cliente se comunica com o servidor.</span><span class="sxs-lookup"><span data-stu-id="c64ad-117">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="c64ad-118">O modo de representação que o cliente seleciona não é imposto no servidor.</span><span class="sxs-lookup"><span data-stu-id="c64ad-118">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="c64ad-119">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c64ad-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="c64ad-120">ID O servidor pode obter a identidade e os privilégios do cliente, mas não pode representar o cliente.</span><span class="sxs-lookup"><span data-stu-id="c64ad-120">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="c64ad-121">Representação O servidor pode representar o contexto de segurança do cliente no sistema local.</span><span class="sxs-lookup"><span data-stu-id="c64ad-121">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="c64ad-122">Delegação O servidor pode representar o contexto de segurança do cliente em sistemas remotos.</span><span class="sxs-lookup"><span data-stu-id="c64ad-122">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="c64ad-123">Modo O servidor não pode representar ou identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="c64ad-123">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="c64ad-124">None Não há um nível de representação atribuído.</span><span class="sxs-lookup"><span data-stu-id="c64ad-124">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="c64ad-125">O padrão é identificação.</span><span class="sxs-lookup"><span data-stu-id="c64ad-125">The default is Identification.</span></span> <span data-ttu-id="c64ad-126">Esse atributo é do tipo <xref:System.Security.Principal.TokenImpersonationLevel>.</span><span class="sxs-lookup"><span data-stu-id="c64ad-126">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
|`allowNtlm`|<span data-ttu-id="c64ad-127">Definir essa propriedade como `true` permite que a autenticação faça downgrade para NTLM se o Kerberos não estiver disponível.</span><span class="sxs-lookup"><span data-stu-id="c64ad-127">Setting this property to `true` allows authentication to downgrade to NTLM if Kerberos is not available.</span></span><br /><br /> <span data-ttu-id="c64ad-128">Definir essa propriedade como `false` faz com que o Windows Communication Foundation (WCF) faça um melhor esforço para gerar uma exceção se o NTLM for usado.</span><span class="sxs-lookup"><span data-stu-id="c64ad-128">Setting this property to `false` causes Windows Communication Foundation (WCF) to make a best-effort to throw an exception if NTLM is used.</span></span> <span data-ttu-id="c64ad-129">Observe que a definição dessa propriedade `false` como pode não impedir que credenciais NTLM sejam enviadas pela conexão.</span><span class="sxs-lookup"><span data-stu-id="c64ad-129">Note that setting this property to `false` may not prevent NTLM credentials from being sent over the wire.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c64ad-130">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c64ad-130">Child Elements</span></span>  
 <span data-ttu-id="c64ad-131">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="c64ad-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c64ad-132">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c64ad-132">Parent Elements</span></span>  
  
|<span data-ttu-id="c64ad-133">Elemento</span><span class="sxs-lookup"><span data-stu-id="c64ad-133">Element</span></span>|<span data-ttu-id="c64ad-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="c64ad-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c64ad-135">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="c64ad-135">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="c64ad-136">Especifica as credenciais usadas para autenticar o cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="c64ad-136">Specifies the credentials used to authenticate the client to the service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c64ad-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c64ad-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.WindowsClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Windows%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- [<span data-ttu-id="c64ad-138">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="c64ad-138">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="c64ad-139">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="c64ad-139">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="c64ad-140">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="c64ad-140">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
