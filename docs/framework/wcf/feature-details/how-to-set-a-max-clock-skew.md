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
ms.openlocfilehash: f8231acade6821c95a76a608633fe443f4add8ab
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84586907"
---
# <a name="how-to-set-a-max-clock-skew"></a><span data-ttu-id="ee5cd-102">Como definir a precisão máxima do relógio</span><span class="sxs-lookup"><span data-stu-id="ee5cd-102">How to: Set a Max Clock Skew</span></span>
<span data-ttu-id="ee5cd-103">As funções de tempo crítico podem ser degradedas se as configurações de relógio em dois computadores forem diferentes.</span><span class="sxs-lookup"><span data-stu-id="ee5cd-103">Time-critical functions can be derailed if the clock settings on two computers are different.</span></span> <span data-ttu-id="ee5cd-104">Para atenuar essa possibilidade, você pode definir a `MaxClockSkew` propriedade como um <xref:System.TimeSpan> .</span><span class="sxs-lookup"><span data-stu-id="ee5cd-104">To mitigate this possibility, you can set the `MaxClockSkew` property to a <xref:System.TimeSpan>.</span></span> <span data-ttu-id="ee5cd-105">Essa propriedade está disponível em duas classes:</span><span class="sxs-lookup"><span data-stu-id="ee5cd-105">This property is available on two classes:</span></span>  
  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
  
