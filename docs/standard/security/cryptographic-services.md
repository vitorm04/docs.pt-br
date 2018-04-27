---
title: Serviços criptográficos
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cryptography [.NET Framework]
- pattern of derived class inheritance
- digital signatures
- asymmetric cryptographic algorithms
- digital signatures, public-key systems
- public keys
- decryptioin [.NET Framework]
- private keys
- MAC algorithms
- cryptographic algorithms
- private keys, overview
- encryption [.NET Framework]
- security [.NET Framework], encryption
- cryptographic services
- symmetric cryptographic algorithms
- hash
- message authentication codes
- derived class inheritance
- cryptography [.NET Framework], about
- random number generation
ms.assetid: f96284bc-7b73-44b5-ac59-fac613ad09f8
caps.latest.revision: 34
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 02d399d85c53cd296fc5f49ca0ec4b51b14ad677
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="cryptographic-services"></a>Serviços criptográficos
<a name="top"></a> Redes públicas, como a Internet não fornecem um meio de comunicação segura entre entidades. Comunicação por essas redes é suscetível a sendo lidas ou modificadas até mesmo por terceiros não autorizados. A criptografia ajuda a proteger os dados sejam exibidos, fornece maneiras para detectar se os dados foram modificados e ajuda a fornecer uma maneira segura de comunicação nos canais de outra forma não seguras. Por exemplo, os dados podem ser criptografados usando um algoritmo de criptografia, transmitidos em um estado criptografado e mais tarde descriptografados pelo parceiro pretendido. Se outra pessoa interceptar os dados criptografados, será difícil decifrar.  
  
 No .NET Framework, as classes de <xref:System.Security.Cryptography?displayProperty=nameWithType> namespace gerenciar muitos detalhes de criptografia para você. Alguns são wrappers para a API de criptografia da Microsoft não gerenciado (CryptoAPI), enquanto outras são implementações totalmente gerenciadas. Você não precisa ser um especialista em criptografia para usar essas classes. Quando você cria uma nova instância de um a criptografia de classes do algoritmo, as chaves são geradas para facilidade de uso e propriedades padrão são tão seguros e protegidos possível.  
  
 Esta visão geral fornece um resumo dos métodos de criptografia e práticas recomendadas com suporte pelo .NET Framework, incluindo os manifestos ClickOnce, Suite B, e o suporte de geração CNG (Cryptography Next) introduzido no [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)].  
  
 Esta visão geral contém as seguintes seções:  
  
