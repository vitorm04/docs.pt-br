---
title: Como restringir acesso com a PrincipalPermissionAttribute class
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PrincipalPermissionAttribute class
- WCF, authorization
- WCF, security
ms.assetid: 5162f5c4-8781-4cc4-9425-bb7620eaeaf4
ms.openlocfilehash: 93268be4b04ec6824ed7ecab070f28ddf40f8831
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320936"
---
# <a name="how-to-restrict-access-with-the-principalpermissionattribute-class"></a><span data-ttu-id="352a7-102">Como restringir acesso com a PrincipalPermissionAttribute class</span><span class="sxs-lookup"><span data-stu-id="352a7-102">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>
<span data-ttu-id="352a7-103">Controlar o acesso a recursos em um computador de domínio do Windows é uma tarefa de segurança básica.</span><span class="sxs-lookup"><span data-stu-id="352a7-103">Controlling the access to resources on a Windows-domain computer is a basic security task.</span></span> <span data-ttu-id="352a7-104">Por exemplo, somente determinados usuários devem ser capazes de exibir dados confidenciais, como informações de folha de pagamento.</span><span class="sxs-lookup"><span data-stu-id="352a7-104">For example, only certain users should be able to view sensitive data, such as payroll information.</span></span> <span data-ttu-id="352a7-105">Este tópico explica como restringir o acesso a um método, exigindo que o usuário pertença a um grupo predefinido.</span><span class="sxs-lookup"><span data-stu-id="352a7-105">This topic explains how to restrict access to a method by demanding that the user belong to a predefined group.</span></span> <span data-ttu-id="352a7-106">Para obter um exemplo funcional, consulte [autorizando o acesso às operações de serviço](./samples/authorizing-access-to-service-operations.md).</span><span class="sxs-lookup"><span data-stu-id="352a7-106">For a working sample, see [Authorizing Access to Service Operations](./samples/authorizing-access-to-service-operations.md).</span></span>  
  
 <span data-ttu-id="352a7-107">A tarefa consiste em dois procedimentos separados.</span><span class="sxs-lookup"><span data-stu-id="352a7-107">The task consists of two separate procedures.</span></span> <span data-ttu-id="352a7-108">O primeiro cria o grupo e o popula com os usuários.</span><span class="sxs-lookup"><span data-stu-id="352a7-108">The first creates the group and populates it with users.</span></span> <span data-ttu-id="352a7-109">O segundo aplica a classe <xref:System.Security.Permissions.PrincipalPermissionAttribute> para especificar o grupo.</span><span class="sxs-lookup"><span data-stu-id="352a7-109">The second applies the <xref:System.Security.Permissions.PrincipalPermissionAttribute> class to specify the group.</span></span>  
  
### <a name="to-create-a-windows-group"></a><span data-ttu-id="352a7-110">Para criar um grupo do Windows</span><span class="sxs-lookup"><span data-stu-id="352a7-110">To create a Windows group</span></span>  
  
1. <span data-ttu-id="352a7-111">Abra o console de **Gerenciamento do computador** .</span><span class="sxs-lookup"><span data-stu-id="352a7-111">Open the **Computer Management** console.</span></span>  
  
2. <span data-ttu-id="352a7-112">No painel esquerdo, clique em **usuários e grupos locais**.</span><span class="sxs-lookup"><span data-stu-id="352a7-112">In the left panel, click **Local Users and Groups**.</span></span>  
  
3. <span data-ttu-id="352a7-113">Clique com o botão direito do mouse em **grupos**e clique em **novo grupo**.</span><span class="sxs-lookup"><span data-stu-id="352a7-113">Right-click **Groups**, and click **New Group**.</span></span>  
  
4. <span data-ttu-id="352a7-114">Na caixa **nome do grupo** , digite um nome para o novo grupo.</span><span class="sxs-lookup"><span data-stu-id="352a7-114">In the **Group Name** box, type a name for the new group.</span></span>  
  
5. <span data-ttu-id="352a7-115">Na caixa **Descrição** , digite uma descrição do novo grupo.</span><span class="sxs-lookup"><span data-stu-id="352a7-115">In the **Description** box, type a description of the new group.</span></span>  
  
6. <span data-ttu-id="352a7-116">Clique no botão **Adicionar** para adicionar novos membros ao grupo.</span><span class="sxs-lookup"><span data-stu-id="352a7-116">Click the **Add** button to add new members to the group.</span></span>  
  