> [!IMPORTANT]
> <span data-ttu-id="ee5cd-106">Para uma conversa segura, as alterações na `MaxClockSkew` Propriedade devem ser feitas quando o serviço ou o cliente é inicializado.</span><span class="sxs-lookup"><span data-stu-id="ee5cd-106">For a secure conversation, changes to the `MaxClockSkew` property  must be made when the service or client is bootstrapped.</span></span> <span data-ttu-id="ee5cd-107">Para fazer isso, você deve definir a propriedade no <xref:System.ServiceModel.Channels.SecurityBindingElement> retornado pela <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="ee5cd-107">To do this, you must set the property on the <xref:System.ServiceModel.Channels.SecurityBindingElement> returned by the <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="ee5cd-108">Para alterar a propriedade em uma das associações fornecidas pelo sistema, você deve encontrar o elemento de associação de segurança na coleção de associações e definir a `MaxClockSkew` propriedade como um novo valor.</span><span class="sxs-lookup"><span data-stu-id="ee5cd-108">To change the property on one of the system-provided bindings, you must find the security binding element in the collection of bindings and set the `MaxClockSkew` property to a new value.</span></span> <span data-ttu-id="ee5cd-109">Duas classes derivam de <xref:System.ServiceModel.Channels.SecurityBindingElement> : <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> e <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="ee5cd-109">Two classes derive from the <xref:System.ServiceModel.Channels.SecurityBindingElement>: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="ee5cd-110">Ao recuperar a associação de segurança da coleção, você deve converter em um desses tipos para definir corretamente a `MaxClockSkew` propriedade.</span><span class="sxs-lookup"><span data-stu-id="ee5cd-110">When retrieving the security binding from the collection, you must cast to one of these types in order to correctly set the `MaxClockSkew` property.</span></span> <span data-ttu-id="ee5cd-111">O exemplo a seguir usa um <xref:System.ServiceModel.WSHttpBinding> , que usa o <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="ee5cd-111">The following example uses a <xref:System.ServiceModel.WSHttpBinding>, which uses the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="ee5cd-112">Para obter uma lista que especifica qual tipo de associação de segurança usar em cada associação fornecida pelo sistema, consulte [associações fornecidas pelo sistema](../system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="ee5cd-112">For a list that specifies which type of security binding to use in each system-provided binding, see [System-Provided Bindings](../system-provided-bindings.md).</span></span>  
  
## <a name="to-create-a-custom-binding-with-a-new-clock-skew-value-in-code"></a><span data-ttu-id="ee5cd-113">Para criar uma associação personalizada com um novo valor de distorção de relógio no código</span><span class="sxs-lookup"><span data-stu-id="ee5cd-113">To create a custom binding with a new clock skew value in code</span></span>  
  
> [!WARNING]
> <span data-ttu-id="ee5cd-114">Adicione referências aos seguintes namespaces em seu código: <xref:System.ServiceModel.Channels> , <xref:System.ServiceModel.Description> , <xref:System.Security.Permissions> e <xref:System.ServiceModel.Security.Tokens> .</span><span class="sxs-lookup"><span data-stu-id="ee5cd-114">Add references to the following namespaces in your code: <xref:System.ServiceModel.Channels>, <xref:System.ServiceModel.Description>, <xref:System.Security.Permissions>, and <xref:System.ServiceModel.Security.Tokens>.</span></span>  
  
1. <span data-ttu-id="ee5cd-115">Crie uma instância de uma <xref:System.ServiceModel.WSHttpBinding> classe e defina seu modo de segurança como <xref:System.ServiceModel.SecurityMode.Message?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="ee5cd-115">Create an instance of a <xref:System.ServiceModel.WSHttpBinding> class and set its security mode to <xref:System.ServiceModel.SecurityMode.Message?displayProperty=nameWithType>.</span></span>  
  
2. <span data-ttu-id="ee5cd-116">Crie uma nova instância da <xref:System.ServiceModel.Channels.BindingElementCollection> classe chamando o <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> método.</span><span class="sxs-lookup"><span data-stu-id="ee5cd-116">Create a new instance of the <xref:System.ServiceModel.Channels.BindingElementCollection> class by calling the <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> method.</span></span>  
  
3. <span data-ttu-id="ee5cd-117">Use o <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> método da <xref:System.ServiceModel.Channels.BindingElementCollection> classe para localizar o elemento de associação de segurança.</span><span class="sxs-lookup"><span data-stu-id="ee5cd-117">Use the <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> method of the <xref:System.ServiceModel.Channels.BindingElementCollection> class to find the security binding element.</span></span>  
  
4. <span data-ttu-id="ee5cd-118">Ao usar o <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> método, converta para o tipo real.</span><span class="sxs-lookup"><span data-stu-id="ee5cd-118">When using the <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> method, cast to the actual type.</span></span> <span data-ttu-id="ee5cd-119">O exemplo a seguir é convertido para o <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> tipo.</span><span class="sxs-lookup"><span data-stu-id="ee5cd-119">The example below casts to the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> type.</span></span>  
  
5. <span data-ttu-id="ee5cd-120">Defina a <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> propriedade no elemento de associação de segurança.</span><span class="sxs-lookup"><span data-stu-id="ee5cd-120">Set the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> property on the security binding element.</span></span>  
  
6. <span data-ttu-id="ee5cd-121">Crie um <xref:System.ServiceModel.ServiceHost> com um tipo de serviço e endereço base apropriados.</span><span class="sxs-lookup"><span data-stu-id="ee5cd-121">Create a <xref:System.ServiceModel.ServiceHost> with an appropriate service type and base address.</span></span>  
  
7. <span data-ttu-id="ee5cd-122">Use o <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> método para adicionar um ponto de extremidade e incluir o <xref:System.ServiceModel.Channels.CustomBinding> .</span><span class="sxs-lookup"><span data-stu-id="ee5cd-122">Use the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method to add an endpoint and include the <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
     [!code-csharp[c_MaxClockSkew#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_maxclockskew/cs/source.cs#1)]
     [!code-vb[c_MaxClockSkew#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_maxclockskew/vb/source.vb#1)]  
  
## <a name="to-set-the-maxclockskew-in-configuration"></a><span data-ttu-id="ee5cd-123">Para definir o MaxClockSkew na configuração</span><span class="sxs-lookup"><span data-stu-id="ee5cd-123">To set the MaxClockSkew in configuration</span></span>  
  
1. <span data-ttu-id="ee5cd-124">Crie um [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) na [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) seção do elemento.</span><span class="sxs-lookup"><span data-stu-id="ee5cd-124">Create a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) in the [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) element section.</span></span>  
  
2. <span data-ttu-id="ee5cd-125">Crie um [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) elemento e defina o `name` atributo como um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="ee5cd-125">Create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element and set the `name` attribute to an appropriate value.</span></span> <span data-ttu-id="ee5cd-126">O exemplo a seguir define como `MaxClockSkewBinding` .</span><span class="sxs-lookup"><span data-stu-id="ee5cd-126">The following example sets it to `MaxClockSkewBinding`.</span></span>  
  
3. <span data-ttu-id="ee5cd-127">Adicione um elemento Encoding.</span><span class="sxs-lookup"><span data-stu-id="ee5cd-127">Add an encoding element.</span></span> <span data-ttu-id="ee5cd-128">O exemplo a seguir adiciona um [\<textMessageEncoding>](../../configure-apps/file-schema/wcf/textmessageencoding.md) .</span><span class="sxs-lookup"><span data-stu-id="ee5cd-128">The example below adds a [\<textMessageEncoding>](../../configure-apps/file-schema/wcf/textmessageencoding.md).</span></span>  
  
4. <span data-ttu-id="ee5cd-129">Adicione um [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) elemento e defina o `authenticationMode` atributo para uma configuração apropriada.</span><span class="sxs-lookup"><span data-stu-id="ee5cd-129">Add a [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element and set the `authenticationMode` attribute to an appropriate setting.</span></span> <span data-ttu-id="ee5cd-130">O exemplo a seguir define o atributo como `Kerberos` para especificar que o serviço usa a autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="ee5cd-130">The following example set the attribute to `Kerberos` to specify that the service use Windows authentication.</span></span>  
  
5. <span data-ttu-id="ee5cd-131">Adicione um [\<localServiceSettings>](../../configure-apps/file-schema/wcf/localservicesettings-element.md) e defina o `maxClockSkew` atributo como um valor na forma de `"##:##:##"` .</span><span class="sxs-lookup"><span data-stu-id="ee5cd-131">Add a [\<localServiceSettings>](../../configure-apps/file-schema/wcf/localservicesettings-element.md) and set the `maxClockSkew` attribute to a value in the form of `"##:##:##"`.</span></span> <span data-ttu-id="ee5cd-132">O exemplo a seguir define como 7 minutos.</span><span class="sxs-lookup"><span data-stu-id="ee5cd-132">The following example sets it to 7 minutes.</span></span> <span data-ttu-id="ee5cd-133">Opcionalmente, adicione um [\<localServiceSettings>](../../configure-apps/file-schema/wcf/localservicesettings-element.md) e defina o `maxClockSkew` atributo para uma configuração apropriada.</span><span class="sxs-lookup"><span data-stu-id="ee5cd-133">Optionally, add a [\<localServiceSettings>](../../configure-apps/file-schema/wcf/localservicesettings-element.md) and set the `maxClockSkew` attribute to an appropriate setting.</span></span>  
  
6. <span data-ttu-id="ee5cd-134">Adicione um elemento Transport.</span><span class="sxs-lookup"><span data-stu-id="ee5cd-134">Add a transport element.</span></span> <span data-ttu-id="ee5cd-135">O exemplo a seguir usa um [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md) .</span><span class="sxs-lookup"><span data-stu-id="ee5cd-135">The following example uses an [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md).</span></span>  
  
7. <span data-ttu-id="ee5cd-136">Para uma conversa segura, as configurações de segurança devem ocorrer na inicialização no [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="ee5cd-136">For a secure conversation, the security settings must occur at the bootstrap in the [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ee5cd-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ee5cd-137">See also</span></span>

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="ee5cd-138">Como criar uma associação personalizada utilizando o SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="ee5cd-138">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](how-to-create-a-custom-binding-using-the-securitybindingelement.md)
