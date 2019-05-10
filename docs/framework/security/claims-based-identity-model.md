---
title: Modelo de identidade baseada em declarações
ms.date: 03/30/2017
ms.assetid: 4a96a9af-d980-43be-bf91-341a23401431
author: BrucePerlerMS
ms.openlocfilehash: 8560c7fd1969cfed6e43e2982fb69313c45c9405
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650455"
---
# <a name="claims-based-identity-model"></a>Modelo de identidade baseada em declarações
Quando você cria aplicativos com reconhecimento de declarações, a identidade do usuário é representada em seu aplicativo como um conjunto de declarações. Uma reivindicação pode ser o nome do usuário, outra pode ser um endereço de email. A ideia é que um sistema externo de identidade seja configurado para dar ao seu aplicativo tudo que ele precisa saber sobre o usuário com cada solicitação que ele faz, juntamente com a segurança criptográfica que os dados de identidade você recebe de uma fonte confiável.  
  
 Nesse modelo, o logon único é muito mais fácil de obter, e seu aplicativo não fica mais responsável pelo seguinte:  
  
- Autenticar os usuários.  
  
- Armazenar contas de usuário e senhas.  
  
- Chamar diretórios corporativos para pesquisar detalhes da identidade do usuário.  
  
- Integrar-se com sistemas de identidade de outras plataformas ou empresas.  
  
 Nesse modelo, o aplicativo toma decisões relacionadas à identidade com base nas declarações fornecidas pelo sistema que autenticou o usuário. Isso pode ser qualquer coisa, desde a personalização simples do aplicativo com o nome do usuário a autorizar o usuário a acessar recursos de maior valor em seu aplicativo.  
  
 Este tópico fornece as seguintes informações:  
  
