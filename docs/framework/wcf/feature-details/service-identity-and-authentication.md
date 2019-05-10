---
title: Identidade e autenticação de serviço
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- authentication [WCF], specifying the identity of a service
ms.assetid: a4c8f52c-5b30-45c4-a545-63244aba82be
ms.openlocfilehash: 834829d8eee95a8a62363a05b4af9430c435753b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64586234"
---
# <a name="service-identity-and-authentication"></a>Identidade e autenticação de serviço
Um serviço *identidade de ponto de extremidade* é um valor gerado do serviço de descrição de linguagem WSDL (Web Services). Esse valor, propagada para qualquer cliente, é usado para autenticar o serviço. Depois que o cliente inicia uma comunicação para um ponto de extremidade e o serviço autentica para o cliente, o cliente compara o valor de identidade do ponto de extremidade com o valor real retornado o processo de autenticação de ponto de extremidade. Se elas corresponderem, o cliente terá certeza que ele entrou em contato o ponto de extremidade de serviço esperada. Isso funciona como uma proteção contra *phishing* , impedindo que um cliente que está sendo redirecionado para um ponto de extremidade hospedado por um serviço mal-intencionado.  
  
 Para um aplicativo de exemplo que demonstra a configuração de identidade, consulte [exemplo de identidade de serviço](../../../../docs/framework/wcf/samples/service-identity-sample.md). Para obter mais informações sobre pontos de extremidade e endereços de ponto de extremidade, consulte [endereços](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md).  
  
> [!NOTE]
>  Quando você usa LanMan NT (NTLM) para autenticação, a identidade de serviço não é verificada porque, sob NTLM, o cliente é capaz de autenticar o servidor. NTLM é usado quando os computadores fazem parte de um grupo de trabalho do Windows, ou ao executar uma versão anterior do Windows que não dá suporte a autenticação Kerberos.  
  
 Quando o cliente inicia um canal seguro para enviar uma mensagem para um serviço sobre ele, a infraestrutura do Windows Communication Foundation (WCF) autentica o serviço e envia a mensagem apenas se a identidade de serviço corresponde a identidade especificada no ponto de extremidade o cliente usa o endereço.  
  
 Processamento de identidade consiste dos seguintes estágios:  
  
- Em tempo de design, o desenvolvedor cliente determina a identidade do serviço de metadados do ponto de extremidade (exposto por meio de WSDL).  
  
- Em tempo de execução, o aplicativo cliente verifica as declarações do serviço credenciais de segurança antes de enviar todas as mensagens para o serviço.  
  
 Identidade de processamento no cliente é análoga à autenticação de cliente no serviço. Um serviço seguro não executar o código até que as credenciais do cliente foram autenticadas. Da mesma forma, o cliente não enviará mensagens para o serviço até que as credenciais do serviço foram autenticadas com base no que é conhecido de antemão de metadados do serviço.  
  
 O <xref:System.ServiceModel.EndpointAddress.Identity%2A> propriedade do <xref:System.ServiceModel.EndpointAddress> classe representa a identidade do serviço chamado pelo cliente. O serviço publica a <xref:System.ServiceModel.EndpointAddress.Identity%2A> em seus metadados. Quando o desenvolvedor do cliente é executado o [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) contra o ponto de extremidade de serviço, a configuração gerada contém o valor do serviço de <xref:System.ServiceModel.EndpointAddress.Identity%2A> propriedade. A infraestrutura do WCF (se configurado com segurança) verifica se o serviço possui a identidade especificada.  
  
> [!IMPORTANT]
>  Os metadados contêm a identidade esperada do serviço, portanto, é recomendável que você exponha os metadados de serviço por meio de forma segura, por exemplo, com a criação de um ponto de extremidade HTTPS para o serviço. Para obter mais informações, confira [Como: Proteger pontos de extremidade de metadados](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md).  
  
## <a name="identity-types"></a>Tipos de identidade  
 Um serviço pode fornecer seis tipos de identidades. Cada tipo de identidade corresponde a um elemento que pode ser contido dentro de `<identity>` elemento na configuração. O tipo usado depende do cenário e requisitos de segurança do serviço. A tabela a seguir descreve cada tipo de identidade.  
  
