---
title: 'Como: Criar um verificador de identidade do cliente personalizado'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f2d34e43-fa8b-46d2-91cf-d2960e13e16b
ms.openlocfilehash: a7107e6e0bfdb948b584b5cbd57eafc3aff1bd59
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54569369"
---
# <a name="how-to-create-a-custom-client-identity-verifier"></a><span data-ttu-id="83080-102">Como: Criar um verificador de identidade do cliente personalizado</span><span class="sxs-lookup"><span data-stu-id="83080-102">How to: Create a Custom Client Identity Verifier</span></span>
<span data-ttu-id="83080-103">O *identidade* recurso do Windows Communication Foundation (WCF) permite que um cliente para especificar com antecedência a identidade esperada do serviço.</span><span class="sxs-lookup"><span data-stu-id="83080-103">The *identity* feature of Windows Communication Foundation (WCF) enables a client to specify in advance the expected identity of the service.</span></span> <span data-ttu-id="83080-104">Sempre que um servidor se autentica para o cliente, a identidade é verificada em relação a identidade esperada.</span><span class="sxs-lookup"><span data-stu-id="83080-104">Whenever a server authenticates itself to the client, the identity is checked against the expected identity.</span></span> <span data-ttu-id="83080-105">(Para obter uma explicação de identidade e como ele funciona, consulte [identidade de serviço e autenticação](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).)</span><span class="sxs-lookup"><span data-stu-id="83080-105">(For an explanation of identity and how it works, see [Service Identity and Authentication](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).)</span></span>  
  
 <span data-ttu-id="83080-106">Se necessário, a verificação pode ser personalizada usando um verificador de identidade personalizada.</span><span class="sxs-lookup"><span data-stu-id="83080-106">If needed, the verification can be customized using a custom identity verifier.</span></span> <span data-ttu-id="83080-107">Por exemplo, você pode executar verificações de verificação de identidade de serviço adicional.</span><span class="sxs-lookup"><span data-stu-id="83080-107">For example, you can perform additional service identity verification checks.</span></span> <span data-ttu-id="83080-108">Neste exemplo, o verificador de identidade personalizado verifica as declarações adicionais no certificado x. 509 retornada do servidor.</span><span class="sxs-lookup"><span data-stu-id="83080-108">In this example, the custom identity verifier checks additional claims in the X.509 certificate returned from the server.</span></span> <span data-ttu-id="83080-109">Para um aplicativo de exemplo, consulte [exemplo de identidade de serviço](../../../../docs/framework/wcf/samples/service-identity-sample.md).</span><span class="sxs-lookup"><span data-stu-id="83080-109">For a sample application, see [Service Identity Sample](../../../../docs/framework/wcf/samples/service-identity-sample.md).</span></span>  
  
### <a name="to-extend-the-endpointidentity-class"></a><span data-ttu-id="83080-110">Estender a classe EndpointIdentity</span><span class="sxs-lookup"><span data-stu-id="83080-110">To extend the EndpointIdentity class</span></span>  
  
1.  <span data-ttu-id="83080-111">Definir uma nova classe que deriva de <xref:System.ServiceModel.EndpointIdentity> classe.</span><span class="sxs-lookup"><span data-stu-id="83080-111">Define a new class that derives from the <xref:System.ServiceModel.EndpointIdentity> class.</span></span> <span data-ttu-id="83080-112">Este exemplo denomina a extensão `OrgEndpointIdentity`.</span><span class="sxs-lookup"><span data-stu-id="83080-112">This example names the extension `OrgEndpointIdentity`.</span></span>  
  