- [Introdução à identidade baseada em declarações](../../../docs/framework/security/claims-based-identity-model.md#BKMK_1)  
  
- [Cenário básico para um modelo de identidade baseada em declarações](../../../docs/framework/security/claims-based-identity-model.md#BKMK_2)  
  
<a name="BKMK_1"></a>   
## <a name="introduction-to-claims-based-identity"></a>Introdução à identidade baseada em declarações  
 A terminologia e os conceitos a seguir podem ajudá-lo a entender essa nova arquitetura da identidade.  
  
### <a name="identity"></a>Identidade  
 Para descrever o modelo de programação no WIF (Windows Identity Foundation), usaremos o termo “identidade” para representar um conjunto de atributos que descreve um usuário ou outra entidade em um sistema que você deseja proteger.  
  
### <a name="claim"></a>Declaração  
 Pense na declaração como uma parte das informações de identidade, como nome, endereço de email, idade, associação na função de vendas. Quanto mais declarações seu aplicativo receber, mais você saberá sobre o usuário. Você pode estar se perguntando por que elas são chamadas de “declarações”, em vez de “atributos”, como é geralmente usado para descrever diretórios corporativos. A razão tem a ver com o método de envio. Nesse modelo, o aplicativo não procura atributos do usuário em um diretório. Em vez disso, o usuário envia as declarações ao aplicativo, e o aplicativo as examina. Cada declaração é feita por um emissor, e você confia na declaração tanto quanto confia no emissor. Por exemplo, você confia em uma declaração feita pelo controlador de domínio de sua empresa mais do que confia em uma declaração feita pelo próprio usuário. O WIF representa declarações com tipo <xref:System.Security.Claims.Claim>, que tem a propriedade <xref:System.Security.Claims.Claim.Issuer%2A> que permite que você descubra quem emitiu a declaração.  
  
### <a name="security-token"></a>Token de segurança  
 O usuário fornece um conjunto de declarações ao seu aplicativo juntamente com uma solicitação. Em um serviço Web, essas declarações são transportadas no cabeçalho de segurança do envelope SOAP. Em um aplicativo Web baseado em navegador, as declarações chegam por meio de um HTTP POST do navegador do usuário e depois podem ser armazenadas em cache, em um cookie, se uma sessão for desejada. Independentemente de como essas declarações chegam, elas devem ser serializadas, e é aí que os tokens de segurança entram. Um token de segurança é um conjunto serializado de declarações que é assinado digitalmente pela autoridade emissora. A assinatura é importante: oferece a garantia de que o usuário não reúna um monte de declarações e as envie para você. Em situações de baixa segurança em que a criptografia não é necessária ou desejada, você pode usar tokens não assinados, mas esse cenário não é descrito neste tópico.  
  
 Um dos principais recursos do WIF é a capacidade de criar e ler tokens de segurança. O WIF e o .NET Framework cuidam de todo o trabalho criptográfico e apresentam ao seu aplicativo um conjunto de declarações que você pode ler.  
  
### <a name="issuing-authority"></a>Autoridade emissora  
 Há vários tipos diferentes de autoridades emissoras, de controladores de domínio que emitem tíquetes Kerberos a autoridades de certificação que emitem certificados X.509, mas o tipo específico de autoridade abordado neste tópico emite tokens de segurança que contêm declarações. Essa autoridade emissora é um aplicativo ou serviço Web que sabe emitir tokens de segurança. Ele deve ter conhecimento suficiente para poder emitir as declarações apropriadas dada o parceiro de confiança de destino e o usuário autor da solicitação, e deve ser responsável por interagir com os repositórios de usuários para procurar declarações e autenticar os usuários.  
  
 Independentemente da autoridade emissora que você escolher, ela terá um papel fundamental em sua solução de identidade. Quando você fatora a autenticação fora de seu aplicativo confiando em declarações, você transfere a responsabilidade para essa autoridade e pede a ela para autenticar os usuários em seu nome.  
  
### <a name="security-token-service-sts"></a>STS (Serviço de Token de Segurança)  
 Um STS ( serviço de token de segurança) é o componente de serviço que cria, assinar e emite tokens de segurança de acordo com os protocolos WS-Trust e WS-Federation. A implementação desses protocolos envolve muito trabalho, mas o WIF faz todo esse trabalho para você, tornando viável para alguém que não é especialista nos protocolos para ativar um STS com o mínimo de esforço. Use um STS pré-criado, como os [Serviços de Federação do Active Directory® (AD FS) 2.0](https://go.microsoft.com/fwlink/?LinkID=247516), um STS de nuvem, como [ACS (Serviço de Controle de Acesso) do Microsoft Azure](https://go.microsoft.com/fwlink/?LinkID=247517) ou, se desejar emitir tokens personalizados ou fornecer autenticação ou autorização personalizada, crie seu próprio STS personalizado usando o WIF. O WIF facilita a criação de seu próprio STS.  
  
### <a name="relying-party-application"></a>Aplicativo de terceira parte confiável  
 Ao criar um aplicativo que confia em declarações, você está criando um aplicativo de terceira parte confiável (RP). Um sinônimo para RP é "aplicativo com reconhecimento de declaração" e “aplicativo baseado em declarações”. Os aplicativos e serviços Web podem ser RPs. Um aplicativo RP consome os tokens emitidos por um STS e extrai as declarações dos tokens para usá-las para tarefas relacionadas à identidade. O WIF oferece funcionalidades para ajudar você a criar aplicativos RP.  
  
### <a name="standards"></a>Padrões  
 Para tornar tudo isso interoperável, vários padrões WS-* são usados no cenário anterior. A política é recuperada usando WS-MetadataExchange, e a própria política é estruturada de acordo com a especificação de WS-Policy. O STS expõe os pontos de extremidade que implementam a especificação de WS-Trust, que descreve como solicitar e receber tokens de segurança. A maioria dos STSs de hoje emite tokens formatados com SAML. SAML é um vocabulário de XML reconhecido no setor que pode ser usado para representar declarações de maneira interoperável. Ou, em uma situação de várias plataformas, permite que você se comunique com um STS em uma plataforma completamente diferente e faça logon único em todos os seus aplicativos, independentemente da plataforma.  
  
### <a name="browser-based-applications"></a>Aplicativos baseados em navegador  
 Os clientes inteligentes não são os únicos que podem usar o modelo de identidade baseada em declarações. Os aplicativos baseados em navegador (também chamados de clientes passivos) podem usá-lo também. O cenário a seguir descreve como isso funciona.  
  
 Primeiro, o usuário aponta para um navegador em um aplicativo Web com reconhecimento de declarações (aplicativo da terceira parte confiável). O aplicativo Web redireciona o navegador para o STS para que o usuário possa ser autenticado. O STS está hospedado em um aplicativo Web simples que lê a solicitação recebida, autentica o usuário usando mecanismos HTTP padrão, cria um token SAML e responde com um código JavaScript que faz com que o navegador inicie um HTTP POST que envia o token SAML de volta para o RP. O corpo desse POST contém as declarações que o RP solicitou. Nesse momento, é comum que o RP empacote as declarações em um cookie para que o usuário não tenha de ser redirecionado para cada solicitação.  
  
<a name="BKMK_2"></a>   
## <a name="basic-scenario-for-a-claims-based-identity-model"></a>Cenário básico para um modelo de identidade baseada em declarações  
 Veja um exemplo de um sistema baseado em declarações a seguir.  
  
 ![Fluxo de autenticação de parceiro confiável](../../../docs/framework/security/media/conc-relying-partner-processc.png "conc_relying_partner_processc")  
  
 Esse diagrama mostra um site (aplicativo da terceira parte confiável, RP) que foi configurado para usar o WIF para autenticação, e um cliente ou um navegador da Web que deseja usar esse site.  
  
1. Quando um usuário não autenticado solicita uma página, seu navegador é redirecionado para as páginas de IdP (provedor) de identidade.  
  
2. O IdP exige que o usuário apresente suas credenciais, como nome de usuário/senha ou autenticação Kerberos.  
  
3. Os problemas de IdP um token que é retornado ao navegador.  
  
4. O navegador é redirecionado de volta à página solicitada originalmente, onde o WIF determina se o token atende aos requisitos para acessar a página. Em caso positivo, um cookie é emitido para estabelecer uma sessão para que a autenticação ocorra apenas uma vez, e o controle é passado para o aplicativo.