|Tipo de identidade|Descrição|Cenário típico|  
|-------------------|-----------------|----------------------|  
|DNS (Sistema de Nomes de Domínio)|Use esse elemento com certificados x. 509 ou contas do Windows. Ele compara o nome DNS especificado na credencial com o valor especificado nesse elemento.|Uma verificação DNS permite que você use certificados com o DNS ou nomes de entidade. Se um certificado seja enviado novamente com o mesmo DNS ou o nome da entidade, em seguida, a verificação de identidade ainda é válida. Quando um certificado seja enviado novamente, ele obtém uma nova chave RSA, mas mantém a mesma DNS ou o nome da entidade. Isso significa que os clientes não precisará atualizar suas informações de identidade sobre o serviço.|  
|Certificado. O padrão quando `ClientCredentialType` está definida como Certificate.|Esse elemento Especifica um valor de certificado x. 509 codificado na Base64 a ser comparado com o cliente.<br /><br /> Use também esse elemento ao usar um [!INCLUDE[infocard](../../../../includes/infocard-md.md)] como uma credencial para autenticar o serviço.|Esse elemento restringe a autenticação para um único certificado com base em seu valor de impressão digital. Isso habilita a autenticação mais rígida porque os valores da impressão digital são exclusivos. Isso é fornecido com uma limitação: Se o certificado seja enviado novamente com o mesmo nome de assunto, ele também tem uma nova impressão digital. Portanto, os clientes não são capazes de validar o serviço, a menos que a nova impressão digital é conhecida. Para obter mais informações sobre como localizar uma impressão digital de certificado, consulte [como: Recuperar a impressão digital de um certificado](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).|  
|Referência de certificado|Idêntico à opção certificado descrita anteriormente. No entanto, esse elemento permite que você especifique um nome de certificado e o local do qual recuperar o certificado do repositório.|Mesmo que o cenário de certificado descrito anteriormente.<br /><br /> A vantagem é que o repositório de certificados local pode alterar.|  
|RSA|Esse elemento Especifica um valor de chave RSA a ser comparado com o cliente. Isso é semelhante à opção de certificado, mas em vez de usar a impressão digital do certificado, a chave do certificado RSA é usada em vez disso.|Uma verificação de RSA permite restringir especificamente a autenticação para um único certificado com base em sua chave RSA. Isso habilita a autenticação mais rígida de uma chave RSA específica às custas de serviço, que não funciona mais com os clientes existentes se altera o valor da chave RSA.|  
|Nome de usuário principal (UPN). O padrão quando o `ClientCredentialType` é definido para o Windows e o serviço de processo não está em execução em uma das contas do sistema.|Esse elemento Especifica o UPN que o serviço está sendo executado. Consulte a seção identidade e o protocolo Kerberos [substituindo a identidade de um serviço de autenticação](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md).|Isso garante que o serviço está em execução em uma conta de usuário específica do Windows. A conta de usuário pode ser o usuário de logon atual ou o serviço em execução em uma conta de usuário específico.<br /><br /> Essa configuração se beneficia da segurança do Kerberos Windows se o serviço está em execução em uma conta de domínio em um ambiente do Active Directory.|  
|Nome principal do serviço (SPN). O padrão quando o `ClientCredentialType` é definido para o Windows e o serviço de processo está em execução em uma das contas do sistema — NetworkService, LocalSystem ou LocalService.|Esse elemento Especifica o SPN associado à conta do serviço. Consulte a seção identidade e o protocolo Kerberos [substituindo a identidade de um serviço de autenticação](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md).|Isso garante que o SPN e a conta específica do Windows associada ao SPN identificam o serviço.<br /><br /> Você pode usar a ferramenta Setspn.exe para associar uma conta de computador para a conta de usuário do serviço.<br /><br /> Essa configuração se beneficia do Kerberos Windows segurança se o serviço está em execução em uma das contas do sistema ou em uma conta de domínio que tenha um nome SPN associado com ele e o computador é um membro de um domínio em um ambiente do Active Directory.|  
  
## <a name="specifying-identity-at-the-service"></a>Especificando a identidade do serviço do  
 Normalmente, você não precisa definir a identidade em um serviço, pois a seleção de um tipo de credencial de cliente determina o tipo de identidade exposto nos metadados de serviço. Para obter mais informações sobre como substituir ou especificar a identidade de serviço, consulte [substituindo a identidade de um serviço de autenticação](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md).  
  
## <a name="using-the-identity-element-in-configuration"></a>Usando o \<identidade > elemento na configuração  
 Se você alterar o tipo de credencial de cliente na associação mostrado anteriormente para `Certificate,` WSDL gerado contém uma Base64 serializada certificado x. 509 para o valor de identidade, conforme mostrado no código a seguir. Esse é o padrão para todos os tipos de credencial de cliente que não sejam Windows.  

 Você pode alterar o valor de identidade do serviço padrão ou alterar o tipo de identidade usando o `<identity>` elemento na configuração ou definindo a identidade no código. O código de configuração a seguir define uma identidade do DNS (sistema) do nome de domínio com o valor `contoso.com`.  

