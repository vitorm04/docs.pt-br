---
title: Identidade e autenticação de serviço
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- authentication [WCF], specifying the identity of a service
ms.assetid: a4c8f52c-5b30-45c4-a545-63244aba82be
ms.openlocfilehash: 21184098f90be3b64cfccd5ab98a1824cee50e48
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33508181"
---
# <a name="service-identity-and-authentication"></a>Identidade e autenticação de serviço
Um serviço *identidade do ponto de extremidade*é um valor gerado do serviço WSDL Web Services Description Language (). Esse valor, propagada para qualquer cliente, é usado para autenticar o serviço. Depois que o cliente inicia uma comunicação para um ponto de extremidade e o serviço se autentica para o cliente, o cliente compara o valor de identidade do ponto de extremidade com o valor real retornado o processo de autenticação de ponto de extremidade. Se elas corresponderem, o cliente terá certeza que ele contatou o ponto de extremidade de serviço esperada. Isso funciona como uma proteção contra *phishing* , impedindo que um cliente que está sendo redirecionado para um ponto de extremidade hospedado por um serviço mal-intencionado.  
  
 Para um aplicativo de exemplo que mostra a configuração de identidade, consulte [exemplo de identidade de serviço](../../../../docs/framework/wcf/samples/service-identity-sample.md). Para obter mais informações sobre pontos de extremidade e endereços de ponto de extremidade, consulte [endereços](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md).  
  
> [!NOTE]
>  Quando você usa LanMan NT (NTLM) para autenticação, a identidade do serviço não está marcada como sob NTLM, o cliente é capaz de autenticar o servidor. NTLM é usado quando os computadores fazem parte de um grupo de trabalho do Windows ou ao executar uma versão mais antiga do Windows que não dá suporte à autenticação de Kerberos.  
  
 Quando o cliente inicia um canal seguro para enviar uma mensagem para um serviço por ele, a infraestrutura do Windows Communication Foundation (WCF) autentica o serviço e envia a mensagem somente se a identidade de serviço coincide com a identidade especificada no ponto de extremidade o cliente usa o endereço.  
  
 Processamento de identidade consiste das seguintes etapas:  
  
-   Em tempo de design, o desenvolvedor do cliente determina a identidade do serviço de metadados do ponto de extremidade (exposto através de WSDL).  
  
-   Em tempo de execução, o aplicativo cliente verifica as declarações de credenciais de segurança do serviço antes de enviar as mensagens para o serviço.  
  
 Identidade de processamento no cliente é semelhante à autenticação de cliente no serviço. Um serviço seguro não executar código até que as credenciais do cliente foi autenticadas. Da mesma forma, o cliente envia mensagens para o serviço até que as credenciais do serviço foram autenticadas com base no que é conhecido com antecedência de metadados do serviço.  
  
 O <xref:System.ServiceModel.EndpointAddress.Identity%2A> propriedade o <xref:System.ServiceModel.EndpointAddress> classe representa a identidade do serviço chamado pelo cliente. O serviço publica o <xref:System.ServiceModel.EndpointAddress.Identity%2A> em seus metadados. Quando o desenvolvedor do cliente é executado o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) contra o ponto de extremidade de serviço, a configuração gerada contém o valor do serviço de <xref:System.ServiceModel.EndpointAddress.Identity%2A> propriedade. A infra-estrutura do WCF (se configurado com segurança) verifica se o serviço possui a identidade especificada.  
  
> [!IMPORTANT]
>  O metadados contém a identidade esperada do serviço, portanto, é recomendável que você exponha os metadados de serviço por meio de forma segura, por exemplo, ao criar um ponto de extremidade HTTPS para o serviço. Para obter mais informações, consulte [como: proteger pontos de extremidade de metadados](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md).  
  
## <a name="identity-types"></a>Tipos de identidade  
 Um serviço pode fornecer seis tipos de identidades. Cada tipo de identidade corresponde a um elemento que pode ser contido dentro de `<identity>` elemento na configuração. O tipo usado depende do cenário e requisitos de segurança do serviço. A tabela a seguir descreve cada tipo de identidade.  
  
