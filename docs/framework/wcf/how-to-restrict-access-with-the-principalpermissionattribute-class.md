---
title: Como restringir acesso com a PrincipalPermissionAttribute class
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
- PrincipalPermissionAttribute class
- WCF, authorization
- WCF, security
ms.assetid: 5162f5c4-8781-4cc4-9425-bb7620eaeaf4
caps.latest.revision: "23"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: afee838dac830d060ac933f314d3a57dcc11d603
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-restrict-access-with-the-principalpermissionattribute-class"></a><span data-ttu-id="80574-102">Como restringir acesso com a PrincipalPermissionAttribute class</span><span class="sxs-lookup"><span data-stu-id="80574-102">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>
<span data-ttu-id="80574-103">Controlar o acesso aos recursos em um computador de domínio do Windows é uma tarefa de segurança básico.</span><span class="sxs-lookup"><span data-stu-id="80574-103">Controlling the access to resources on a Windows-domain computer is a basic security task.</span></span> <span data-ttu-id="80574-104">Por exemplo, somente a certos usuários devem ser capazes de exibir dados confidenciais, como informações de folha de pagamento.</span><span class="sxs-lookup"><span data-stu-id="80574-104">For example, only certain users should be able to view sensitive data, such as payroll information.</span></span> <span data-ttu-id="80574-105">Este tópico explica como restringir o acesso a um método exigindo que o usuário pertence a um grupo predefinido.</span><span class="sxs-lookup"><span data-stu-id="80574-105">This topic explains how to restrict access to a method by demanding that the user belong to a predefined group.</span></span> <span data-ttu-id="80574-106">Para obter um exemplo de funcionamento, consulte [autorizar o acesso a operações de serviço](../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md).</span><span class="sxs-lookup"><span data-stu-id="80574-106">For a working sample, see [Authorizing Access to Service Operations](../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md).</span></span>  
  
 <span data-ttu-id="80574-107">A tarefa consiste em dois procedimentos separados.</span><span class="sxs-lookup"><span data-stu-id="80574-107">The task consists of two separate procedures.</span></span> <span data-ttu-id="80574-108">O primeiro cria o grupo e a preenche com os usuários.</span><span class="sxs-lookup"><span data-stu-id="80574-108">The first creates the group and populates it with users.</span></span> <span data-ttu-id="80574-109">O segundo aplica o <xref:System.Security.Permissions.PrincipalPermissionAttribute> classe para especificar o grupo.</span><span class="sxs-lookup"><span data-stu-id="80574-109">The second applies the <xref:System.Security.Permissions.PrincipalPermissionAttribute> class to specify the group.</span></span>  
  
### <a name="to-create-a-windows-group"></a><span data-ttu-id="80574-110">Para criar um grupo do Windows</span><span class="sxs-lookup"><span data-stu-id="80574-110">To create a Windows group</span></span>  
  
1.  <span data-ttu-id="80574-111">Abra o **gerenciamento do computador** console.</span><span class="sxs-lookup"><span data-stu-id="80574-111">Open the **Computer Management** console.</span></span>  
  
2.  <span data-ttu-id="80574-112">No painel esquerdo, clique em **usuários e grupos locais**.</span><span class="sxs-lookup"><span data-stu-id="80574-112">In the left panel, click **Local Users and Groups**.</span></span>  
  
3.  <span data-ttu-id="80574-113">Clique com botão direito **grupos**e clique em **novo grupo**.</span><span class="sxs-lookup"><span data-stu-id="80574-113">Right-click **Groups**, and click **New Group**.</span></span>  
  
4.  <span data-ttu-id="80574-114">No **nome do grupo** , digite um nome para o novo grupo.</span><span class="sxs-lookup"><span data-stu-id="80574-114">In the **Group Name** box, type a name for the new group.</span></span>  
  
5.  <span data-ttu-id="80574-115">No **descrição** , digite uma descrição do novo grupo.</span><span class="sxs-lookup"><span data-stu-id="80574-115">In the **Description** box, type a description of the new group.</span></span>  
  
6.  <span data-ttu-id="80574-116">Clique o **adicionar** botão para adicionar novos membros ao grupo.</span><span class="sxs-lookup"><span data-stu-id="80574-116">Click the **Add** button to add new members to the group.</span></span>  
  