2.  <span data-ttu-id="83080-113">Adicionar membros privados junto com as propriedades que serão usados pelo estendido <xref:System.ServiceModel.Security.IdentityVerifier> classe para executar a verificação de identidade nos declarações no token de segurança retornado do serviço.</span><span class="sxs-lookup"><span data-stu-id="83080-113">Add private members along with properties that will be used by the extended <xref:System.ServiceModel.Security.IdentityVerifier> class to perform the identity check against claims in the security token returned from the service.</span></span> <span data-ttu-id="83080-114">Este exemplo define uma propriedade: o `OrganizationClaim` propriedade.</span><span class="sxs-lookup"><span data-stu-id="83080-114">This example defines one property: the `OrganizationClaim` property.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
     [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
### <a name="to-extend-the-identityverifier-class"></a><span data-ttu-id="83080-115">Estender a classe IdentityVerifier</span><span class="sxs-lookup"><span data-stu-id="83080-115">To extend the IdentityVerifier class</span></span>  
  
1.  <span data-ttu-id="83080-116">Definir uma nova classe que deriva de <xref:System.ServiceModel.Security.IdentityVerifier>.</span><span class="sxs-lookup"><span data-stu-id="83080-116">Define a new class that derives from <xref:System.ServiceModel.Security.IdentityVerifier>.</span></span> <span data-ttu-id="83080-117">Este exemplo denomina a extensão `CustomIdentityVerifier`.</span><span class="sxs-lookup"><span data-stu-id="83080-117">This example names the extension `CustomIdentityVerifier`.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#7)]
     [!code-vb[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#7)]  
  
2.  <span data-ttu-id="83080-118">Substituir o método <xref:System.ServiceModel.Security.IdentityVerifier.CheckAccess%2A>.</span><span class="sxs-lookup"><span data-stu-id="83080-118">Override the <xref:System.ServiceModel.Security.IdentityVerifier.CheckAccess%2A> method.</span></span> <span data-ttu-id="83080-119">O método determina se a verificação de identidade foi bem-sucedida ou falhou.</span><span class="sxs-lookup"><span data-stu-id="83080-119">The method determines whether the identity check succeeded or failed.</span></span>  
  
3.  <span data-ttu-id="83080-120">O `CheckAccess` método tem dois parâmetros.</span><span class="sxs-lookup"><span data-stu-id="83080-120">The `CheckAccess` method has two parameters.</span></span> <span data-ttu-id="83080-121">A primeira é uma instância da <xref:System.ServiceModel.EndpointIdentity> classe.</span><span class="sxs-lookup"><span data-stu-id="83080-121">The first is an instance of the <xref:System.ServiceModel.EndpointIdentity> class.</span></span> <span data-ttu-id="83080-122">A segunda é uma instância da <xref:System.IdentityModel.Policy.AuthorizationContext> classe.</span><span class="sxs-lookup"><span data-stu-id="83080-122">The second is an instance of the <xref:System.IdentityModel.Policy.AuthorizationContext> class.</span></span>  
  
     <span data-ttu-id="83080-123">Na implementação do método, examine a coleção de declarações retornadas pela <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> propriedade do <xref:System.IdentityModel.Policy.AuthorizationContext> de classe e executar verificações de autenticação conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="83080-123">In the method implementation, examine the collection of claims returned by the <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> property of the <xref:System.IdentityModel.Policy.AuthorizationContext> class, and perform authentication checks as required.</span></span> <span data-ttu-id="83080-124">Este exemplo inicia Localizando qualquer declaração que é do tipo "Nome distinto" e, em seguida, compara o nome para a extensão do <xref:System.ServiceModel.EndpointIdentity> (`OrgEndpointIdentity`).</span><span class="sxs-lookup"><span data-stu-id="83080-124">This example begins by finding any claim that is of type "Distinguished Name" and then compares the name to the extension of the <xref:System.ServiceModel.EndpointIdentity> (`OrgEndpointIdentity`).</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#1)]
     [!code-vb[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#1)]  
  
### <a name="to-implement-the-trygetidentity-method"></a><span data-ttu-id="83080-125">Para implementar o método TryGetIdentity</span><span class="sxs-lookup"><span data-stu-id="83080-125">To implement the TryGetIdentity method</span></span>  
  
1.  <span data-ttu-id="83080-126">Implemente a <xref:System.ServiceModel.Security.IdentityVerifier.TryGetIdentity%2A> método, que determina se uma instância da <xref:System.ServiceModel.EndpointIdentity> classe pode ser retornado ao cliente.</span><span class="sxs-lookup"><span data-stu-id="83080-126">Implement the <xref:System.ServiceModel.Security.IdentityVerifier.TryGetIdentity%2A> method, which determines whether an instance of the <xref:System.ServiceModel.EndpointIdentity> class can be returned by the client.</span></span> <span data-ttu-id="83080-127">A infraestrutura do WCF chama a implementação da `TryGetIdentity` método primeiro para recuperar a identidade do serviço de mensagem.</span><span class="sxs-lookup"><span data-stu-id="83080-127">The WCF infrastructure calls the implementation of the `TryGetIdentity` method first to retrieve the service's identity from the message.</span></span> <span data-ttu-id="83080-128">Em seguida, chama a infraestrutura do `CheckAccess` implementação de com retornado `EndpointIdentity` e <xref:System.IdentityModel.Policy.AuthorizationContext>.</span><span class="sxs-lookup"><span data-stu-id="83080-128">Next, the infrastructure calls the `CheckAccess` implementation with the returned `EndpointIdentity` and <xref:System.IdentityModel.Policy.AuthorizationContext>.</span></span>  
  
2.  <span data-ttu-id="83080-129">No `TryGetIdentity` método, coloque o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="83080-129">In the `TryGetIdentity` method, put the following code:</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#2)]
     [!code-vb[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#2)]  
  
### <a name="to-implement-a-custom-binding-and-set-the-custom-identityverifier"></a><span data-ttu-id="83080-130">Para implementar uma ligação personalizada e definir o IdentityVerifier personalizado</span><span class="sxs-lookup"><span data-stu-id="83080-130">To implement a custom binding and set the custom IdentityVerifier</span></span>  
  
1.  <span data-ttu-id="83080-131">Criar um método que retorna um <xref:System.ServiceModel.Channels.Binding> objeto.</span><span class="sxs-lookup"><span data-stu-id="83080-131">Create a method that returns a <xref:System.ServiceModel.Channels.Binding> object.</span></span> <span data-ttu-id="83080-132">Este exemplo começa cria uma instância das <xref:System.ServiceModel.WSHttpBinding> de classe e define seu modo de segurança para <xref:System.ServiceModel.SecurityMode.Message>e seu <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> para <xref:System.ServiceModel.MessageCredentialType.None>.</span><span class="sxs-lookup"><span data-stu-id="83080-132">This example begins creates an instance of the <xref:System.ServiceModel.WSHttpBinding> class and sets its security mode to <xref:System.ServiceModel.SecurityMode.Message>, and its <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> to <xref:System.ServiceModel.MessageCredentialType.None>.</span></span>  
  
2.  <span data-ttu-id="83080-133">Criar uma <xref:System.ServiceModel.Channels.BindingElementCollection> usando o <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> método.</span><span class="sxs-lookup"><span data-stu-id="83080-133">Create a <xref:System.ServiceModel.Channels.BindingElementCollection> using the <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> method.</span></span>  
  
3.  <span data-ttu-id="83080-134">Retornar o <xref:System.ServiceModel.Channels.SecurityBindingElement> da coleção e convertê-lo em um <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> variável.</span><span class="sxs-lookup"><span data-stu-id="83080-134">Return the <xref:System.ServiceModel.Channels.SecurityBindingElement> from the collection and cast it to a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> variable.</span></span>  
  
4.  <span data-ttu-id="83080-135">Defina a <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.IdentityVerifier%2A> propriedade do <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> uma nova instância da classe a `CustomIdentityVerifier` classe criada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="83080-135">Set the <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.IdentityVerifier%2A> property of the <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> class to a new instance of the `CustomIdentityVerifier` class created previously.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#3)]
     [!code-vb[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#3)]  
  
5.  <span data-ttu-id="83080-136">A associação personalizada que é retornada é usada para criar uma instância do cliente e a classe.</span><span class="sxs-lookup"><span data-stu-id="83080-136">The custom binding that is returned is used to create an instance of the client and class.</span></span> <span data-ttu-id="83080-137">O cliente, em seguida, poderá executar uma verificação de identidade personalizada do serviço, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="83080-137">The client can then perform a custom identity verification check of the service as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#4)]
     [!code-vb[c_HowToSetCustomClientIdentity#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="83080-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="83080-138">Example</span></span>  
 <span data-ttu-id="83080-139">O exemplo a seguir mostra uma implementação completa da <xref:System.ServiceModel.Security.IdentityVerifier> classe.</span><span class="sxs-lookup"><span data-stu-id="83080-139">The following example shows a complete implementation of the <xref:System.ServiceModel.Security.IdentityVerifier> class.</span></span>  
  
 [!code-csharp[c_HowToSetCustomClientIdentity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#5)]
 [!code-vb[c_HowToSetCustomClientIdentity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="83080-140">Exemplo</span><span class="sxs-lookup"><span data-stu-id="83080-140">Example</span></span>  
 <span data-ttu-id="83080-141">O exemplo a seguir mostra uma implementação completa da <xref:System.ServiceModel.EndpointIdentity> classe.</span><span class="sxs-lookup"><span data-stu-id="83080-141">The following example shows a complete implementation of the <xref:System.ServiceModel.EndpointIdentity> class.</span></span>  
  
 [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
 [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="83080-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="83080-142">See also</span></span>
- <xref:System.ServiceModel.ServiceAuthorizationManager>
- <xref:System.ServiceModel.EndpointIdentity>
- <xref:System.ServiceModel.Security.IdentityVerifier>
- [<span data-ttu-id="83080-143">Exemplo de identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="83080-143">Service Identity Sample</span></span>](../../../../docs/framework/wcf/samples/service-identity-sample.md)
- [<span data-ttu-id="83080-144">Política de autorização</span><span class="sxs-lookup"><span data-stu-id="83080-144">Authorization Policy</span></span>](../../../../docs/framework/wcf/samples/authorization-policy.md)
- [<span data-ttu-id="83080-145">Política de autorização</span><span class="sxs-lookup"><span data-stu-id="83080-145">Authorization Policy</span></span>](../../../../docs/framework/wcf/samples/authorization-policy.md)
