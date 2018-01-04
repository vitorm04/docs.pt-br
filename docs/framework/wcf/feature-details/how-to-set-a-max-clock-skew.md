---
title: "Como definir a precisão máxima do relógio"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MaxClockSkew property
- WCF, custom bindings
ms.assetid: 491d1705-eb29-43c2-a44c-c0cf996f74eb
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e186043a6cb32eaf5ed6bac6be3eaf50cb1ea32b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-a-max-clock-skew"></a><span data-ttu-id="817d4-102">Como definir a precisão máxima do relógio</span><span class="sxs-lookup"><span data-stu-id="817d4-102">How to: Set a Max Clock Skew</span></span>
<span data-ttu-id="817d4-103">Funções críticas de tempo podem ser derailed se as configurações de relógio em dois computadores diferentes.</span><span class="sxs-lookup"><span data-stu-id="817d4-103">Time-critical functions can be derailed if the clock settings on two computers are different.</span></span> <span data-ttu-id="817d4-104">Para atenuar essa possibilidade, você pode definir o `MaxClockSkew` propriedade para um <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="817d4-104">To mitigate this possibility, you can set the `MaxClockSkew` property to a <xref:System.TimeSpan>.</span></span> <span data-ttu-id="817d4-105">Essa propriedade está disponível em duas classes:</span><span class="sxs-lookup"><span data-stu-id="817d4-105">This property is available on two classes:</span></span>  
  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
  
