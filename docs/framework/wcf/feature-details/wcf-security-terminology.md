---
title: "Terminologia de segurança do WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [WCF], terminology
- security glossary [WCF]
- security terms [WCF]
ms.assetid: 68dde024-8e51-40ba-804f-ec52d85e9ca9
caps.latest.revision: 
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 352615238d95cf02788cf88ef412a11ffd2faf37
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2018
---
# <a name="wcf-security-terminology"></a>Terminologia de segurança do WCF
Parte da terminologia usada ao abordar a segurança podem não ser conhecidas. Este tópico fornece curtas explicações sobre alguns dos termos de segurança, mas não se destina a fornecer a documentação abrangente para cada item.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] termos usados no [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] documentação, consulte [fundamentais conceitos do Windows Communication Foundation](../../../../docs/framework/wcf/fundamental-concepts.md).  
  
 lista de controle de acesso (ACL)  
 Uma lista de proteções de segurança que se aplica a um objeto. (Um objeto pode ser um arquivo, processo, eventos ou qualquer outro com um descritor de segurança). Uma entrada em uma ACL é uma entrada de controle de acesso (ACE). Há dois tipos de ACLs: condicional e do sistema.  
  
 autenticação  
 O processo de verificar se um usuário, computador, serviço ou processo é quem ou o que ela diz ser.  
  
 autorização  
 O ato de controle de acesso e direitos a um recurso. Por exemplo, permitir que os membros de um grupo ler um arquivo, mas permitir que somente os membros de outro grupo para alterar o arquivo.  
  
 certificado de autoridade de certificação  
 Identifica a autoridade de certificação que emite certificados de autenticação de cliente e servidor para os servidores e clientes que solicitam esses certificados. Porque ele contém uma chave pública usada em assinaturas digitais, ele também é chamado como uma *certificado de assinatura*. Se a autoridade de certificação é uma autoridade raiz, o certificado de autoridade de certificação pode ser chamado como uma *certificado raiz*. Às vezes também é conhecido como um *certificado de site*.  
  
 Hierarquia de CA  
 Uma hierarquia de autoridade de certificação contém várias autoridades de certificação. Ele é organizado de forma que cada autoridade de certificação é certificada por outra autoridade de certificação em um nível mais alto da hierarquia até a parte superior da hierarquia, também conhecido como o *autoridade raiz*, for atingido.  
  
 certificado  
 Uma instrução assinada digitalmente que contém informações sobre uma entidade e a chave da entidade pública, assim, esses dois tipos de informações de associação juntos. Um certificado é emitido por uma autoridade confiável de organização (ou entidade), chamado uma certificação, depois que a autoridade verificou se a entidade é quem diz ser.  
  
 Certificados podem conter diferentes tipos de dados. Por exemplo, um certificado x. 509 inclui o formato do certificado, o número de série do certificado, o algoritmo usado para assinar o certificado, o nome da autoridade de certificação que emitiu o certificado, o nome e a chave pública da entidade que está solicitando o certificado e a assinatura da autoridade de certificação.  
  
 repositório de certificados  
 Normalmente, um armazenamento permanente onde certificados, listas de certificados revogados (CRLs) e listas de certificados confiáveis (CTLs) são armazenados. No entanto, é possível, para criar e abrir um repositório de certificados apenas na memória ao trabalhar com certificados que não precisam ser colocados em armazenamento permanente.  
  
 declarações  
 Informações transmitidas de uma entidade para outra usado para estabelecer a identidade do remetente. Por exemplo, um nome de usuário e token de senha ou um certificado x. 509.  
  
 Certificado de cliente  
 Refere-se a um certificado usado para autenticação de cliente, como autenticação de um navegador da Web em um servidor Web. Quando um cliente de navegador da Web tenta acessar um servidor Web seguro, o cliente envia o certificado para o servidor para permitir que ele verifique se a identidade do cliente.  
  
 credenciais  
 Dados de logon que usa uma entidade de segurança para estabelecer sua própria identidade, como uma senha ou um tíquete do protocolo Kerberos foram autenticados anteriormente. As credenciais são usadas para controlar o acesso aos recursos.  
  
 dados resumidos  
 Um tipo de conteúdo de dados definido pelo criptografia padrão da chave pública (PKCS) #7 que consiste em qualquer tipo de dados mais um hash de mensagem (digest) do conteúdo.  
  
 assinatura digital  
 Dados que associa a identidade do remetente para as informações que estão sendo enviadas. Uma assinatura digital pode ser agrupada com qualquer mensagem, arquivo ou outra informação codificada digitalmente ou transmitida em separado. Assinaturas digitais são usadas em ambientes de chave pública e fornecem serviços de autenticação e integridade.  
  
 encoding  
 O processo de transformar dados em um fluxo de bits. A codificação é parte do processo de serialização que converte dados em um fluxo de uns e os zeros.  
  
 par de chaves do Exchange  
 Um par de chaves de pública/privada usado para criptografar as chaves de sessão para que eles podem ser com segurança armazenados e trocados com outros usuários.  
  
 hash  
 Um valor numérico de tamanho fixo obtido pela aplicação de uma função matemática (consulte algoritmo de hash) a uma quantidade de dados arbitrária. Os dados geralmente incluem dados aleatórios, conhecidos como um *nonce*. O serviço e o cliente contribuem momentos do exchange para aumentar a complexidade do resultado. O resultado é também conhecido como um *Resumo da mensagem*. Enviar um valor de hash é mais seguro do que o envio de dados confidenciais, como uma senha, mesmo que a senha é criptografada. O remetente de hash e o destinatário devem concordar com o algoritmo de hash e os valores de uso único para que, uma vez recebida, um hash pode ser verificado.  
  
 algoritmo de hash  
 Um algoritmo usado para produzir um valor de hash de alguns dados, como uma chave de sessão ou mensagem. Algoritmos de hash típicos incluem o MD2, MD4, MD5 e SHA-1.  
  
 Protocolo Kerberos  
 Um protocolo que define como os clientes interagem com um serviço de autenticação de rede. Os clientes obtêm tíquetes do Kerberos chave Distribution Center (KDC), e eles apresentam esses tíquetes para servidores quando as conexões são estabelecidas. Os tíquetes Kerberos representam as credenciais de rede do cliente.  
  
 autoridade de segurança local (LSA)  
 Um subsistema protegido que autentica e logs de usuários no sistema local. LSA também mantém informações sobre todos os aspectos de segurança local em um sistema, coletivamente conhecido como a política de segurança local do sistema.  
  
 Negotiate  
 Um segurança suporte SSP (provedor) que atua como uma camada de aplicativo entre a Interface do provedor de suporte de segurança (SSPI) e outros SSPs. Quando um aplicativo chama SSPI para efetuar logon em uma rede, ele pode especificar um SSP para processar a solicitação. Se o aplicativo especificar `Negotiate`, `Negotiate` analisa a solicitação e escolhe o melhor SSP para manipular a solicitação com base na política de segurança configurado pelo cliente.  
  
 Valor de uso único  
 Um valor gerado aleatoriamente usado para anular a ataques "Repetir".  
  
 nonrepudiation  
 A capacidade de identificar os usuários que executaram determinadas ações, portanto irrefutably responder a qualquer tentativa de negar a responsabilidade por um usuário. Por exemplo, um sistema pode registrar a ID de um usuário sempre que um arquivo é excluído.  
  
 Padrão de criptografia de chave pública (PKCS)  
 Especificações produzidas pelo RSA Data Security, Inc. em cooperação com os desenvolvedores dos sistemas de segurança em todo o mundo para acelerar a implantação de criptografia de chave pública.  
  
 PKCS #7  
 O padrão de sintaxe de mensagem criptografada. Uma sintaxe geral para a qual a criptografia pode ser aplicada, como assinaturas digitais e criptografia de dados. Ele também fornece uma sintaxe para disseminar certificados ou listas de revogação de certificados e outros atributos da mensagem, como os carimbos de hora para a mensagem.  
  
 plaintext  
 Uma mensagem que não está criptografada. Mensagens de texto sem formatação às vezes são chamadas de *texto não criptografado* mensagens.  
  
 privilégio  
 O direito de um usuário a executar várias operações relacionadas ao sistema, como o desligamento do sistema, carregar drivers de dispositivo ou alterar a hora do sistema. O token de acesso do usuário contém uma lista dos privilégios do que o usuário ou o usuário os grupos de espera.  
  
 Chave privada  
 A metade secreta de um par de chaves usado em um algoritmo de chave pública. As chaves privadas são normalmente usadas para criptografar uma chave de sessão simétrica, assinar digitalmente uma mensagem ou descriptografar uma mensagem que foram criptografada com a chave pública correspondente. Consulte também "chave pública".  
  
 process  
 O contexto de segurança sob a qual um aplicativo é executado. Normalmente, o contexto de segurança está associado um usuário, para que todos os aplicativos em execução em um determinado processo assumir as permissões e os privilégios do usuário proprietário.  
  
 par de chaves pública/privada  
 Um conjunto de chaves de criptografia usadas para criptografia de chave pública. Para cada usuário, um provedor de serviços de criptografia (CSP) geralmente mantém dois pares de chaves pública/privada: um par de chaves do exchange e um par de chaves de assinatura digital. Ambos os pares de chaves são mantidas da sessão para a sessão.  
  
 chave pública  
 Uma chave criptográfica usada normalmente ao descriptografar uma chave de sessão ou uma assinatura digital. A chave pública também pode ser usada para criptografar uma mensagem, garantindo que somente a pessoa com a chave privada correspondente pode descriptografar a mensagem.  
  
 criptografia de chave pública  
 Criptografia que usa um par de chaves, uma chave para criptografar os dados e a outra chave para descriptografar dados. Em contraste, os algoritmos de criptografia simétrica que usam a mesma chave para criptografia e descriptografia. Na prática, criptografia de chave pública é normalmente usada para proteger a chave de sessão que usa um algoritmo de criptografia simétrica. Nesse caso, a chave pública é usada para criptografar a chave de sessão, que por sua vez foi usado para criptografar alguns dados e a chave privada é usada para descriptografia. Além de proteger as chaves de sessão, criptografia de chave pública pode ser usada para assinar uma mensagem (usando a chave privada) digitalmente e validar a assinatura (usando a chave pública).  
  
 Infraestrutura de chave pública (PKI)  
 Uma infraestrutura fornecendo um conjunto integrado de serviços e ferramentas administrativas para criar, implantar e gerenciar aplicativos de chave pública.  
  
 recusa  
 A capacidade de negar falsamente ter executado uma ação, enquanto outras partes de um usuário não puder provar, caso contrário. Por exemplo, um usuário que exclui um arquivo e quem pode negar com êxito tendo feito isso.  
  
 autoridade raiz  
 A autoridade de certificação na parte superior de uma hierarquia de autoridade de certificação. A autoridade raiz certifica CAs no próximo nível da hierarquia.  
  
 Algoritmo de Hash seguro (SHA)  
 Um algoritmo de hash que gera um resumo da mensagem. SHA é usado com algoritmo o Digital assinatura (DSA) ou na Assinatura Digital padrão (DSS), entre outros lugares. Existem quatro variedades de SHA: SHA-1, SHA-256, SHA-384 e SHA-512. SHA-1 gera um resumo da mensagem de 160 bits. SHA-256, SHA-384 e SHA-512 geram 256 bits, 384 bits e resumos de mensagem de 512 bits, respectivamente. SHA foi desenvolvido pelo Instituto Nacional de padrões e tecnologia (NIST) e por agência de segurança nacional (NSA).  
  
 Secure Sockets Layer (SSL)  
 Um protocolo para comunicações de rede segura usando uma combinação de tecnologia de chave pública e o segredo.  
  
 contexto de segurança  
 Os atributos de segurança ou as regras que estão em vigor no momento. Por exemplo, o usuário atual conectado ao computador ou o número de identificação pessoal inserida pelo usuário do cartão inteligente. Para que o SSPI, um contexto de segurança é uma estrutura de dados opaco que contém dados de segurança relevantes para uma conexão, como uma chave de sessão ou uma indicação de que a duração da sessão.  
  
 entidade de segurança  
 Uma entidade reconhecida pelo sistema de segurança. Entidades de segurança podem incluir usuários humanos, bem como processos autônomos.  
  
 provedor de suporte de segurança (SSP)  
 Uma biblioteca de vínculo dinâmico (DLL) que implementa o SSPI ao disponibilizar um ou mais pacotes de segurança para aplicativos. Cada pacote de segurança fornece mapeamentos entre as chamadas de função SSPI de um aplicativo e funções de um modelo de segurança. Pacotes de segurança oferecem suporte para protocolos de segurança como a autenticação Kerberos e a Microsoft LAN Manager (LanMan).  
  
 Interface de provedor de suporte de segurança (SSPI)  
 Uma interface comum entre os aplicativos de nível de transporte, como a chamada de procedimento remoto (RPC) do Microsoft e provedores de segurança, como o Windows distributed security. A SSPI permite que um aplicativo de transporte para chamar um dos vários provedores de segurança para obter uma conexão autenticada. Essas chamadas não exigem extenso conhecimento de detalhes do protocolo de segurança.  
  
 serviço de token de segurança  
 Serviços projetados para emitir e gerenciar tokens de segurança personalizada (tokens emitidos) em um cenário de multisserviço. Os tokens personalizados geralmente são tokens de segurança asserções Markup Language (SAML) que incluem uma credencial personalizada.  
  
 certificado do servidor  
 Refere-se a um certificado usado para autenticação de servidor, como autenticar um servidor Web para um navegador da Web. Quando um cliente de navegador da Web tenta acessar um servidor Web seguro, o servidor envia seu certificado para o navegador para permitir que ele verifique se a identidade do servidor.  
  
 Sessão  
 Uma troca de mensagens sob a proteção de uma única parte de material de chave. Por exemplo, as sessões SSL usam uma única chave para enviar várias mensagens e para trás sob essa chave.  
  
 chave de sessão  
 Uma chave gerada aleatoriamente que é usada uma vez e depois é descartada. As chaves de sessão são simétricas (usado para criptografia e descriptografia). Elas são enviadas com a mensagem, protegida pela criptografia com uma chave pública do destinatário pretendido. Uma chave de sessão consiste em um número aleatório de cerca de 40 a 2.000 bits.  
  
 credenciais complementares  
 Credenciais para uso na autenticação de uma entidade de segurança para os domínios de segurança externas.  
  
 criptografia simétrica  
 Criptografia que usa uma única chave de criptografia e descriptografia. A criptografia simétrica é preferencial para criptografar grandes quantidades de dados. Alguns dos algoritmos de criptografia simétrica mais comuns são RC2, RC4 e padrão de criptografia de dados (DES).  
  
 Consulte também "criptografia de chave pública."  
  
 Chave simétrica  
 Uma única chave usada para criptografia e descriptografia. As chaves de sessão são geralmente simétricas.  
  
 token (token de acesso)  
 Um token de acesso contém as informações de segurança para uma sessão de logon. O sistema cria um token de acesso quando um usuário faz logon, e cada processo executado em nome do usuário tem uma cópia do token. O token identifica o usuário, grupos de usuários e os privilégios do usuário. O sistema usa o token para controlar o acesso a objetos protegíveis e controlar a capacidade de executar várias operações relacionadas ao sistema no computador local do usuário. Há dois tipos de tokens de acesso primários e representação.  
  
 Camada de transporte  
 A camada de rede que é responsável por ambos os qualidade de serviço e entrega precisa de informações. Entre as tarefas executadas nesta camada estão correção e detecção de erro.  
  
 lista de confiança (lista de certificados confiáveis ou lista de certificados confiáveis)  
 Uma lista predefinida de itens que foram assinados por uma entidade confiável. Uma CTL pode ser qualquer coisa, como uma lista de hashes de certificados ou uma lista de nomes de arquivo. Todos os itens na lista são autenticados (aprovado) pela entidade de assinatura.  
  
 provedor de confiança  
 O software que decide se um determinado arquivo é confiável. Essa decisão se baseia no certificado associado ao arquivo.  
  
 Nome de usuário principal (UPN)  
 Um nome de conta de usuário (também conhecido como o *nome de logon do usuário*) e um nome de domínio identificando o domínio no qual a conta de usuário está localizada. Este é o uso padrão para fazer logon em um domínio do Windows. O formato é: someone@example.com (como um endereço de email).  
  
> [!NOTE]
>  Além de formulário padrão do UPN, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aceita UPNs no formulário de nível inferior, por exemplo, cohowinery.com\someone.  
  
 X.509  
 Um padrão reconhecido internacionalmente para certificados que define suas partes necessárias.  
  
## <a name="see-also"></a>Consulte também  
 [Conceitos fundamentais do Windows Communication Foundation](../../../../docs/framework/wcf/fundamental-concepts.md)  
 [Conceitos de segurança](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
 [Modelo de segurança para o Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
