---
title: 'Como: restringir o acesso com a classe PrincipalPermissionAttribute'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PrincipalPermissionAttribute class
- WCF, authorization
- WCF, security
ms.assetid: 5162f5c4-8781-4cc4-9425-bb7620eaeaf4
ms.openlocfilehash: 3b109e3e6817c300af1e79258d555562dcba067a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951021"
---
# <a name="how-to-restrict-access-with-the-principalpermissionattribute-class"></a>Como: restringir o acesso com a classe PrincipalPermissionAttribute
Controlar o acesso a recursos em um computador de domínio do Windows é uma tarefa de segurança básica. Por exemplo, somente determinados usuários devem ser capazes de exibir dados confidenciais, como informações de folha de pagamento. Este tópico explica como restringir o acesso a um método, exigindo que o usuário pertença a um grupo predefinido. Para obter um exemplo funcional, consulte autorizando o [acesso às operações de serviço](../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md).  
  
 A tarefa consiste em dois procedimentos separados. O primeiro cria o grupo e o popula com os usuários. O segundo aplica a <xref:System.Security.Permissions.PrincipalPermissionAttribute> classe para especificar o grupo.  
  
### <a name="to-create-a-windows-group"></a>Para criar um grupo do Windows  
  
1. Abra o console de **Gerenciamento do computador** .  
  
2. No painel esquerdo, clique em **usuários e grupos locais**.  
  
3. Clique com o botão direito do mouse em **grupos**e clique em **novo grupo**.  
  
4. Na caixa **nome do grupo** , digite um nome para o novo grupo.  
  
5. Na caixa **Descrição** , digite uma descrição do novo grupo.  
  
6. Clique no botão **Adicionar** para adicionar novos membros ao grupo.  
  
7. Se você tiver se adicionado ao grupo e desejar testar o código a seguir, será necessário fazer logoff do computador e fazer logon novamente para que ele seja incluído no grupo.  
  
### <a name="to-demand-user-membership"></a>Para solicitar a associação do usuário  
  
1. Abra o arquivo de código Windows Communication Foundation (WCF) que contém o código do contrato de serviço implementado. Para obter mais informações sobre como implementar um contrato, consulte [implementando contratos de serviço](../../../docs/framework/wcf/implementing-service-contracts.md).  
  
2. Aplique o <xref:System.Security.Permissions.PrincipalPermissionAttribute> atributo a cada método que deve ser restrito a um grupo específico. Defina a <xref:System.Security.Permissions.SecurityAttribute.Action%2A> Propriedade como <xref:System.Security.Permissions.SecurityAction.Demand> e a <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A> Propriedade como o nome do grupo. Por exemplo:  
  
     [!code-csharp[c_PrincipalPermissionAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#1)]
     [!code-vb[c_PrincipalPermissionAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#1)]  
  
    > [!NOTE]
    > Se você aplicar o <xref:System.Security.Permissions.PrincipalPermissionAttribute> atributo a um contrato, <xref:System.Security.SecurityException> um será gerado. Você só pode aplicar o atributo no nível do método.  
  
## <a name="using-a-certificate-to-control-access-to-a-method"></a>Usando um certificado para controlar o acesso a um método  
 Você também pode usar a `PrincipalPermissionAttribute` classe para controlar o acesso a um método se o tipo de credencial do cliente for um certificado. Para fazer isso, você deve ter o assunto e a impressão digital do certificado.  
  
 Para examinar um certificado para suas propriedades, consulte [como: Exibir certificados com o snap-in](../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)do MMC. Para localizar o valor da impressão digital [, consulte Como: Recupere a impressão digital de um](../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)certificado.  
  
#### <a name="to-control-access-using-a-certificate"></a>Para controlar o acesso usando um certificado  
  
1. Aplique a <xref:System.Security.Permissions.PrincipalPermissionAttribute> classe ao método ao qual você deseja restringir o acesso.  
  
2. Defina a ação do atributo como <xref:System.Security.Permissions.SecurityAction.Demand?displayProperty=nameWithType>.  
  
3. Defina a `Name` Propriedade como uma cadeia de caracteres que consiste no nome da entidade e na impressão digital do certificado. Separe os dois valores com um ponto e vírgula e um espaço, conforme mostrado no exemplo a seguir:  
  
     [!code-csharp[c_PrincipalPermissionAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#2)]
     [!code-vb[c_PrincipalPermissionAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#2)]  
  
4. Defina a <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles> Propriedade como, conforme mostrado no exemplo de configuração a seguir:  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
      <behavior name="SvcBehavior1">  
      <serviceAuthorization principalPermissionMode="UseAspNetRoles" />  
      </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     Definir esse valor como `UseAspNetRoles` indica que a `Name` propriedade de `PrincipalPermissionAttribute` será usada para executar uma comparação de cadeia de caracteres. Quando um certificado é usado como uma credencial de cliente, por padrão, o WCF concatena o nome comum do certificado e a impressão digital com um ponto e vírgula para criar um valor exclusivo para a identidade primária do cliente. Com `UseAspNetRoles` Set `Name` as no serviço, esse valor de identidade principal é comparado com o valor da propriedade para determinar os direitos de acesso do usuário. `PrincipalPermissionMode`  
  
     Como alternativa, ao criar um serviço auto-hospedado, defina a <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> Propriedade no código, conforme mostrado no código a seguir:  
  
     [!code-csharp[c_PrincipalPermissionAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#3)]
     [!code-vb[c_PrincipalPermissionAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#3)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- <xref:System.Security.Permissions.SecurityAction.Demand>
- <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A>
- [Autorizando o acesso a operações de serviço](../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)
- [Visão geral de segurança](../../../docs/framework/wcf/feature-details/security-overview.md)
- [Implementando contratos de serviço](../../../docs/framework/wcf/implementing-service-contracts.md)
