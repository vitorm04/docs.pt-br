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
ms.openlocfilehash: 38e3c62aaf0e87860732bcb12c61da69b1c4346d
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33805766"
---
# <a name="how-to-restrict-access-with-the-principalpermissionattribute-class"></a>Como restringir acesso com a PrincipalPermissionAttribute class
Controlar o acesso aos recursos em um computador de domínio do Windows é uma tarefa de segurança básico. Por exemplo, somente a certos usuários devem ser capazes de exibir dados confidenciais, como informações de folha de pagamento. Este tópico explica como restringir o acesso a um método exigindo que o usuário pertence a um grupo predefinido. Para obter um exemplo de funcionamento, consulte [autorizar o acesso a operações de serviço](../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md).  
  
 A tarefa consiste em dois procedimentos separados. O primeiro cria o grupo e a preenche com os usuários. O segundo aplica o <xref:System.Security.Permissions.PrincipalPermissionAttribute> classe para especificar o grupo.  
  
### <a name="to-create-a-windows-group"></a>Para criar um grupo do Windows  
  
1.  Abra o **gerenciamento do computador** console.  
  
2.  No painel esquerdo, clique em **usuários e grupos locais**.  
  
3.  Clique com botão direito **grupos**e clique em **novo grupo**.  
  
4.  No **nome do grupo** , digite um nome para o novo grupo.  
  
5.  No **descrição** , digite uma descrição do novo grupo.  
  
6.  Clique o **adicionar** botão para adicionar novos membros ao grupo.  
  
7.  Se você tiver adicionado por conta própria para o grupo e para testar o código a seguir, você deve fazer logoff do computador e logon novamente para ser incluído no grupo.  
  
### <a name="to-demand-user-membership"></a>A associação do usuário por demanda  
  
1.  Abra o arquivo de código do Windows Communication Foundation (WCF) que contém o código de contrato de serviço implementado. Para obter mais informações sobre como implementar um contrato, consulte [implementando contratos de serviço](../../../docs/framework/wcf/implementing-service-contracts.md).  
  
2.  Aplicar o <xref:System.Security.Permissions.PrincipalPermissionAttribute> de atributo para cada método que deve ser restrito a um grupo específico. Definir o <xref:System.Security.Permissions.SecurityAttribute.Action%2A> propriedade <xref:System.Security.Permissions.SecurityAction.Demand> e o <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A> propriedade para o nome do grupo. Por exemplo:  
  
     [!code-csharp[c_PrincipalPermissionAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#1)]
     [!code-vb[c_PrincipalPermissionAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#1)]  
  
    > [!NOTE]
    >  Se você aplicar o <xref:System.Security.Permissions.PrincipalPermissionAttribute> de atributo para um contrato de um <xref:System.Security.SecurityException> será lançada. Você só pode aplicar o atributo no nível de método.  
  
## <a name="using-a-certificate-to-control-access-to-a-method"></a>Usando um certificado para controlar o acesso a um método  
 Você também pode usar o `PrincipalPermissionAttribute` classe para controlar o acesso a um método se o tipo de credencial de cliente é um certificado. Para fazer isso, você deve ter o assunto e a impressão digital do certificado.  
  
 Para examinar um certificado para suas propriedades, consulte [como: exibir certificados com o Snap-in do MMC](../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md). Para localizar o valor de impressão digital, consulte [como: recuperar a impressão digital de um certificado](../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
#### <a name="to-control-access-using-a-certificate"></a>Para controlar o acesso usando um certificado  
  
1.  Aplicar o <xref:System.Security.Permissions.PrincipalPermissionAttribute> classe para o método que você deseja restringir o acesso.  
  
2.  Definir a ação do atributo <xref:System.Security.Permissions.SecurityAction.Demand?displayProperty=nameWithType>.  
  
3.  Definir o `Name` propriedade como uma cadeia de caracteres que consiste do nome da entidade e impressão digital do certificado. Separe os dois valores com um ponto e vírgula e um espaço, conforme mostrado no exemplo a seguir:  
  
     [!code-csharp[c_PrincipalPermissionAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#2)]
     [!code-vb[c_PrincipalPermissionAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#2)]  
  
4.  Definir o <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> propriedade <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles> conforme mostrado no exemplo de configuração a seguir:  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
      <behavior name="SvcBehavior1">  
      <serviceAuthorization principalPermissionMode="UseAspNetRoles" />  
      </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     Definir esse valor como `UseAspNetRoles` indica que o `Name` propriedade o `PrincipalPermissionAttribute` será usado para realizar uma comparação de cadeia de caracteres. Quando um certificado é usado como uma credencial de cliente, por padrão WCF concatena o nome comum do certificado e a impressão digital com um ponto e vírgula para criar um valor exclusivo para a identidade do cliente principal. Com `UseAspNetRoles` definido como o `PrincipalPermissionMode` no serviço, esse valor de identidade primária é comparado com o `Name` valor da propriedade para determinar os direitos de acesso do usuário.  
  
     Como alternativa, ao criar um serviço auto-hospedado, defina o <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> propriedade no código, conforme mostrado no código a seguir:  
  
     [!code-csharp[c_PrincipalPermissionAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#3)]
     [!code-vb[c_PrincipalPermissionAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#3)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
 <xref:System.Security.Permissions.SecurityAction.Demand>  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A>  
 [Autorizando o acesso a operações de serviço](../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)  
 [Visão geral de segurança](../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Implementando contratos de serviço](../../../docs/framework/wcf/implementing-service-contracts.md)