-   [Primitivos criptográficos](#primitives)  
  
-   [Criptografia de chave secreta](#secret_key)  
  
-   [Criptografia de chave pública](#public_key)  
  
-   [Assinaturas digitais](#digital_signatures)  
  
-   [Valores de hash](#hash_values)  
  
-   [Geração de números aleatórios](#random_numbers)  
  
-   [Manifestos ClickOnce](#clickonce)  
  
-   [Suporte ao conjunto B](#suite_b)  
  
-   [Tópicos relacionados](#related_topics)  
  
 Para obter informações adicionais sobre a criptografia e sobre os serviços da Microsoft, componentes e ferramentas que permitem a adição de segurança criptográfica para seus aplicativos, consulte o Win32 e COM, seção de segurança desta documentação.  
  
<a name="primitives"></a>   
## <a name="cryptographic-primitives"></a>Primitivos criptográficos  
 Em uma situação típica, em que a criptografia é usada, duas partes (Alice e Bob) se comunicam através de um canal não seguro. Alice e Bob deseja garantir que sua comunicação permaneça incompreensível por qualquer pessoa que pode estar escutando. Além disso, como Alice e Bob está em locais remotos, Alice deve ter certeza de que as informações que ele recebe de Bob não foi modificadas por qualquer pessoa durante a transmissão. Além disso, ela deve garantir que as informações realmente se originar de Bob e não de uma pessoa que está representando Bob.  
  
 A criptografia é usada para atingir as seguintes metas:  
  
-   Confidencialidade: Para ajudar a proteger dados ou a identidade de um usuário que está sendo lido.  
  
-   Integridade de dados: para ajudar a proteger os dados que está sendo alterada.  
  
-   Autenticação: Para garantir que os dados são originados de uma pessoa específica.  
  
-   Não-repúdio: Para impedir que uma pessoa específica negar que enviou uma mensagem.  
  
 Para atingir essas metas, você pode usar uma combinação de algoritmos e práticas recomendadas conhecidas como primitivos criptográficos para criar um esquema de criptografia. A tabela a seguir lista os primitivos criptográficos e seus usos.  
  
|Primitivos de criptografia|Use|  
|-----------------------------|---------|  
|Criptografia de chave secreta (a criptografia simétrica)|Executa uma transformação nos dados para evitar que ele está sendo lido por terceiros. Esse tipo de criptografia usa uma única compartilhada, a chave secreta para criptografar e descriptografar dados.|  
|Criptografia de chave pública (criptografia assimétrica)|Executa uma transformação nos dados para evitar que ele está sendo lido por terceiros. Esse tipo de criptografia usa um par de chaves pública/privada para criptografar e descriptografar dados.|  
|Assinatura de criptografia|Ajuda a verificar a origem dos dados de um terceiro específico criando uma assinatura digital que é exclusiva para essa parte. Esse processo também usa funções de hash.|  
|Hashes criptográficos|Mapeia dados de qualquer comprimento para uma sequência de bytes de comprimento fixo. Os hashes são estatisticamente exclusivos; uma sequência diferente de dois bytes não será hash para o mesmo valor.|  
  
 [Voltar ao início](#top)  
  
<a name="secret_key"></a>   
## <a name="secret-key-encryption"></a>Criptografia de chave secreta  
 Algoritmos de criptografia de chave secreta usam uma única chave secreta para criptografar e descriptografar dados. Você deve proteger a chave de acesso não autorizado agentes, porque todas as pessoas que tem a chave podem ser usada para descriptografar os dados ou criptografar seus próprios dados, alegando que ela seja proveniente de você.  
  
 Criptografia de chave secreta também é conhecida como criptografia simétrica porque a mesma chave é usada para criptografia e descriptografia. Algoritmos de criptografia de chave secreta são muito rápidos (em comparação com algoritmos de chave pública) e são adequados para executar transformações de criptografia em grandes fluxos de dados. Algoritmos de criptografia assimétrica como RSA são limitados matematicamente em quantos dados eles podem criptografar. Algoritmos de criptografia simétrica geralmente não têm esses problemas.  
  
 Um tipo de algoritmo de chave de segredo chamado uma codificação de bloco é usado para criptografar um bloco de dados por vez. Codificações em bloco, como criptografia de dados padrão (DES), TripleDES, e o padrão de criptografia avançada (AES) criptograficamente transformar um bloco de entrada de *n* bytes em um bloco de saída de bytes criptografados. Se você deseja criptografar ou descriptografar uma sequência de bytes, você precisa fazer isso bloco por bloco. Porque *n* é pequeno (8 bytes para DES e TripleDES; 32 bytes para AES, 24 bytes ou 16 bytes [padrão]), valores de dados que são maiores do que *n* precisa ser criptografado um bloco por vez. Valores de dados que são menores que *n* precisa ser expandido para *n* para ser processado.  
  
 Uma forma simple de codificação de bloco é chamada de modo eletrônica livro de códigos (ECB). Modo ECB não é considerado seguro, porque ele não usa um vetor de inicialização para inicializar o primeiro bloco de texto sem formatação. Para uma determinada chave secreta *k*, uma codificação de bloco simples que não usa um vetor de inicialização criptografará o mesmo bloco de entrada de texto sem formatação no mesmo bloco de saída de texto cifrado. Portanto, se você tiver blocos em seu fluxo de entrada de texto sem formatação, você terá de blocos no seu fluxo de texto cifrado de saída. Esses blocos de saída duplicado alertar os usuários não autorizados para a criptografia fraca usaram os algoritmos que já foram empregados e os modos possíveis de ataque. O modo de criptografia ECB, portanto, é bastante vulnerável a análise e, por fim, a descoberta de chave.  
  
 As classes de codificação de bloco que são fornecidas na biblioteca de classes base usam um padrão de encadeamento de modo de chamada de blocos de codificação encadeamento CBC (), embora você possa alterar esse padrão, se você quiser.  
  
 Codificações CBC superam os problemas associados com codificações ECB usando um vetor de inicialização (IV) para criptografar o primeiro bloco de texto sem formatação. Cada bloco subsequente de texto sem formatação passa por um OR exclusivo bit a bit (`XOR`) operação com o bloco de texto cifrado anterior antes de ele está criptografado. Cada bloco de texto cifrado, portanto, é dependente de todos os blocos anteriores. Quando este for cabeçalhos de mensagem usado, comuns que poderiam ser conhecidos para um usuário não autorizado não pode ser usado para a engenharia reversa de uma chave.  
  
 Uma maneira de comprometer os dados criptografados com uma codificação CBC é realizar uma pesquisa detalhada de cada chave possíveis. Dependendo do tamanho da chave que é usada para executar a criptografia, esse tipo de pesquisa é muito demorado usando até mesmo os computadores mais rápidos e, portanto, se for inviável. Tamanhos maiores de chave são mais difíceis de decifrar. Embora a criptografia não impossibilitar teoricamente um adversário recuperar os dados criptografados, ele gera o custo de fazer isso. Se demorar três meses para executar uma pesquisa detalhada para recuperar dados que seja significativos apenas para alguns dias, o método de pesquisa detalhada é muito prático.  
  
 A desvantagem da criptografia de chave secreta é que ele supõe que duas partes tem estabelecido em uma chave e IV e comunicadas seus valores. O IV não é considerado um segredo e pode ser transmitido em texto não criptografado com a mensagem. No entanto, a chave deve ser mantida em segredo de usuários não autorizados. Devido a esses problemas, a criptografia de chave secreta é frequentemente usada junto com criptografia de chave pública em particular se comuniquem os valores da chave e do IV.  
  
 Supondo que Alice e Bob é duas partes que desejam se comunicar através de um canal inseguro, eles podem usar criptografia de chave secreta da seguinte maneira: Alice e Bob concorda em usar um algoritmo específico (por exemplo, AES) com uma chave particular e o IV. Alice compõe uma mensagem e cria um fluxo de rede (talvez um nome pipe ou rede email) para enviar a mensagem. Em seguida, ela criptografa o texto usando a chave e IV e envia a mensagem criptografada e IV para Bob através da intranet. Bob recebe o texto criptografado e descriptografa-a usando o IV e acordados anteriormente a chave. Se a transmissão é interceptada, o interceptador não é possível recuperar a mensagem original, porque ele não sabe qual é a chave. Nesse cenário, apenas a chave deve permanecer segreda. Em um cenário do mundo real, Alice ou Bob gera uma chave de segredo e usa criptografia de chave pública (assimétrica) para transferir a chave secreta do (simétrica) para outra parte. Para obter mais informações sobre criptografia de chave pública, consulte a próxima seção.  
  
 O [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] fornece as seguintes classes que implementam algoritmos de criptografia de chave de segredo:  
  
-   <xref:System.Security.Cryptography.AesManaged> (introduzido no [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)]).  
  
-   <xref:System.Security.Cryptography.DESCryptoServiceProvider>.  
  
-   <xref:System.Security.Cryptography.HMACSHA1> (Isso é tecnicamente um algoritmo de chave de segredo porque ela representa o código de autenticação de mensagem que é calculado usando uma função de hash criptográfico combinada com uma chave secreta. Consulte [valores de Hash](#hash_values), mais adiante neste tópico.)  
  
-   <xref:System.Security.Cryptography.RC2CryptoServiceProvider>.  
  
-   <xref:System.Security.Cryptography.RijndaelManaged>.  
  
-   <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider>.  
  
 [Voltar ao início](#top)  
  
<a name="public_key"></a>   
## <a name="public-key-encryption"></a>Criptografia de chave pública  
 Criptografia de chave pública usa uma chave privada deve ser mantida em segredo de usuários não autorizados e uma chave pública que pode se tornar pública para qualquer pessoa. A chave pública e a chave privada matematicamente são vinculadas. dados criptografados com a chave pública podem ser descriptografados apenas com a chave privada e os dados que estão assinados com a chave privada podem ser verificados apenas com a chave pública. A chave pública pode ser disponibilizada para qualquer pessoa; ele é usado para criptografar os dados sejam enviados para o guardião da chave privada. Algoritmos de criptografia de chave pública também são conhecidos como algoritmos assimétricos porque uma chave é necessária para criptografar dados e outra chave é necessária para descriptografar dados. Uma regra básica de criptografia impede a reutilização da chave, e as duas chaves devem ser exclusivas para cada sessão de comunicação. No entanto, na prática, chaves assimétricas são geralmente vida longa.  
  
 Duas partes (Alice e Bob) podem usar criptografia de chave pública da seguinte maneira: primeiro, Alice gera um par de chaves pública/privada. Se Bob deseja enviar uma mensagem criptografada de Alice, ele solicita a sua chave pública. Alice envia Bob sua chave pública em uma rede não segura e Bob usa essa chave para criptografar uma mensagem. Bob envia a mensagem criptografada para Alice, e ela descriptografa usando sua chave privada. Se Bob recebido chave de Alice por um canal inseguro, como uma rede pública, Bob está aberto para um ataque man-in-the-middle. Portanto, Bob deve verificar com Alice que ele tenha uma cópia correta da sua chave pública.  
  
 Durante a transmissão de chave pública de Alice, um agente não autorizado pode interceptar a chave. Além disso, o mesmo agente pode interceptar a mensagem criptografada de Bob. No entanto, o agente não pode descriptografar a mensagem com a chave pública. A mensagem pode ser descriptografada somente com a chave privada de Alice, que não foi transmitida. Alice não usa sua chave privada para criptografar uma mensagem de resposta para Bob, porque qualquer pessoa com a chave pública pode descriptografar a mensagem. Se Alice deseja enviar uma mensagem de volta para Bob, ela solicita Bob sua chave pública e criptografa a mensagem usando a chave pública. Bob descriptografa a mensagem usando sua chave privada associada.  
  
 Nesse cenário, Alice e Bob usa criptografia de chave pública (assimétrica) para transferir uma chave de segredo (simétrica) e usar a criptografia de chave secreta para o restante da sua sessão.  
  
 A lista a seguir oferece comparações entre os algoritmos de criptografia de chave pública e a chave secreta:  
  
-   Algoritmos de criptografia de chave pública usam um tamanho de buffer fixo, enquanto que os algoritmos de criptografia de chave secreta usam um buffer de comprimento variável.  
  
-   Algoritmos de chave pública não podem ser usado para dados de cadeia juntos em fluxos a maneira como os algoritmos de chave secreta podem, porque apenas pequenas quantidades de dados podem ser criptografadas. Portanto, operações assimétricas não usam o mesmo modelo de streaming como operações simétricas.  
  
-   Criptografia de chave pública tem um keyspace muito maior (intervalo de valores possíveis para a chave) que a criptografia de chave secreta. Portanto, a criptografia de chave pública é menos suscetível a ataques completa que tente cada chave possíveis.  
  
-   Chaves públicas são fáceis de distribuir porque eles não precisam ser protegida, desde que existe alguma maneira para verificar a identidade do remetente.  
  
-   Alguns algoritmos de chave pública (como RSA e DSA, mas não Diffie-Hellman) podem ser usados para criar assinaturas digitais para verificar a identidade do remetente de dados.  
  
-   Algoritmos de chave pública são muito lentos em comparação com algoritmos de chave de segredo e não são projetados para criptografar grandes quantidades de dados. Algoritmos de chave pública são úteis somente para transferir muito pequenas quantidades de dados. Normalmente, criptografia de chave pública é usada para criptografar uma chave e IV a ser usado por um algoritmo de chave secreta. Depois que a chave e IV são transferidas, criptografia de chave secreta é usada para o restante da sessão.  
  
 O [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] fornece as seguintes classes que implementam algoritmos de criptografia de chave pública:  
  
-   <xref:System.Security.Cryptography.DSACryptoServiceProvider>  
  
-   <xref:System.Security.Cryptography.RSACryptoServiceProvider>  
  
-   <xref:System.Security.Cryptography.ECDiffieHellman> (classe base)  
  
-   <xref:System.Security.Cryptography.ECDiffieHellmanCng>  
  
-   <xref:System.Security.Cryptography.ECDiffieHellmanCngPublicKey> (classe base)  
  
-   <xref:System.Security.Cryptography.ECDiffieHellmanKeyDerivationFunction> (classe base)  
  
-   <xref:System.Security.Cryptography.ECDsaCng>  
  
 RSA permite criptografia e assinatura, mas DSA pode ser usado apenas para assinar e Diffie-Hellman pode ser usado apenas para a geração de chave. Em geral, os algoritmos de chave pública são mais limitados em seus usos que algoritmos de chave privada.  
  
 [Voltar ao início](#top)  
  
<a name="digital_signatures"></a>   
## <a name="digital-signatures"></a>Assinaturas digitais  
 Algoritmos de chave pública também podem ser usados para formar assinaturas digitais. Assinaturas digitais para autenticar a identidade de um remetente (se você confiar a chave pública do remetente) e ajudar a proteger a integridade dos dados. Usando uma chave pública gerada pelo Alice, o destinatário de dados de Alice pode verificar que Alice enviados, comparando a assinatura digital para dados de Alice e uma chave pública de Alice.  
  
 Para usar a criptografia de chave pública para assinar digitalmente uma mensagem, Alice primeiro aplica um algoritmo de hash para a mensagem para criar um resumo da mensagem. Resumo da mensagem é uma representação compacta e exclusiva dos dados. Alice, em seguida, criptografa o resumo de mensagem com sua chave privada para criar sua assinatura pessoal. Ao receber a mensagem e a assinatura, Bob descriptografa a assinatura usando a chave pública de Alice para recuperar o conteúdo da mensagem e hashes a mensagem usando o mesmo algoritmo de hash usada Alice. Se o resumo de mensagem que Bob calcula exatamente corresponder o resumo de mensagem recebido de Alice, Bob terá certeza de que a mensagem veio o detentor da chave privada e que os dados não foi modificados. Se Bob confia Alice é o detentor da chave privada, ele saberá que a mensagem veio Alice.  
  
> [!NOTE]
>  Uma assinatura pode ser verificada por qualquer pessoa, porque a chave pública do remetente é conhecimento comum e geralmente é incluído no formato de assinatura digital. Esse método não manter a confidencialidade da mensagem; para a mensagem a ser secreta, ele também deve ser criptografado.  
  
 O [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] fornece as seguintes classes que implementam algoritmos de assinatura digital:  
  
-   <xref:System.Security.Cryptography.DSACryptoServiceProvider>  
  
-   <xref:System.Security.Cryptography.RSACryptoServiceProvider>  
  
-   <xref:System.Security.Cryptography.ECDsa> (classe base)  
  
-   <xref:System.Security.Cryptography.ECDsaCng>  
  
 [Voltar ao início](#top)  
  
<a name="hash_values"></a>   
## <a name="hash-values"></a>Valores de hash  
 Algoritmos de hash mapeiam valores binários de um comprimento arbitrário para menores valores binários de comprimento fixo, conhecido como valores de hash. Um valor de hash é uma representação numérica de um item de dados. Se o hash de um parágrafo de texto sem formatação e alterar uma letra do parágrafo, um hash subsequente produzirá um valor diferente. Se o hash é forte criptograficamente, seu valor seja alterada significativamente. Por exemplo, se um único bit de uma mensagem for alterado, uma função de hash forte pode produzir uma saída diferente de 50 por cento. Muitos valores de entrada podem hash para o mesmo valor de saída. No entanto, é impraticável para encontrar duas entradas distintas que usam o hash para o mesmo valor.  
  
 Duas partes (Alice e Bob) podem usar uma função de hash para garantir a integridade da mensagem. Eles selecione um algoritmo de hash para assinar as mensagens. Alice gravar uma mensagem e, em seguida, criar um hash da mensagem usando o algoritmo selecionado. Eles, em seguida, siga um dos seguintes métodos:  
  
-   Alice envia a mensagem de texto sem formatação e a mensagem de hash (assinatura digital) para Bob. Bob recebe e hashes de mensagem e compara o valor de hash para o valor de hash que recebeu de Alice. Se os valores de hash forem idênticos, a mensagem não foi alterada. Se os valores não forem idênticos, a mensagem foi alterada depois de Alice escreveu.  
  
     Infelizmente, esse método não estabelecer a autenticidade do remetente. Qualquer pessoa pode representar Alice e enviar uma mensagem para Bob. Eles podem usar o mesmo algoritmo de hash para assinar sua mensagem, e tudo Bob pode determinar é que a mensagem corresponde a sua assinatura. Isso é uma forma de um ataque man-in-the-middle. Consulte [NIB: exemplo de comunicação seguro geração CNG (Cryptography Next)](https://msdn.microsoft.com/library/8048e94e-054a-417b-87c6-4f5e26710e6e) para obter mais informações.  
  
-   Alice envia a mensagem de texto sem formatação para Bob através de um canal de público não seguro. Envia a mensagem de hash para Bob por um canal seguro de particular. Bob recebe a mensagem de texto sem formatação, coloca em hash e compara o hash com o hash troca em particular. Se os hashes corresponderem, Bob saberá duas coisas:  
  
    -   A mensagem não foi alterada.  
  
    -   O remetente da mensagem (Alice) é autêntico.  
  
     Para este sistema de trabalho, Alice deve ocultar seu valor original do hash de todas as partes exceto Bob.  
  
-   Alice envia a mensagem de texto sem formatação para Bob através de um canal de público não seguro e coloca a mensagem de hash em seu site podem ser exibido publicamente.  
  
     Este método evita a violação de mensagem, impedindo que qualquer pessoa modificando o valor de hash. Embora a mensagem e seu hash podem ser lidos por qualquer pessoa, o valor de hash pode ser alterado somente por Alice. Um invasor que deseja representar Alice requer acesso ao site de Alice.  
  
 Nenhum dos métodos anteriores impede que alguém ler mensagens de Alice, porque elas são transmitidas em texto não criptografado. Segurança completa normalmente requer criptografia e assinaturas digitais (assinatura de mensagens).  
  
 O [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] fornece as seguintes classes que implementam algoritmos de hash:  
  
-   <xref:System.Security.Cryptography.HMACSHA1>.  
  
-   <xref:System.Security.Cryptography.MACTripleDES>.  
  
-   <xref:System.Security.Cryptography.MD5CryptoServiceProvider>.  
  
-   <xref:System.Security.Cryptography.RIPEMD160>.  
  
-   <xref:System.Security.Cryptography.SHA1Managed>.  
  
-   <xref:System.Security.Cryptography.SHA256Managed>.  
  
-   <xref:System.Security.Cryptography.SHA384Managed>.  
  
-   <xref:System.Security.Cryptography.SHA512Managed>.  
  
-   Variantes HMAC de todos os algoritmos de algoritmo de Hash seguro (SHA), Message Digest 5 (MD5) e RIPEMD 160.  
  
-   Implementações de CryptoServiceProvider (wrappers de código gerenciado) de todos os algoritmos SHA.  
  
-   Implementações de Next Generation (CNG) de criptografia de todos os algoritmos MD5 e SHA.  
  
> [!NOTE]
>  Falhas de design de MD5 foram descobertas em 1996, e SHA-1 foi recomendado em vez disso. Em 2004, falhas adicionais foram descobertas e o algoritmo MD5 não é mais considerado seguro. O algoritmo SHA-1 também foi encontrado como sendo inseguras e SHA-2 agora é recomendado em vez disso.  
  
 [Voltar ao início](#top)  
  
<a name="random_numbers"></a>   
## <a name="random-number-generation"></a>Geração de números aleatórios  
 Geração de números aleatórios é parte integrante de muitas operações criptográficas. Por exemplo, as chaves de criptografia necessário para que seja possível aleatório que é impraticável para reproduzi-los. Geradores de números aleatórios criptográficos devem gerar uma saída é impraticável para prever com uma probabilidade que é melhor do que a metade. Portanto, qualquer método de prever o próximo bit de saída não deve executar melhor previsão aleatória. As classes de [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] usar geradores de números aleatórios para gerar chaves de criptografia.  
  
 O <xref:System.Security.Cryptography.RNGCryptoServiceProvider> classe é uma implementação de um algoritmo de gerador de número aleatório.  
  
 [Voltar ao início](#top)  
  
<a name="clickonce"></a>   
## <a name="clickonce-manifests"></a>Manifestos ClickOnce  
 No [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)], as seguintes classes de criptografia permitem que você obtenha e verifique as informações sobre assinaturas de manifesto para aplicativos que são implantados usando [a tecnologia ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment):  
  
-   O <xref:System.Security.Cryptography.ManifestSignatureInformation> classe obtém informações sobre uma assinatura de manifesto quando você usar seu <xref:System.Security.Cryptography.ManifestSignatureInformation.VerifySignature%2A> sobrecargas do método.  
  
-   Você pode usar o <xref:System.Security.ManifestKinds> enumeração para especificar quais manifestos para verificar. O resultado da verificação é um do <xref:System.Security.Cryptography.SignatureVerificationResult> valores de enumeração.  
  
-   O <xref:System.Security.Cryptography.ManifestSignatureInformationCollection> classe fornece uma coleção somente leitura de <xref:System.Security.Cryptography.ManifestSignatureInformation> objetos das assinaturas verificadas.  
  
 Além disso, as classes a seguir fornecem informações específicas de assinatura:  
  
-   <xref:System.Security.Cryptography.StrongNameSignatureInformation> Contém as informações de assinatura de nome forte de um manifesto.  
  
-   <xref:System.Security.Cryptography.X509Certificates.AuthenticodeSignatureInformation> representa as informações de assinatura Authenticode de um manifesto.  
  
-   <xref:System.Security.Cryptography.X509Certificates.TimestampInformation> contém informações sobre o carimbo de hora em uma assinatura Authenticode.  
  
-   <xref:System.Security.Cryptography.X509Certificates.TrustStatus> Fornece uma maneira simple para verificar se uma assinatura Authenticode é confiável.  
  
 [Voltar ao início](#top)  
  
<a name="suite_b"></a>   
## <a name="suite-b-support"></a>Suporte ao conjunto B  
 O [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] suporta o conjunto de algoritmos criptográficos publicado pela agência de segurança (NSA) National conjunto B. Para obter mais informações sobre o Suite B, consulte o [NSA Suite B criptografia fatos folha](https://www.nsa.gov/what-we-do/information-assurance/).  
  
 Os seguintes algoritmos estão incluídos:  
  
-   Avançadas de algoritmo de criptografia AES (padrão) com tamanhos de chave de 128, 192, e 256 bits para criptografia.  
  
-   Proteja os algoritmos de Hash SHA-1, SHA-256, SHA-384 e SHA-512 para hash. (Os três últimos são geralmente agrupados juntos e chamados de SHA-2.)  
  
-   Elíptica curva assinatura ECDSA (algoritmo Digital), usando curvas de 256 bits, 384 bits e 521 bits primos para assinatura. A documentação da NSA especificamente define essas curvas e chama p-256, p-384 e p-521. Esse algoritmo é fornecido pelo <xref:System.Security.Cryptography.ECDsaCng> classe. Ele permite que você entre com uma chave privada e verificar a assinatura com uma chave pública.  
  
-   Algoritmo de curva Diffie-Hellman (ECDH) elíptica, usando curvas de primos 521 bits, 384 bits e 256 bits para a troca de chaves e acordo secreto. Esse algoritmo é fornecido pelo <xref:System.Security.Cryptography.ECDiffieHellmanCng> classe.  
  
 Wrappers de código gerenciado para o FIPS Federal Information Processing Standard () certified implementações das implementações do AES, SHA-256, SHA-384 e SHA-512 estão disponíveis na nova <xref:System.Security.Cryptography.AesCryptoServiceProvider>, <xref:System.Security.Cryptography.SHA256CryptoServiceProvider>, <xref:System.Security.Cryptography.SHA384CryptoServiceProvider>, e <xref:System.Security.Cryptography.SHA512CryptoServiceProvider> classes.  
  
 [Voltar ao início](#top)  
  
<a name="cng"></a>   
## <a name="cryptography-next-generation-cng-classes"></a>Cryptography Next Generation (CNG) Classes  
 As classes de Cryptography Next Generation (CNG) fornecem um wrapper gerenciado em torno das funções CNG nativo. (A CNG é a substituição de CryptoAPI.) Essas classes têm "Cng" como parte de seus nomes. É fundamental para as classes de wrapper CNG o <xref:System.Security.Cryptography.CngKey> chave da classe de contêiner, que abstrai o armazenamento e o uso de chaves CNG. Essa classe permite que você armazene um par de chaves ou uma chave pública de forma segura e consultá-lo usando um nome de cadeia de caracteres simples. O elíptica com base em curva <xref:System.Security.Cryptography.ECDsaCng> classe da assinatura e o <xref:System.Security.Cryptography.ECDiffieHellmanCng> pode usar a classe de criptografia <xref:System.Security.Cryptography.CngKey> objetos.  
  
 O <xref:System.Security.Cryptography.CngKey> classe é usada para uma variedade de operações adicionais, incluindo abrir, criar, excluir e exportar chaves. Ele também fornece acesso para o identificador de chave base a ser usado ao chamar funções nativas diretamente.  
  
 O [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] também inclui uma variedade de classes CNG auxiliares, como o seguinte:  
  
-   <xref:System.Security.Cryptography.CngProvider> mantém um provedor de armazenamento de chaves.  
  
-   <xref:System.Security.Cryptography.CngAlgorithm> mantém um algoritmo CNG.  
  
-   <xref:System.Security.Cryptography.CngProperty> mantém as propriedades de chave usadas com frequência.  
  
 [Voltar ao início](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Modelo de criptografia](../../../docs/standard/security/cryptography-model.md)|Descreve como a criptografia é implementada na biblioteca de classes base.|  
|[Instruções passo a passo: criando um aplicativo criptográfico](../../../docs/standard/security/walkthrough-creating-a-cryptographic-application.md)|Demonstra as tarefas básicas de criptografia e descriptografia.|  
|[Configurando classes de criptografia](../../../docs/framework/configure-apps/configure-cryptography-classes.md)|Descreve como mapear nomes de algoritmo para classes de criptografia e mapear os identificadores de objeto para um algoritmo de criptografia.|