> [!IMPORTANT]
>  <span data-ttu-id="817d4-106">Importante para uma conversa segura, alterações de `MaxClockSkew` propriedade deve ser feita quando o serviço ou cliente é inicializado.</span><span class="sxs-lookup"><span data-stu-id="817d4-106">Important   For a secure conversation, changes to the `MaxClockSkew` property  must be made when the service or client is bootstrapped.</span></span> <span data-ttu-id="817d4-107">Para fazer isso, você deve definir a propriedade no <xref:System.ServiceModel.Channels.SecurityBindingElement> retornado pelo <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A>.</span><span class="sxs-lookup"><span data-stu-id="817d4-107">To do this, you must set the property on the <xref:System.ServiceModel.Channels.SecurityBindingElement> returned by the <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A>.</span></span>  
  
 <span data-ttu-id="817d4-108">Para alterar a propriedade em uma das associações fornecidas pelo sistema, você deve localizar o elemento de associação de segurança na coleção de associações e definir o `MaxClockSkew` propriedade para um novo valor.</span><span class="sxs-lookup"><span data-stu-id="817d4-108">To change the property on one of the system-provided bindings, you must find the security binding element in the collection of bindings and set the `MaxClockSkew` property to a new value.</span></span> <span data-ttu-id="817d4-109">Duas classes derivam o <xref:System.ServiceModel.Channels.SecurityBindingElement>: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> e <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="817d4-109">Two classes derive from the <xref:System.ServiceModel.Channels.SecurityBindingElement>: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="817d4-110">Ao recuperar a associação de segurança da coleção, você deve converter para um desses tipos para configurar corretamente o `MaxClockSkew` propriedade.</span><span class="sxs-lookup"><span data-stu-id="817d4-110">When retrieving the security binding from the collection, you must cast to one of these types in order to correctly set the `MaxClockSkew` property.</span></span> <span data-ttu-id="817d4-111">O exemplo a seguir usa uma <xref:System.ServiceModel.WSHttpBinding>, que usa o <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="817d4-111">The following example uses a <xref:System.ServiceModel.WSHttpBinding>, which uses the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="817d4-112">Para obter uma lista que especifica o tipo de associação de segurança para usar em cada associação fornecida pelo sistema, consulte [System-Provided associações](../../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="817d4-112">For a list that specifies which type of security binding to use in each system-provided binding, see [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>  
  
### <a name="to-create-a-custom-binding-with-a-new-clock-skew-value-in-code"></a><span data-ttu-id="817d4-113">Para criar uma associação personalizada com um relógio de novo distorcer valor no código</span><span class="sxs-lookup"><span data-stu-id="817d4-113">To create a custom binding with a new clock skew value in code</span></span>  
  
1.  > [!WARNING]
    >  <span data-ttu-id="817d4-114">Observe a adicionar referências para os namespaces a seguir no seu código: <xref:System.ServiceModel.Channels>, <xref:System.ServiceModel.Description>, <xref:System.Security.Permissions>, e <xref:System.ServiceModel.Security.Tokens>.</span><span class="sxs-lookup"><span data-stu-id="817d4-114">Note   Add references to the following namespaces in your code: <xref:System.ServiceModel.Channels>, <xref:System.ServiceModel.Description>, <xref:System.Security.Permissions>, and <xref:System.ServiceModel.Security.Tokens>.</span></span>  
  
     <span data-ttu-id="817d4-115">Criar uma instância de um <xref:System.ServiceModel.WSHttpBinding> de classe e defina o modo de segurança <xref:System.ServiceModel.SecurityMode.Message>.</span><span class="sxs-lookup"><span data-stu-id="817d4-115">Create an instance of a <xref:System.ServiceModel.WSHttpBinding> class and set its security mode to <xref:System.ServiceModel.SecurityMode.Message>.</span></span>  
  
2.  <span data-ttu-id="817d4-116">Criar uma nova instância do <xref:System.ServiceModel.Channels.BindingElementCollection> classe chamando o <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> método.</span><span class="sxs-lookup"><span data-stu-id="817d4-116">Create a new instance of the <xref:System.ServiceModel.Channels.BindingElementCollection> class by calling the <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> method.</span></span>  
  
3.  <span data-ttu-id="817d4-117">Use o <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> método o <xref:System.ServiceModel.Channels.BindingElementCollection> classe para localizar o elemento de associação de segurança.</span><span class="sxs-lookup"><span data-stu-id="817d4-117">Use the <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> method of the <xref:System.ServiceModel.Channels.BindingElementCollection> class to find the security binding element.</span></span>  
  
4.  <span data-ttu-id="817d4-118">Ao usar o <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> método, convertido para o tipo real.</span><span class="sxs-lookup"><span data-stu-id="817d4-118">When using the <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> method, cast to the actual type.</span></span> <span data-ttu-id="817d4-119">O exemplo a seguir conversões para o <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> tipo.</span><span class="sxs-lookup"><span data-stu-id="817d4-119">The example below casts to the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> type.</span></span>  
  
5.  <span data-ttu-id="817d4-120">Definir o <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> propriedade no elemento de associação de segurança.</span><span class="sxs-lookup"><span data-stu-id="817d4-120">Set the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> property on the security binding element.</span></span>  
  
6.  <span data-ttu-id="817d4-121">Criar um <xref:System.ServiceModel.ServiceHost> com um endereço de base e de tipo de serviço apropriado.</span><span class="sxs-lookup"><span data-stu-id="817d4-121">Create a <xref:System.ServiceModel.ServiceHost> with an appropriate service type and base address.</span></span>  
  
7.  <span data-ttu-id="817d4-122">Use o <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> método para adicionar um ponto de extremidade e incluem o <xref:System.ServiceModel.Channels.CustomBinding>.</span><span class="sxs-lookup"><span data-stu-id="817d4-122">Use the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method to add an endpoint and include the <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
     [!code-csharp[c_MaxClockSkew#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_maxclockskew/cs/source.cs#1)]
     [!code-vb[c_MaxClockSkew#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_maxclockskew/vb/source.vb#1)]  
  
### <a name="to-set-the-maxclockskew-in-configuration"></a><span data-ttu-id="817d4-123">Para definir o MaxClockSkew na configuração</span><span class="sxs-lookup"><span data-stu-id="817d4-123">To set the MaxClockSkew in configuration</span></span>  
  
1.  <span data-ttu-id="817d4-124">Criar um [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) no [ \<associações >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) seção do elemento.</span><span class="sxs-lookup"><span data-stu-id="817d4-124">Create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) in the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element section.</span></span>  
  
2.  <span data-ttu-id="817d4-125">Criar um [ \<associação >](../../../../docs/framework/misc/binding.md) elemento e defina o `name` de atributo para um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="817d4-125">Create a [\<binding>](../../../../docs/framework/misc/binding.md) element and set the `name` attribute to an appropriate value.</span></span> <span data-ttu-id="817d4-126">O exemplo a seguir define `MaxClockSkewBinding`.</span><span class="sxs-lookup"><span data-stu-id="817d4-126">The following example sets it to `MaxClockSkewBinding`.</span></span>  
  
3.  <span data-ttu-id="817d4-127">Adicione um elemento de codificação.</span><span class="sxs-lookup"><span data-stu-id="817d4-127">Add an encoding element.</span></span> <span data-ttu-id="817d4-128">O exemplo a seguir adiciona uma [ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span><span class="sxs-lookup"><span data-stu-id="817d4-128">The example below adds a [\<textMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span></span>  
  
4.  <span data-ttu-id="817d4-129">Adicionar um [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elemento e defina o `authenticationMode` de atributo para uma configuração apropriada.</span><span class="sxs-lookup"><span data-stu-id="817d4-129">Add a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element and set the `authenticationMode` attribute to an appropriate setting.</span></span> <span data-ttu-id="817d4-130">O exemplo a seguir define o atributo `Kerberos` para especificar que o serviço usa a autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="817d4-130">The following example set the attribute to `Kerberos` to specify that the service use Windows authentication.</span></span>  
  
5.  <span data-ttu-id="817d4-131">Adicionar um [ \<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) e defina o `maxClockSkew` de atributo para um valor na forma de `"##:##:##"`.</span><span class="sxs-lookup"><span data-stu-id="817d4-131">Add a [\<localServiceSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) and set the `maxClockSkew` attribute to a value in the form of `"##:##:##"`.</span></span> <span data-ttu-id="817d4-132">O exemplo a seguir define a 7 minutos.</span><span class="sxs-lookup"><span data-stu-id="817d4-132">The following example sets it to 7 minutes.</span></span> <span data-ttu-id="817d4-133">Opcionalmente, adicione um [ \<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) e defina o `maxClockSkew` de atributo para uma configuração apropriada.</span><span class="sxs-lookup"><span data-stu-id="817d4-133">Optionally, add a [\<localServiceSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) and set the `maxClockSkew` attribute to an appropriate setting.</span></span>  
  
6.  <span data-ttu-id="817d4-134">Adicione um elemento de transporte.</span><span class="sxs-lookup"><span data-stu-id="817d4-134">Add a transport element.</span></span> <span data-ttu-id="817d4-135">O exemplo a seguir usa uma [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).</span><span class="sxs-lookup"><span data-stu-id="817d4-135">The following example uses an [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).</span></span>  
  
7.  <span data-ttu-id="817d4-136">Para uma conversa segura, as configurações de segurança devem ocorrer com a inicialização no [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="817d4-136">For a secure conversation, the security settings must occur at the bootstrap in the [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element.</span></span>  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="MaxClockSkewBinding">  
            <textMessageEncoding />  
            <security authenticationMode="Kerberos">  
               <localClientSettings maxClockSkew="00:07:00" />  
               <localServiceSettings maxClockSkew="00:07:00" />  
               <secureConversationBootstrap>  
                  <localClientSettings maxClockSkew="00:30:00" />  
                  <localServiceSettings maxClockSkew="00:30:00" />  
               </secureConversationBootstrap>  
            </security>  
            <httpTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="817d4-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="817d4-137">See Also</span></span>  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="817d4-138">Como criar uma associação personalizada utilizando o SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="817d4-138">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