|Tipo de identidade|Descrição|Cenário típico|  
|-------------------|-----------------|----------------------|  
|DNS (Sistema de Nomes de Domínio)|Use esse elemento com certificados x. 509 ou contas do Windows. Ele compara o nome DNS especificado na credencial com o valor especificado neste elemento.|Uma verificação DNS permite que você use certificados com o DNS ou nomes de entidade. Se um certificado seja enviado novamente com o mesmo DNS ou o nome da entidade, em seguida, a verificação de identidade ainda é válida. Quando um certificado for reemitido, ele obtém uma nova chave RSA, mas mantém o mesmo DNS ou o nome da entidade. Isso significa que os clientes não precisa atualizar as informações de identidade sobre o serviço.|  
|Certificado. O padrão quando `ClientCredentialType` está definida como Certificate.|Este elemento Especifica um valor de certificado x. 509 codificado na Base64 para comparar com o cliente.<br /><br /> Use também esse elemento ao usar um [!INCLUDE[infocard](../../../../includes/infocard-md.md)] como uma credencial para autenticar o serviço.|Esse elemento restringe a autenticação para um único certificado com base em seu valor de impressão digital. Isso permite a autenticação mais rígida porque os valores de impressão digital são exclusivos. Isso é fornecido com uma limitação: se o certificado seja enviado novamente com o mesmo nome de entidade, ele também tem uma nova impressão digital. Portanto, os clientes não são capazes de validar o serviço, a menos que a nova impressão digital é conhecida. Para obter mais informações sobre como encontrar a impressão digital do certificado, consulte [como: recuperar a impressão digital de um certificado](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).|  
|Referência de certificado|Idêntica à opção de certificado descrita anteriormente. No entanto, esse elemento permite que você especifique um nome de certificado e o local do qual recuperar o certificado do repositório.|Mesmo que o cenário de certificado descrito anteriormente.<br /><br /> A vantagem é que o local de armazenamento pode alterar.|  
|RSA|Este elemento Especifica um valor de chave RSA para comparar com o cliente. Isso é semelhante à opção de certificado, mas em vez de usar a impressão digital do certificado, chave RSA do certificado é usado em vez disso.|Uma verificação RSA permite restringir especificamente a autenticação para um único certificado com base em sua chave RSA. Isso permite a autenticação mais rígida de uma chave RSA específica às custas de serviço, que não funciona com os clientes existentes se altera o valor da chave RSA.|  
|Nome de usuário principal (UPN). O padrão quando o `ClientCredentialType` é definido para o Windows e o serviço de processo não está em execução em uma das contas do sistema.|Este elemento Especifica o UPN que o serviço está em execução. Consulte a seção de protocolo Kerberos e identidade [substituindo a identidade de um serviço de autenticação](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md).|Isso garante que o serviço está em execução em uma conta de usuário específica do Windows. A conta de usuário pode ser o usuário de logon atual ou o serviço executado sob uma conta de usuário específico.<br /><br /> Essa configuração se beneficia de segurança do Windows Kerberos se o serviço está em execução em uma conta de domínio em um ambiente do Active Directory.|  
|Nome principal do serviço (SPN). O padrão quando o `ClientCredentialType` é definido para o Windows e o serviço de processo está sendo executado em uma das contas do sistema — LocalService, LocalSystem ou NetworkService.|Este elemento Especifica o SPN associado à conta do serviço. Consulte a seção de protocolo Kerberos e identidade [substituindo a identidade de um serviço de autenticação](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md).|Isso garante que o SPN e a conta do Windows específica associada ao SPN identificam o serviço.<br /><br /> Você pode usar a ferramenta Setspn.exe para associar uma conta de computador para a conta de usuário do serviço.<br /><br /> Essa configuração se beneficia do Kerberos Windows segurança se o serviço está em execução em uma das contas de sistema ou em uma conta de domínio que tenha um nome SPN associado com ele e o computador é um membro de um domínio em um ambiente do Active Directory.|  
  
## <a name="specifying-identity-at-the-service"></a>Especificação de identidade de serviço  
 Normalmente, você não precisa definir a identidade de um serviço porque a seleção de um tipo de credencial de cliente determina o tipo de identidade exposto nos metadados do serviço. Para obter mais informações sobre como substituir ou especificar a identidade de serviço, consulte [substituindo a identidade de um serviço de autenticação](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md).  
  
## <a name="using-the-identity-element-in-configuration"></a>Usando o \<identidade > elemento na configuração  
 Se você alterar o tipo de credencial de cliente na associação mostrada anteriormente para `Certificate,` , em seguida, o WSDL gerado contém uma Base64 serializado certificado x. 509 para o valor de identidade, conforme mostrado no código a seguir. Esse é o padrão para todos os tipos de credencial de cliente diferentes do Windows.  
  
  
  
 Você pode alterar o valor da identidade do serviço padrão ou alterar o tipo de identidade usando o `<identity>` elemento na configuração ou definindo a identidade no código. O código de configuração a seguir define uma identidade do DNS (sistema) do nome de domínio com o valor `contoso.com`.  
  
  
  