7. <span data-ttu-id="352a7-117">Se você tiver se adicionado ao grupo e desejar testar o código a seguir, será necessário fazer logoff do computador e fazer logon novamente para que ele seja incluído no grupo.</span><span class="sxs-lookup"><span data-stu-id="352a7-117">If you have added yourself to the group and want to test the following code, you must log off the computer and log back on to be included in the group.</span></span>  
  
### <a name="to-demand-user-membership"></a><span data-ttu-id="352a7-118">Para solicitar a associação do usuário</span><span class="sxs-lookup"><span data-stu-id="352a7-118">To demand user membership</span></span>  
  
1. <span data-ttu-id="352a7-119">Abra o arquivo de código Windows Communication Foundation (WCF) que contém o código do contrato de serviço implementado.</span><span class="sxs-lookup"><span data-stu-id="352a7-119">Open the Windows Communication Foundation (WCF) code file that contains the implemented service contract code.</span></span> <span data-ttu-id="352a7-120">Para obter mais informações sobre como implementar um contrato, consulte [implementando contratos de serviço](implementing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="352a7-120">For more information about implementing a contract, see [Implementing Service Contracts](implementing-service-contracts.md).</span></span>  
  
2. <span data-ttu-id="352a7-121">Aplique o atributo <xref:System.Security.Permissions.PrincipalPermissionAttribute> a cada método que deve ser restrito a um grupo específico.</span><span class="sxs-lookup"><span data-stu-id="352a7-121">Apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to each method that must be restricted to a specific group.</span></span> <span data-ttu-id="352a7-122">Defina a propriedade <xref:System.Security.Permissions.SecurityAttribute.Action%2A> como <xref:System.Security.Permissions.SecurityAction.Demand> e a propriedade <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A> como o nome do grupo.</span><span class="sxs-lookup"><span data-stu-id="352a7-122">Set the <xref:System.Security.Permissions.SecurityAttribute.Action%2A> property to <xref:System.Security.Permissions.SecurityAction.Demand> and the <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A> property to the name of the group.</span></span> <span data-ttu-id="352a7-123">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="352a7-123">For example:</span></span>  
  
     [!code-csharp[c_PrincipalPermissionAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#1)]
     [!code-vb[c_PrincipalPermissionAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#1)]  
  
    > [!NOTE]
    > <span data-ttu-id="352a7-124">Se você aplicar o atributo <xref:System.Security.Permissions.PrincipalPermissionAttribute> a um contrato, um <xref:System.Security.SecurityException> será gerado.</span><span class="sxs-lookup"><span data-stu-id="352a7-124">If you apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to a contract a <xref:System.Security.SecurityException> will be thrown.</span></span> <span data-ttu-id="352a7-125">Você só pode aplicar o atributo no nível do método.</span><span class="sxs-lookup"><span data-stu-id="352a7-125">You can only apply the attribute at the method level.</span></span>  
  
## <a name="using-a-certificate-to-control-access-to-a-method"></a><span data-ttu-id="352a7-126">Usando um certificado para controlar o acesso a um método</span><span class="sxs-lookup"><span data-stu-id="352a7-126">Using a Certificate to Control Access to a Method</span></span>  
 <span data-ttu-id="352a7-127">Você também pode usar a classe `PrincipalPermissionAttribute` para controlar o acesso a um método se o tipo de credencial do cliente for um certificado.</span><span class="sxs-lookup"><span data-stu-id="352a7-127">You can also use the `PrincipalPermissionAttribute` class to control access to a method if the client credential type is a certificate.</span></span> <span data-ttu-id="352a7-128">Para fazer isso, você deve ter o assunto e a impressão digital do certificado.</span><span class="sxs-lookup"><span data-stu-id="352a7-128">To do this, you must have the certificate's subject and thumbprint.</span></span>  
  
 <span data-ttu-id="352a7-129">Para examinar um certificado para suas propriedades, consulte [como exibir certificados com o snap-in do MMC](./feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="352a7-129">To examine a certificate for its properties, see [How to: View Certificates with the MMC Snap-in](./feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span></span> <span data-ttu-id="352a7-130">Para localizar o valor da impressão digital, consulte [como recuperar a impressão digital de um certificado](./feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="352a7-130">To find the thumbprint value, see [How to: Retrieve the Thumbprint of a Certificate](./feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
#### <a name="to-control-access-using-a-certificate"></a><span data-ttu-id="352a7-131">Para controlar o acesso usando um certificado</span><span class="sxs-lookup"><span data-stu-id="352a7-131">To control access using a certificate</span></span>  
  
1. <span data-ttu-id="352a7-132">Aplique a classe <xref:System.Security.Permissions.PrincipalPermissionAttribute> ao método ao qual você deseja restringir o acesso.</span><span class="sxs-lookup"><span data-stu-id="352a7-132">Apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> class to the method you want to restrict access to.</span></span>  
  
2. <span data-ttu-id="352a7-133">Defina a ação do atributo como <xref:System.Security.Permissions.SecurityAction.Demand?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="352a7-133">Set the action of the attribute to <xref:System.Security.Permissions.SecurityAction.Demand?displayProperty=nameWithType>.</span></span>  
  
3. <span data-ttu-id="352a7-134">Defina a propriedade `Name` como uma cadeia de caracteres que consiste no nome da entidade e na impressão digital do certificado.</span><span class="sxs-lookup"><span data-stu-id="352a7-134">Set the `Name` property to a string that consists of the subject name and the certificate's thumbprint.</span></span> <span data-ttu-id="352a7-135">Separe os dois valores com um ponto e vírgula e um espaço, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="352a7-135">Separate the two values with a semicolon and a space, as shown in the following example:</span></span>  
  
     [!code-csharp[c_PrincipalPermissionAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#2)]
     [!code-vb[c_PrincipalPermissionAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#2)]  
  
4. <span data-ttu-id="352a7-136">Defina a propriedade <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> como <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>, conforme mostrado no exemplo de configuração a seguir:</span><span class="sxs-lookup"><span data-stu-id="352a7-136">Set the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> property to <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles> as shown in the following configuration example:</span></span>  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
      <behavior name="SvcBehavior1">  
      <serviceAuthorization principalPermissionMode="UseAspNetRoles" />  
      </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     <span data-ttu-id="352a7-137">Definir esse valor como `UseAspNetRoles` indica que a propriedade `Name` do `PrincipalPermissionAttribute` será usada para executar uma comparação de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="352a7-137">Setting this value to `UseAspNetRoles` indicates that the `Name` property of the `PrincipalPermissionAttribute` will be used to perform a string comparison.</span></span> <span data-ttu-id="352a7-138">Quando um certificado é usado como uma credencial de cliente, por padrão, o WCF concatena o nome comum do certificado e a impressão digital com um ponto e vírgula para criar um valor exclusivo para a identidade primária do cliente.</span><span class="sxs-lookup"><span data-stu-id="352a7-138">When a certificate is used as a client credential, by default WCF concatenates the certificate common name and the thumbprint with a semicolon to create a unique value for the client's primary identity.</span></span> <span data-ttu-id="352a7-139">Com `UseAspNetRoles` definido como o `PrincipalPermissionMode` no serviço, esse valor de identidade principal é comparado com o valor da propriedade `Name` para determinar os direitos de acesso do usuário.</span><span class="sxs-lookup"><span data-stu-id="352a7-139">With `UseAspNetRoles` set as the `PrincipalPermissionMode` on the service, this primary identity value is compared with the `Name` property value to determine the access rights of the user.</span></span>  
  
     <span data-ttu-id="352a7-140">Como alternativa, ao criar um serviço auto-hospedado, defina a propriedade <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> no código, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="352a7-140">Alternatively, when creating a self-hosted service, set the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> property in code as shown in the following code:</span></span>  
  
     [!code-csharp[c_PrincipalPermissionAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#3)]
     [!code-vb[c_PrincipalPermissionAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="352a7-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="352a7-141">See also</span></span>

- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- <xref:System.Security.Permissions.SecurityAction.Demand>
- <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A>
- [<span data-ttu-id="352a7-142">Autorizando o acesso a operações de serviço</span><span class="sxs-lookup"><span data-stu-id="352a7-142">Authorizing Access to Service Operations</span></span>](./samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="352a7-143">Visão geral de segurança</span><span class="sxs-lookup"><span data-stu-id="352a7-143">Security Overview</span></span>](./feature-details/security-overview.md)
- [<span data-ttu-id="352a7-144">Implementando contratos de serviço</span><span class="sxs-lookup"><span data-stu-id="352a7-144">Implementing Service Contracts</span></span>](implementing-service-contracts.md)