7.  <span data-ttu-id="80574-117">Se você tiver adicionado por conta própria para o grupo e para testar o código a seguir, você deve fazer logoff do computador e logon novamente para ser incluído no grupo.</span><span class="sxs-lookup"><span data-stu-id="80574-117">If you have added yourself to the group and want to test the following code, you must log off the computer and log back on to be included in the group.</span></span>  
  
### <a name="to-demand-user-membership"></a><span data-ttu-id="80574-118">A associação do usuário por demanda</span><span class="sxs-lookup"><span data-stu-id="80574-118">To demand user membership</span></span>  
  
1.  <span data-ttu-id="80574-119">Abra o [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] arquivo de código que contém o código de contrato de serviço implementado.</span><span class="sxs-lookup"><span data-stu-id="80574-119">Open the [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] code file that contains the implemented service contract code.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="80574-120">implementar um contrato, consulte [implementando contratos de serviço](../../../docs/framework/wcf/implementing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="80574-120"> implementing a contract, see [Implementing Service Contracts](../../../docs/framework/wcf/implementing-service-contracts.md).</span></span>  
  
2.  <span data-ttu-id="80574-121">Aplicar o <xref:System.Security.Permissions.PrincipalPermissionAttribute> de atributo para cada método que deve ser restrito a um grupo específico.</span><span class="sxs-lookup"><span data-stu-id="80574-121">Apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to each method that must be restricted to a specific group.</span></span> <span data-ttu-id="80574-122">Definir o <xref:System.Security.Permissions.SecurityAttribute.Action%2A> propriedade <xref:System.Security.Permissions.SecurityAction.Demand> e o <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A> propriedade para o nome do grupo.</span><span class="sxs-lookup"><span data-stu-id="80574-122">Set the <xref:System.Security.Permissions.SecurityAttribute.Action%2A> property to <xref:System.Security.Permissions.SecurityAction.Demand> and the <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A> property to the name of the group.</span></span> <span data-ttu-id="80574-123">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="80574-123">For example:</span></span>  
  
     [!code-csharp[c_PrincipalPermissionAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#1)]
     [!code-vb[c_PrincipalPermissionAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#1)]  
  
    > [!NOTE]
    >  <span data-ttu-id="80574-124">Se você aplicar o <xref:System.Security.Permissions.PrincipalPermissionAttribute> de atributo para um contrato de um <xref:System.Security.SecurityException> será lançada.</span><span class="sxs-lookup"><span data-stu-id="80574-124">If you apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to a contract a <xref:System.Security.SecurityException> will be thrown.</span></span> <span data-ttu-id="80574-125">Você só pode aplicar o atributo no nível de método.</span><span class="sxs-lookup"><span data-stu-id="80574-125">You can only apply the attribute at the method level.</span></span>  
  
## <a name="using-a-certificate-to-control-access-to-a-method"></a><span data-ttu-id="80574-126">Usando um certificado para controlar o acesso a um método</span><span class="sxs-lookup"><span data-stu-id="80574-126">Using a Certificate to Control Access to a Method</span></span>  
 <span data-ttu-id="80574-127">Você também pode usar o `PrincipalPermissionAttribute` classe para controlar o acesso a um método se o tipo de credencial de cliente é um certificado.</span><span class="sxs-lookup"><span data-stu-id="80574-127">You can also use the `PrincipalPermissionAttribute` class to control access to a method if the client credential type is a certificate.</span></span> <span data-ttu-id="80574-128">Para fazer isso, você deve ter o assunto e a impressão digital do certificado.</span><span class="sxs-lookup"><span data-stu-id="80574-128">To do this, you must have the certificate's subject and thumbprint.</span></span>  
  
 <span data-ttu-id="80574-129">Para examinar um certificado para suas propriedades, consulte [como: exibir certificados com o Snap-in do MMC](../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="80574-129">To examine a certificate for its properties, see [How to: View Certificates with the MMC Snap-in](../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span></span> <span data-ttu-id="80574-130">Para localizar o valor de impressão digital, consulte [como: recuperar a impressão digital de um certificado](../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="80574-130">To find the thumbprint value, see [How to: Retrieve the Thumbprint of a Certificate](../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
#### <a name="to-control-access-using-a-certificate"></a><span data-ttu-id="80574-131">Para controlar o acesso usando um certificado</span><span class="sxs-lookup"><span data-stu-id="80574-131">To control access using a certificate</span></span>  
  
1.  <span data-ttu-id="80574-132">Aplicar o <xref:System.Security.Permissions.PrincipalPermissionAttribute> classe para o método que você deseja restringir o acesso.</span><span class="sxs-lookup"><span data-stu-id="80574-132">Apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> class to the method you want to restrict access to.</span></span>  
  
2.  <span data-ttu-id="80574-133">Definir a ação do atributo <xref:System.Security.Permissions.SecurityAction.Demand?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="80574-133">Set the action of the attribute to <xref:System.Security.Permissions.SecurityAction.Demand?displayProperty=nameWithType>.</span></span>  
  
3.  <span data-ttu-id="80574-134">Definir o `Name` propriedade como uma cadeia de caracteres que consiste do nome da entidade e impressão digital do certificado.</span><span class="sxs-lookup"><span data-stu-id="80574-134">Set the `Name` property to a string that consists of the subject name and the certificate's thumbprint.</span></span> <span data-ttu-id="80574-135">Separe os dois valores com um ponto e vírgula e um espaço, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="80574-135">Separate the two values with a semicolon and a space, as shown in the following example:</span></span>  
  
     [!code-csharp[c_PrincipalPermissionAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#2)]
     [!code-vb[c_PrincipalPermissionAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#2)]  
  
4.  <span data-ttu-id="80574-136">Definir o <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> propriedade <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles> conforme mostrado no exemplo de configuração a seguir:</span><span class="sxs-lookup"><span data-stu-id="80574-136">Set the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> property to <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles> as shown in the following configuration example:</span></span>  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
      <behavior name="SvcBehavior1">  
      <serviceAuthorization principalPermissionMode="UseAspNetRoles" />  
      </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     <span data-ttu-id="80574-137">Definir esse valor como `UseAspNetRoles` indica que o `Name` propriedade o `PrincipalPermissionAttribute` será usado para realizar uma comparação de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="80574-137">Setting this value to `UseAspNetRoles` indicates that the `Name` property of the `PrincipalPermissionAttribute` will be used to perform a string comparison.</span></span> <span data-ttu-id="80574-138">Quando um certificado é usado como uma credencial de cliente, por padrão [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] concatena o nome comum do certificado e a impressão digital com um ponto e vírgula para criar um valor exclusivo para a identidade do cliente principal.</span><span class="sxs-lookup"><span data-stu-id="80574-138">When a certificate is used as a client credential, by default [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] concatenates the certificate common name and the thumbprint with a semicolon to create a unique value for the client's primary identity.</span></span> <span data-ttu-id="80574-139">Com `UseAspNetRoles` definido como o `PrincipalPermissionMode` no serviço, esse valor de identidade primária é comparado com o `Name` valor da propriedade para determinar os direitos de acesso do usuário.</span><span class="sxs-lookup"><span data-stu-id="80574-139">With `UseAspNetRoles` set as the `PrincipalPermissionMode` on the service, this primary identity value is compared with the `Name` property value to determine the access rights of the user.</span></span>  
  
     <span data-ttu-id="80574-140">Como alternativa, ao criar um serviço auto-hospedado, defina o <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> propriedade no código, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="80574-140">Alternatively, when creating a self-hosted service, set the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> property in code as shown in the following code:</span></span>  
  
     [!code-csharp[c_PrincipalPermissionAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#3)]
     [!code-vb[c_PrincipalPermissionAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="80574-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="80574-141">See Also</span></span>  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
 <xref:System.Security.Permissions.SecurityAction.Demand>  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A>  
 [<span data-ttu-id="80574-142">Autorizando o acesso a operações de serviço</span><span class="sxs-lookup"><span data-stu-id="80574-142">Authorizing Access to Service Operations</span></span>](../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)  
 [<span data-ttu-id="80574-143">Visão geral de segurança</span><span class="sxs-lookup"><span data-stu-id="80574-143">Security Overview</span></span>](../../../docs/framework/wcf/feature-details/security-overview.md)  
 <span data-ttu-id="80574-144">[Implementing Service Contracts](../../../docs/framework/wcf/implementing-service-contracts.md) (Implementando contratos de serviço)</span><span class="sxs-lookup"><span data-stu-id="80574-144">[Implementing Service Contracts](../../../docs/framework/wcf/implementing-service-contracts.md)</span></span>