## <a name="setting-identity-programmatically"></a>Definir a identidade por meio de programação  
 Seu serviço não precisa especificar explicitamente uma identidade, pois WCF determina automaticamente. No entanto, o WCF permite que você especifique uma identidade em um ponto de extremidade, se necessário. O código a seguir adiciona um novo ponto de extremidade de serviço com uma identidade específica de DNS.  
  
 [!code-csharp[C_Identity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_identity/cs/source.cs#5)]
 [!code-vb[C_Identity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_identity/vb/source.vb#5)]  
  
## <a name="specifying-identity-at-the-client"></a>Especificação de identidade no cliente  
 Em tempo de design, um desenvolvedor de cliente geralmente usa a [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para gerar a configuração do cliente. O arquivo de configuração gerado (deve ser usada pelo cliente) contém a identidade do servidor. Por exemplo, o código a seguir é gerado de um serviço que especifica uma identidade DNS, conforme mostrado no exemplo anterior. Observe que o valor de identidade do ponto de extremidade do cliente corresponda a que o serviço. Nesse caso, quando o cliente recebe as credenciais do Windows (Kerberos) para o serviço, ele espera o valor a ser `contoso.com`.  
  
  
  
 Se, em vez do Windows, o serviço Especifica um certificado como o tipo de credencial de cliente, propriedade DNS do certificado deve ser o valor `contoso.com`. (Ou se a propriedade DNS é `null`, nome da entidade do certificado deve ser `contoso.com`.)  
  
#### <a name="using-a-specific-value-for-identity"></a>Usando um valor específico para a identidade  
 O seguinte arquivo de configuração do cliente mostra como a identidade do serviço deve ser um valor específico. No exemplo a seguir, o cliente pode se comunicar com dois pontos de extremidade. A primeira é identificada com uma impressão digital do certificado e o segundo com uma chave RSA do certificado. Ou seja, um certificado que contenha somente é uma chave/particular da pública par de chaves, mas não foi emitido por uma autoridade confiável.  
  
  
  
## <a name="identity-checking-at-run-time"></a>A verificação em tempo de execução de identidade  
 Em tempo de design, um desenvolvedor de cliente determina a identidade do servidor por meio de seus metadados. Em tempo de execução, a verificação de identidade é executada antes de chamar qualquer ponto de extremidade do serviço.  
  
 O valor de identidade está associado ao tipo de autenticação especificado pelos metadados; em outras palavras, o tipo de credenciais usado para o serviço.  
  
 Se o canal está configurado para autenticar usando o nível de transporte ou mensagem de protocolo (SSL) com certificados x. 509 para autenticação, os seguintes valores de identidade são válidos:  
  
-   DNS. WCF garante que o certificado fornecido durante o handshake SSL contém um DNS ou `CommonName` atributo de (CN) igual ao valor especificado na identidade do DNS no cliente. Observe que essas verificações são feitas Além disso, para determinar a validade do certificado do servidor. Por padrão, o WCF valida que o certificado do servidor é emitido por uma autoridade raiz confiável.  
  
-   Certificado. Durante o handshake SSL, o WCF garante que o ponto de extremidade remoto fornece o valor exato do certificado especificado na identidade.  
  
-   Referência de certificado. Mesmo que o certificado.  
  
-   RSA. Durante o handshake SSL, o WCF garante que o ponto de extremidade remoto fornece a chave RSA exata especificada na identidade.  
  
 Se o serviço autentica usando o SSL de nível de transporte ou de mensagem com uma credencial do Windows para autenticação e negocia a credencial, os valores de identidade a seguir são válidos:  
  
-   DNS. A negociação passa o SPN do serviço para que o nome DNS pode ser verificado. O SPN está no formato `host/<dns name>`.  
  
-   SPN. Um serviço explícito SPN for retornado, por exemplo, `host/myservice`.  
  
-   UPN. O UPN da conta de serviço. O UPN está no formato `username` @ `domain`. Por exemplo, quando o serviço é executado em uma conta de usuário, pode ser `username@contoso.com`.  
  
 Especificando a identidade programaticamente (usando o <xref:System.ServiceModel.EndpointAddress.Identity%2A> propriedade) é opcional. Se nenhuma identidade é especificada, e o tipo de credencial de cliente for Windows, o padrão é o SPN com o valor definido para a parte do nome de host do endereço de ponto de extremidade de serviço prefixado com o "host /" literal. Se nenhuma identidade é especificada, e o tipo de credencial de cliente é um certificado, o padrão é `Certificate`. Isso se aplica a ambos os segurança em nível de mensagem e transporte.  
  
## <a name="identity-and-custom-bindings"></a>Identidade e associações personalizadas  
 Como a identidade de um serviço depende do tipo de associação usado, certifique-se de que uma identidade apropriada é exposta ao criar uma associação personalizada. Por exemplo, no exemplo de código a seguir, a identidade exposta não é compatível com o tipo de segurança, porque a identidade para a associação de inicialização de conversa segura não coincide com a identidade para a associação no ponto de extremidade. A associação de conversa segura define a identidade do DNS, enquanto o <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement> define a identidade UPN ou SPN.  
  
 [!code-csharp[C_Identity#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_identity/cs/source.cs#8)]
 [!code-vb[C_Identity#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_identity/vb/source.vb#8)]  
  
 Para obter mais informações sobre a associação de pilha elementos corretamente para uma associação personalizada, consulte [Criando associações](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md). Para obter mais informações sobre como criar uma associação personalizada com o <xref:System.ServiceModel.Channels.SecurityBindingElement>, consulte [como: criar um SecurityBindingElement para um modo de autenticação especificado](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md).  
  
## <a name="see-also"></a>Consulte também  
 [Como criar uma associação personalizada utilizando o SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [Como criar um SecurityBindingElement para um modo de autenticação especificado](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)  
 [Como criar um verificador de identidade de cliente personalizado](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md)  
 [Selecionando um tipo de credencial](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [Trabalhando com certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [Criando associações definidas pelo usuário](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)  
 [Como recuperar a impressão digital de um certificado](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
