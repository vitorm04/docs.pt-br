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
# <a name="how-to-restrict-access-with-the-principalpermissionattribute-class"></a>Como restringir acesso com a PrincipalPermissionAttribute class
Controlar o acesso a recursos em um computador de domínio do Windows é uma tarefa de segurança básica. Por exemplo, somente determinados usuários devem ser capazes de exibir dados confidenciais, como informações de folha de pagamento. Este tópico explica como restringir o acesso a um método, exigindo que o usuário pertença a um grupo predefinido. Para obter um exemplo funcional, consulte [autorizando o acesso às operações de serviço](./samples/authorizing-access-to-service-operations.md).  
  
 A tarefa consiste em dois procedimentos separados. O primeiro cria o grupo e o popula com os usuários. O segundo aplica a classe <xref:System.Security.Permissions.PrincipalPermissionAttribute> para especificar o grupo.  
  
### <a name="to-create-a-windows-group"></a>Para criar um grupo do Windows  
  
1. Abra o console de **Gerenciamento do computador** .  
  
2. No painel esquerdo, clique em **usuários e grupos locais**.  
  
3. Clique com o botão direito do mouse em **grupos**e clique em **novo grupo**.  
  
4. Na caixa **nome do grupo** , digite um nome para o novo grupo.  
  
5. Na caixa **Descrição** , digite uma descrição do novo grupo.  
  
6. Clique no botão **Adicionar** para adicionar novos membros ao grupo.  
  
7. Se você tiver se adicionado ao grupo e desejar testar o código a seguir, será necessário fazer logoff do computador e fazer logon novamente para que ele seja incluído no grupo.  
  
### <a name="to-demand-user-membership"></a>Para solicitar a associação do usuário  
  
1. Abra o arquivo de código Windows Communication Foundation (WCF) que contém o código do contrato de serviço implementado. Para obter mais informações sobre como implementar um contrato, consulte [implementando contratos de serviço](implementing-service-contracts.md).  
  
2. Aplique o atributo <xref:System.Security.Permissions.PrincipalPermissionAttribute> a cada método que deve ser restrito a um grupo específico. Defina a propriedade <xref:System.Security.Permissions.SecurityAttribute.Action%2A> como <xref:System.Security.Permissions.SecurityAction.Demand> e a propriedade <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A> como o nome do grupo. Por exemplo:  
  
     [!code-csharp[c_PrincipalPermissionAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#1)]
     [!code-vb[c_PrincipalPermissionAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#1)]  
  
    > [!NOTE]
    > Se você aplicar o atributo <xref:System.Security.Permissions.PrincipalPermissionAttribute> a um contrato, um <xref:System.Security.SecurityException> será gerado. Você só pode aplicar o atributo no nível do método.  
  
## <a name="using-a-certificate-to-control-access-to-a-method"></a>Usando um certificado para controlar o acesso a um método  
 Você também pode usar a classe `PrincipalPermissionAttribute` para controlar o acesso a um método se o tipo de credencial do cliente for um certificado. Para fazer isso, você deve ter o assunto e a impressão digital do certificado.  
  
 Para examinar um certificado para suas propriedades, consulte [como exibir certificados com o snap-in do MMC](./feature-details/how-to-view-certificates-with-the-mmc-snap-in.md). Para localizar o valor da impressão digital, consulte [como recuperar a impressão digital de um certificado](./feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
#### <a name="to-control-access-using-a-certificate"></a>Para controlar o acesso usando um certificado  
  
1. Aplique a classe <xref:System.Security.Permissions.PrincipalPermissionAttribute> ao método ao qual você deseja restringir o acesso.  
  
2. Defina a ação do atributo como <xref:System.Security.Permissions.SecurityAction.Demand?displayProperty=nameWithType>.  
  
3. Defina a propriedade `Name` como uma cadeia de caracteres que consiste no nome da entidade e na impressão digital do certificado. Separe os dois valores com um ponto e vírgula e um espaço, conforme mostrado no exemplo a seguir:  
  
     [!code-csharp[c_PrincipalPermissionAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#2)]
     [!code-vb[c_PrincipalPermissionAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#2)]  
  
4. Defina a propriedade <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> como <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>, conforme mostrado no exemplo de configuração a seguir:  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
      <behavior name="SvcBehavior1">  
      <serviceAuthorization principalPermissionMode="UseAspNetRoles" />  
      </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     Definir esse valor como `UseAspNetRoles` indica que a propriedade `Name` do `PrincipalPermissionAttribute` será usada para executar uma comparação de cadeia de caracteres. Quando um certificado é usado como uma credencial de cliente, por padrão, o WCF concatena o nome comum do certificado e a impressão digital com um ponto e vírgula para criar um valor exclusivo para a identidade primária do cliente. Com `UseAspNetRoles` definido como o `PrincipalPermissionMode` no serviço, esse valor de identidade principal é comparado com o valor da propriedade `Name` para determinar os direitos de acesso do usuário.  
  
     Como alternativa, ao criar um serviço auto-hospedado, defina a propriedade <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> no código, conforme mostrado no código a seguir:  
  
     [!code-csharp[c_PrincipalPermissionAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#3)]
     [!code-vb[c_PrincipalPermissionAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#3)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- <xref:System.Security.Permissions.SecurityAction.Demand>
- <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A>
- [Autorizando o acesso a operações de serviço](./samples/authorizing-access-to-service-operations.md)
- [Visão geral de segurança](./feature-details/security-overview.md)
- [Implementando contratos de serviço](implementing-service-contracts.md)
