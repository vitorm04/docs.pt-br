---
title: Como definir a precisão máxima do relógio
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MaxClockSkew property
- WCF, custom bindings
ms.assetid: 491d1705-eb29-43c2-a44c-c0cf996f74eb
ms.openlocfilehash: 96afa61d32e1ba744c9f3dbbeeb7fb2e55157f4c
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141651"
---
# <a name="how-to-set-a-max-clock-skew"></a><span data-ttu-id="79fe8-102">Como definir a precisão máxima do relógio</span><span class="sxs-lookup"><span data-stu-id="79fe8-102">How to: Set a Max Clock Skew</span></span>
<span data-ttu-id="79fe8-103">As funções de tempo crítico podem ser degradedas se as configurações de relógio em dois computadores forem diferentes.</span><span class="sxs-lookup"><span data-stu-id="79fe8-103">Time-critical functions can be derailed if the clock settings on two computers are different.</span></span> <span data-ttu-id="79fe8-104">Para atenuar essa possibilidade, você pode definir a propriedade `MaxClockSkew` como um <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="79fe8-104">To mitigate this possibility, you can set the `MaxClockSkew` property to a <xref:System.TimeSpan>.</span></span> <span data-ttu-id="79fe8-105">Essa propriedade está disponível em duas classes:</span><span class="sxs-lookup"><span data-stu-id="79fe8-105">This property is available on two classes:</span></span>  
  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
  