## <a name="setting-identity-programmatically"></a>Definindo a identidade do forma programática  
 Seu serviço não precisa especificar explicitamente uma identidade, porque o WCF determina automaticamente. No entanto, o WCF permite que você especifique uma identidade de um ponto de extremidade, se necessário. O código a seguir adiciona um novo ponto de extremidade de serviço com uma identidade específica do DNS.  
  
 [!code-csharp[C_Identity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_identity/cs/source.cs#5)]
 [!code-vb[C_Identity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_identity/vb/source.vb#5)]  
  
## <a name="specifying-identity-at-the-client"></a>Especificação de identidade no cliente  
 Em tempo de design, um desenvolvedor cliente normalmente usa o [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para gerar a configuração do cliente. O arquivo de configuração gerada (deve ser usada pelo cliente) contém a identidade do servidor. Por exemplo, o código a seguir é gerado de um serviço que especifica uma identidade do DNS, conforme mostrado no exemplo anterior. Observe que o valor de identidade do ponto de extremidade do cliente corresponde ao que o serviço. Nesse caso, quando o cliente recebe as credenciais do Windows (Kerberos) para o serviço, ele espera que o valor a ser `contoso.com`.  

 Se, em vez do Windows, o serviço Especifica um certificado como o tipo de credencial de cliente, propriedade de DNS do certificado deve ser o valor `contoso.com`. (Ou se a propriedade de DNS estiver `null`, nome do assunto do certificado deve ser `contoso.com`.)  
  
#### <a name="using-a-specific-value-for-identity"></a>Usando um valor específico para a identidade  
 O seguinte arquivo de configuração de cliente mostra como a identidade do serviço deve ser um valor específico. No exemplo a seguir, o cliente pode se comunicar com dois pontos de extremidade. A primeira é identificada com uma impressão digital do certificado e o segundo com uma chave RSA do certificado. Ou seja, um certificado que contém apenas um público chave chaves par de chaves, mas não é emitido por uma autoridade confiável.  

## <a name="identity-checking-at-run-time"></a>A verificação em tempo de execução de identidade  
 Em tempo de design, um desenvolvedor cliente determina a identidade do servidor por meio de seus metadados. Em tempo de execução, a verificação de identidade é executada antes de chamar qualquer ponto de extremidade de serviço.  
  
 O valor de identidade é vinculado ao tipo de autenticação especificado por metadados; em outras palavras, o tipo de credenciais usadas para o serviço.  
  
 Se o canal está configurado para se autenticar usando o nível de transporte ou de mensagem de protocolo (SSL) com certificados X.509 para autenticação, os seguintes valores de identidade são válidos:  
  
- DNS. WCF garante que o certificado fornecido durante o handshake SSL contém um DNS ou `CommonName` atributo de (CN) igual ao valor especificado na identidade do DNS no cliente. Observe que essas verificações são feitas Além disso, para determinar a validade do certificado do servidor. Por padrão, o WCF valida se o certificado do servidor é emitido por uma autoridade raiz confiável.  
  
- Certificado. Durante o handshake SSL, o WCF assegura que o ponto de extremidade remoto fornece o valor de certificado exato especificado na identidade.  
  
- Referência de certificado. Mesmo que o certificado.  
  
- RSA. Durante o handshake SSL, o WCF assegura que o ponto de extremidade remoto fornece a chave RSA exata especificada na identidade.  
  
 Se o serviço é autenticado usando o SSL no nível de transporte ou de mensagem com uma credencial do Windows para autenticação e negocia a credencial, os seguintes valores de identidade são válidos:  
  
- DNS. A negociação passa o SPN do serviço para que o nome DNS pode ser verificado. O SPN está no formato `host/<dns name>`.  
  
- SPN. Um serviço explícito SPN for retornado, por exemplo, `host/myservice`.  
  
- UPN. O UPN da conta de serviço. O UPN está no formato `username` @ `domain`. Por exemplo, quando o serviço está em execução em uma conta de usuário, ele pode ser `username@contoso.com`.  
  
 Especificando a identidade por meio de programação (usando o <xref:System.ServiceModel.EndpointAddress.Identity%2A> propriedade) é opcional. Se nenhuma identidade for especificada, e o tipo de credencial de cliente é o Windows, o padrão é o SPN com o valor definido para a parte do nome do host do endereço do ponto de extremidade de serviço prefixada com o "host /" literal. Se nenhuma identidade for especificada, e o tipo de credencial de cliente é um certificado, o padrão é `Certificate`. Isso se aplica a ambos os segurança em nível de mensagem e transporte.  
  
## <a name="identity-and-custom-bindings"></a>Identidade e associações personalizadas  
 Como a identidade de um serviço depende do tipo de associação usado, certifique-se de que uma identidade apropriada é exposta ao criar uma associação personalizada. Por exemplo, no exemplo de código a seguir, a identidade exposta não é compatível com o tipo de segurança, porque a identidade para a associação de inicialização de conversa segura não é compatível com a identidade para a associação no ponto de extremidade. A associação de conversa segura define a identidade do DNS, enquanto o <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement> define a identidade SPN ou UPN.  
  
 [!code-csharp[C_Identity#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_identity/cs/source.cs#8)]
 [!code-vb[C_Identity#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_identity/vb/source.vb#8)]  
  
 Para obter mais informações sobre a associação de pilha elementos corretamente para uma associação personalizada, consulte [Criando associações](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md). Para obter mais informações sobre como criar uma associação personalizada com o <xref:System.ServiceModel.Channels.SecurityBindingElement>, consulte [como: Criar um SecurityBindingElement para um modo de autenticação especificado](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md).  
  
## <a name="see-also"></a>Consulte também

- [Como: Criar uma associação personalizada utilizando o SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Como: Criar um SecurityBindingElement para um modo de autenticação especificado](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
- [Como: Criar um verificador de identidade do cliente personalizado](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md)
- [Selecionando um tipo de credencial](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)
- [Trabalhando com certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Criando associações definidas pelo usuário](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)
- [Como: Recuperar a impressão digital de um certificado](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
