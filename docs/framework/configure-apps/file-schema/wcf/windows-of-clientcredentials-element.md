---
title: <windows> do <clientCredentials> elemento
ms.date: 03/30/2017
ms.assetid: 793e41c2-31ea-4159-abbc-2123bf097233
ms.openlocfilehash: 115e1822659c04ee37a7364f7b25616b52dc5efe
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177820"
---
# <a name="windows-of-clientcredentials-element"></a><span data-ttu-id="e8808-102">\<windows> do \<clientCredentials> elemento</span><span class="sxs-lookup"><span data-stu-id="e8808-102">\<windows> of \<clientCredentials> Element</span></span>

<span data-ttu-id="e8808-103">Especifica as configurações para uma credencial do Windows a ser usada para representar o cliente.</span><span class="sxs-lookup"><span data-stu-id="e8808-103">Specifies the settings for a Windows credential to be used to represent the client.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<windows>**  
  
## <a name="syntax"></a><span data-ttu-id="e8808-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e8808-104">Syntax</span></span>  
  
```xml  
<windows allowedImpersonationLevel="Identification/Impersonation/Delegation/Anonymous/None"
         allowNtlm="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e8808-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e8808-105">Attributes and Elements</span></span>  

 <span data-ttu-id="e8808-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e8808-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e8808-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="e8808-107">Attributes</span></span>  
  
|<span data-ttu-id="e8808-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="e8808-108">Attribute</span></span>|<span data-ttu-id="e8808-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="e8808-109">Description</span></span>|  
|---------------|-----------------|  
|`allowedImpersonationLevel`|<span data-ttu-id="e8808-110">Define a preferência de representação que o cliente se comunica com o servidor.</span><span class="sxs-lookup"><span data-stu-id="e8808-110">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="e8808-111">O modo de representação que o cliente seleciona não é imposto no servidor.</span><span class="sxs-lookup"><span data-stu-id="e8808-111">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="e8808-112">Os valores válidos incluem os seguintes:</span><span class="sxs-lookup"><span data-stu-id="e8808-112">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e8808-113">-Identificação: o servidor pode obter a identidade e os privilégios do cliente, mas não pode representar o cliente.</span><span class="sxs-lookup"><span data-stu-id="e8808-113">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="e8808-114">-Impersonation: o servidor pode representar o contexto de segurança do cliente no sistema local.</span><span class="sxs-lookup"><span data-stu-id="e8808-114">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="e8808-115">-Delegation: o servidor pode representar o contexto de segurança do cliente em sistemas remotos.</span><span class="sxs-lookup"><span data-stu-id="e8808-115">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="e8808-116">-Anônimo: o servidor não pode representar ou identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="e8808-116">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="e8808-117">-Nenhum: um nível de representação não é atribuído.</span><span class="sxs-lookup"><span data-stu-id="e8808-117">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="e8808-118">O padrão é identificação.</span><span class="sxs-lookup"><span data-stu-id="e8808-118">The default is Identification.</span></span> <span data-ttu-id="e8808-119">Esse atributo é do tipo <xref:System.Security.Principal.TokenImpersonationLevel> .</span><span class="sxs-lookup"><span data-stu-id="e8808-119">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
|`allowNtlm`|<span data-ttu-id="e8808-120">Definir essa propriedade como `true` permite que a autenticação faça downgrade para NTLM se o Kerberos não estiver disponível.</span><span class="sxs-lookup"><span data-stu-id="e8808-120">Setting this property to `true` allows authentication to downgrade to NTLM if Kerberos is not available.</span></span><br /><br /> <span data-ttu-id="e8808-121">Definir essa propriedade como `false` faz com que o Windows Communication Foundation (WCF) faça um melhor esforço para gerar uma exceção se o NTLM for usado.</span><span class="sxs-lookup"><span data-stu-id="e8808-121">Setting this property to `false` causes Windows Communication Foundation (WCF) to make a best-effort to throw an exception if NTLM is used.</span></span> <span data-ttu-id="e8808-122">Observe que a definição dessa propriedade como `false` pode não impedir que credenciais NTLM sejam enviadas pela conexão.</span><span class="sxs-lookup"><span data-stu-id="e8808-122">Note that setting this property to `false` may not prevent NTLM credentials from being sent over the wire.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e8808-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e8808-123">Child Elements</span></span>  

 <span data-ttu-id="e8808-124">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="e8808-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e8808-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e8808-125">Parent Elements</span></span>  
  
|<span data-ttu-id="e8808-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="e8808-126">Element</span></span>|<span data-ttu-id="e8808-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="e8808-127">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="e8808-128">Especifica as credenciais usadas para autenticar o cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="e8808-128">Specifies the credentials used to authenticate the client to the service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e8808-129">Veja também</span><span class="sxs-lookup"><span data-stu-id="e8808-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.WindowsClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Windows%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- [<span data-ttu-id="e8808-130">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="e8808-130">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="e8808-131">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="e8808-131">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="e8808-132">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="e8808-132">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