> [!IMPORTANT]
> <span data-ttu-id="79fe8-106">Para uma conversa segura, as alterações na propriedade `MaxClockSkew` devem ser feitas quando o serviço ou o cliente é inicializado.</span><span class="sxs-lookup"><span data-stu-id="79fe8-106">For a secure conversation, changes to the `MaxClockSkew` property  must be made when the service or client is bootstrapped.</span></span> <span data-ttu-id="79fe8-107">Para fazer isso, você deve definir a propriedade no <xref:System.ServiceModel.Channels.SecurityBindingElement> retornado pela propriedade <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="79fe8-107">To do this, you must set the property on the <xref:System.ServiceModel.Channels.SecurityBindingElement> returned by the <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="79fe8-108">Para alterar a propriedade em uma das associações fornecidas pelo sistema, você deve encontrar o elemento de associação de segurança na coleção de associações e definir a propriedade `MaxClockSkew` como um novo valor.</span><span class="sxs-lookup"><span data-stu-id="79fe8-108">To change the property on one of the system-provided bindings, you must find the security binding element in the collection of bindings and set the `MaxClockSkew` property to a new value.</span></span> <span data-ttu-id="79fe8-109">Duas classes derivam do <xref:System.ServiceModel.Channels.SecurityBindingElement>: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> e <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="79fe8-109">Two classes derive from the <xref:System.ServiceModel.Channels.SecurityBindingElement>: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="79fe8-110">Ao recuperar a associação de segurança da coleção, você deve converter em um desses tipos para definir corretamente a propriedade `MaxClockSkew`.</span><span class="sxs-lookup"><span data-stu-id="79fe8-110">When retrieving the security binding from the collection, you must cast to one of these types in order to correctly set the `MaxClockSkew` property.</span></span> <span data-ttu-id="79fe8-111">O exemplo a seguir usa um <xref:System.ServiceModel.WSHttpBinding>, que usa o <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="79fe8-111">The following example uses a <xref:System.ServiceModel.WSHttpBinding>, which uses the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="79fe8-112">Para obter uma lista que especifica qual tipo de associação de segurança usar em cada associação fornecida pelo sistema, consulte [associações fornecidas pelo sistema](../../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="79fe8-112">For a list that specifies which type of security binding to use in each system-provided binding, see [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>  
  
## <a name="to-create-a-custom-binding-with-a-new-clock-skew-value-in-code"></a><span data-ttu-id="79fe8-113">Para criar uma associação personalizada com um novo valor de distorção de relógio no código</span><span class="sxs-lookup"><span data-stu-id="79fe8-113">To create a custom binding with a new clock skew value in code</span></span>  
  
> [!WARNING]
> <span data-ttu-id="79fe8-114">Adicione referências aos seguintes namespaces em seu código: <xref:System.ServiceModel.Channels>, <xref:System.ServiceModel.Description>, <xref:System.Security.Permissions>e <xref:System.ServiceModel.Security.Tokens>.</span><span class="sxs-lookup"><span data-stu-id="79fe8-114">Add references to the following namespaces in your code: <xref:System.ServiceModel.Channels>, <xref:System.ServiceModel.Description>, <xref:System.Security.Permissions>, and <xref:System.ServiceModel.Security.Tokens>.</span></span>  
  
1. <span data-ttu-id="79fe8-115">Crie uma instância de uma classe de <xref:System.ServiceModel.WSHttpBinding> e defina seu modo de segurança como <xref:System.ServiceModel.SecurityMode.Message?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="79fe8-115">Create an instance of a <xref:System.ServiceModel.WSHttpBinding> class and set its security mode to <xref:System.ServiceModel.SecurityMode.Message?displayProperty=nameWithType>.</span></span>  
  
2. <span data-ttu-id="79fe8-116">Crie uma nova instância da classe <xref:System.ServiceModel.Channels.BindingElementCollection> chamando o método <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A>.</span><span class="sxs-lookup"><span data-stu-id="79fe8-116">Create a new instance of the <xref:System.ServiceModel.Channels.BindingElementCollection> class by calling the <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> method.</span></span>  
  
3. <span data-ttu-id="79fe8-117">Use o método <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> da classe <xref:System.ServiceModel.Channels.BindingElementCollection> para localizar o elemento de associação de segurança.</span><span class="sxs-lookup"><span data-stu-id="79fe8-117">Use the <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> method of the <xref:System.ServiceModel.Channels.BindingElementCollection> class to find the security binding element.</span></span>  
  
4. <span data-ttu-id="79fe8-118">Ao usar o método <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A>, converta para o tipo real.</span><span class="sxs-lookup"><span data-stu-id="79fe8-118">When using the <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> method, cast to the actual type.</span></span> <span data-ttu-id="79fe8-119">O exemplo a seguir é convertido para o tipo de <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="79fe8-119">The example below casts to the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> type.</span></span>  
  
5. <span data-ttu-id="79fe8-120">Defina a propriedade <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> no elemento de associação de segurança.</span><span class="sxs-lookup"><span data-stu-id="79fe8-120">Set the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> property on the security binding element.</span></span>  
  
6. <span data-ttu-id="79fe8-121">Crie um <xref:System.ServiceModel.ServiceHost> com um tipo de serviço e endereço base apropriados.</span><span class="sxs-lookup"><span data-stu-id="79fe8-121">Create a <xref:System.ServiceModel.ServiceHost> with an appropriate service type and base address.</span></span>  
  
7. <span data-ttu-id="79fe8-122">Use o método <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> para adicionar um ponto de extremidade e incluir o <xref:System.ServiceModel.Channels.CustomBinding>.</span><span class="sxs-lookup"><span data-stu-id="79fe8-122">Use the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method to add an endpoint and include the <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
     [!code-csharp[c_MaxClockSkew#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_maxclockskew/cs/source.cs#1)]
     [!code-vb[c_MaxClockSkew#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_maxclockskew/vb/source.vb#1)]  
  
## <a name="to-set-the-maxclockskew-in-configuration"></a><span data-ttu-id="79fe8-123">Para definir o MaxClockSkew na configuração</span><span class="sxs-lookup"><span data-stu-id="79fe8-123">To set the MaxClockSkew in configuration</span></span>  
  
1. <span data-ttu-id="79fe8-124">Crie uma [\<> CustomBinding](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) na seção do elemento [\<bindings >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) .</span><span class="sxs-lookup"><span data-stu-id="79fe8-124">Create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) in the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element section.</span></span>  
  
2. <span data-ttu-id="79fe8-125">Crie um elemento de [> de associação de\<](../../configure-apps/file-schema/wcf/bindings.md) e defina o atributo `name` como um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="79fe8-125">Create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element and set the `name` attribute to an appropriate value.</span></span> <span data-ttu-id="79fe8-126">O exemplo a seguir o define como `MaxClockSkewBinding`.</span><span class="sxs-lookup"><span data-stu-id="79fe8-126">The following example sets it to `MaxClockSkewBinding`.</span></span>  
  
3. <span data-ttu-id="79fe8-127">Adicione um elemento Encoding.</span><span class="sxs-lookup"><span data-stu-id="79fe8-127">Add an encoding element.</span></span> <span data-ttu-id="79fe8-128">O exemplo a seguir adiciona um [\<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span><span class="sxs-lookup"><span data-stu-id="79fe8-128">The example below adds a [\<textMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span></span>  
  
4. <span data-ttu-id="79fe8-129">Adicione um elemento de [> de segurança\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) e defina o atributo `authenticationMode` como uma configuração apropriada.</span><span class="sxs-lookup"><span data-stu-id="79fe8-129">Add a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element and set the `authenticationMode` attribute to an appropriate setting.</span></span> <span data-ttu-id="79fe8-130">O exemplo a seguir define o atributo como `Kerberos` para especificar que o serviço usa a autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="79fe8-130">The following example set the attribute to `Kerberos` to specify that the service use Windows authentication.</span></span>  
  
5. <span data-ttu-id="79fe8-131">Adicione um [\<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) e defina o atributo `maxClockSkew` como um valor na forma de `"##:##:##"`.</span><span class="sxs-lookup"><span data-stu-id="79fe8-131">Add a [\<localServiceSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) and set the `maxClockSkew` attribute to a value in the form of `"##:##:##"`.</span></span> <span data-ttu-id="79fe8-132">O exemplo a seguir define como 7 minutos.</span><span class="sxs-lookup"><span data-stu-id="79fe8-132">The following example sets it to 7 minutes.</span></span> <span data-ttu-id="79fe8-133">Opcionalmente, adicione um [\<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) e defina o atributo `maxClockSkew` como uma configuração apropriada.</span><span class="sxs-lookup"><span data-stu-id="79fe8-133">Optionally, add a [\<localServiceSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) and set the `maxClockSkew` attribute to an appropriate setting.</span></span>  
  
6. <span data-ttu-id="79fe8-134">Adicione um elemento Transport.</span><span class="sxs-lookup"><span data-stu-id="79fe8-134">Add a transport element.</span></span> <span data-ttu-id="79fe8-135">O exemplo a seguir usa um [\<httpTransport](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).</span><span class="sxs-lookup"><span data-stu-id="79fe8-135">The following example uses an [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).</span></span>  
  
7. <span data-ttu-id="79fe8-136">Para uma conversa segura, as configurações de segurança devem ocorrer na inicialização no elemento [\<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) .</span><span class="sxs-lookup"><span data-stu-id="79fe8-136">For a secure conversation, the security settings must occur at the bootstrap in the [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="79fe8-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="79fe8-137">See also</span></span>

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="79fe8-138">Como criar uma associação personalizada utilizando o SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="79fe8-138">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
