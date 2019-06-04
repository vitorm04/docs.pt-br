---
title: Serviços criptográficos
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- cryptography [.NET Framework]
- pattern of derived class inheritance
- digital signatures
- asymmetric cryptographic algorithms
- digital signatures, public-key systems
- public keys
- decryption [.NET Framework]
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fa05fe1e170a0285df73d179ef39db6301059ac8
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490955"
---
# <a name="cryptographic-services"></a>Serviços criptográficos

<a name="top"></a> As redes públicas, como a Internet não fornecem um meio de uma comunicação segura entre entidades. A comunicação por essas redes é suscetível a que está sendo lido ou modificado até mesmo por terceiros não autorizados. A criptografia ajuda a proteger os dados sejam exibidos, fornece maneiras de detectar se os dados foram modificados, e ajuda a fornecer um meio seguro de comunicação em canais de outra forma não seguras. Por exemplo, dados podem ser criptografados usando um algoritmo de criptografia, transmitidos em um estado criptografado e mais tarde descriptografados pelo parceiro pretendido. Se um terceiro intercepta os dados criptografados, será difícil decifrar.

No .NET Framework, as classes de <xref:System.Security.Cryptography?displayProperty=nameWithType> namespace gerenciar muitos detalhes de criptografia para você. Algumas são invólucros para a API de criptografia da Microsoft não gerenciado (CryptoAPI), enquanto outras são implementações puramente gerenciadas. Você não precisa ser um especialista em criptografia para usar essas classes. Quando você cria uma nova instância de um da criptografia de classes do algoritmo, as chaves são geradas automaticamente para facilidade de uso e as propriedades padrão são tão seguros e protegidos possível.

Esta visão geral fornece um resumo dos métodos de criptografia e práticas recomendadas com suporte pelo .NET Framework, incluindo os manifestos do ClickOnce, Suite B e suporte de criptografia CNG (Next Generation) introduzido no .NET Framework 3.5.

Esta visão geral contém as seguintes seções:

- [Primitivos criptográficos](#primitives)

- [Criptografia de chave secreta](#secret_key)

- [Criptografia de chave pública](#public_key)

- [Assinaturas digitais](#digital_signatures)

- [Valores de hash](#hash_values)

- [Geração de números aleatórios](#random_numbers)

- [Manifestos do ClickOnce](#clickonce)

- [Suporte para Suite B](#suite_b)

- [Tópicos relacionados](#related_topics)

Para obter informações adicionais sobre a criptografia e sobre as ferramentas que permitem que você adicione segurança criptográfica aos seus aplicativos, componentes e serviços da Microsoft, consulte o desenvolvimento de Win32 e COM, a seção de segurança desta documentação.

<a name="primitives"></a>

## <a name="cryptographic-primitives"></a>Primitivos criptográficos

Em uma situação comum em que a criptografia é usada, duas partes (Alice e Bob) se comunicam por um canal não seguro. Alice e Bob deseja garantir que sua comunicação permaneça incompreensível por qualquer pessoa que pode estar escutando. Além disso, como Alice e Bob está em locais remotos, Alice deve ter certeza de que as informações que ela recebeu de Bob não foi modificadas por qualquer pessoa durante a transmissão. Além disso, ela deve garantir que as informações realmente se originam de Bob e não de alguém que está representando a Bob.

Criptografia é usada para atingir as seguintes metas:

- Confidencialidade: Para ajudar a proteger a identidade do usuário ou os dados sejam lidas.

- Integridade de dados: Para ajudar a proteger os dados que está sendo alterada.

- Autenticação: Para garantir que os dados originados de uma pessoa específica.

- Não-repúdio: Para impedir que uma pessoa específica negando o envio de uma mensagem.

Para atingir essas metas, você pode usar uma combinação de algoritmos e práticas recomendadas, conhecidas como primitivos criptográficos para criar um esquema de criptografia. A tabela a seguir lista os primitivos criptográficos e seus usos.

|Primitivos criptográficos|Use|
|-----------------------------|---------|
|Criptografia de chave de segredo (criptografia simétrica)|Executa uma transformação nos dados para mantê-lo de ser lido por terceiros. Esse tipo de criptografia usa compartilhada, uma única chave secreta para criptografar e descriptografar dados.|
|Criptografia de chave pública (criptografia assimétrica)|Executa uma transformação nos dados para mantê-lo de ser lido por terceiros. Esse tipo de criptografia usa um par de chaves pública/privada para criptografar e descriptografar dados.|
|Uma assinatura criptográfica|Ajuda a verificar a origem dos dados de um terceiro, criando uma assinatura digital que é exclusiva para essa parte. Esse processo também usa funções de hash.|
|Hashes criptográficos|Mapeia dados de qualquer comprimento para uma sequência de bytes de comprimento fixo. Os hashes são estatisticamente exclusivos; uma sequência diferente de dois bytes não serão de hash para o mesmo valor.|

[Voltar ao início](#top)

<a name="secret_key"></a>

## <a name="secret-key-encryption"></a>Criptografia de chave secreta

Algoritmos de criptografia de chave secreta usam uma única chave secreta para criptografar e descriptografar dados. Você deve proteger a chave de acesso por agentes não autorizados, pois qualquer parte que tem a chave pode usá-lo para descriptografar os dados ou criptografar seus próprios dados, afirmando que ela seja proveniente de você.

Chave secreta de criptografia também é conhecida como criptografia simétrica porque a mesma chave é usada para criptografia e descriptografia. Algoritmos de criptografia de chave secreta são muito rápidos (em comparação com os algoritmos de chave pública) e são bem adequados para executar transformações de criptografia em grandes fluxos de dados. Algoritmos de criptografia assimétrica, como RSA são limitados matematicamente na quantidade de dados, eles podem criptografar. Algoritmos de criptografia simétrica geralmente não têm esses problemas.

Um tipo de algoritmo de chave de segredo chamado uma codificação de bloco é usado para criptografar um bloco de dados por vez. Codificações de bloco fortes, como criptografia de dados padrão (DES), TripleDES, e a criptografia AES (padrão avançado) criptograficamente transformar um bloco de entrada de *n* bytes em um bloco de saída de bytes criptografados. Se você quiser criptografar ou descriptografar uma sequência de bytes, você precisa fazê-lo bloco por bloco. Porque *n* é pequeno (8 bytes para DES e TripleDES; 16 bytes [padrão], em bytes de 24 ou 32 bytes para AES), valores de dados que são maiores do que *n* precisam ser criptografados um bloco por vez. Valores de dados que são menores do que *n* precisa ser expandido para *n* fim de ser processado.

Uma forma simple de codificação de bloco é chamada de modo de livro de códigos eletrônico (ECB). Modo ECB não é considerado seguro, porque ele não usa um vetor de inicialização para inicializar o primeiro bloco de texto sem formatação. Para uma determinada chave secreta *k*, uma codificação de bloco simples que não usa um vetor de inicialização criptografará o mesmo bloco de entrada de texto não criptografado no mesmo bloco de saída do texto cifrado. Portanto, se você tiver blocos duplicados no seu fluxo de entrada de texto sem formatação, você terá de blocos duplicados no seu fluxo de texto cifrado de saída. Esses blocos de saída duplicado alertar os usuários não autorizados para a criptografia fraca usaram os algoritmos que já foram empregados e os modos possíveis de ataque. O modo de criptografia ECB, portanto, é bastante vulnerável a análise e, por fim, a descoberta de chave.

As classes de codificação de bloco que são fornecidas na biblioteca de classes base usam um padrão de encadeamento de modo chamado blocos de criptografia encadeamento CBC (), embora você possa alterar esse padrão se desejar.

Codificações CBC superam os problemas associados com ECB codificações por meio de um vetor de inicialização (IV) para criptografar o primeiro bloco de texto sem formatação. Cada bloco subsequente de texto sem formatação passa por um OR exclusivo bit a bit (`XOR`) operação com o bloco de texto cifrado anterior antes de ele é criptografado. Cada bloco de texto cifrado, portanto, é dependente de todos os blocos anteriores. Quando esse sistema é cabeçalhos de mensagem usado, comuns que podem ser conhecidos para um usuário não autorizado não pode ser usado para efetuar engenharia reversa de uma chave.

Uma maneira de comprometer os dados são criptografados com uma criptografia CBC é executar uma pesquisa detalhada de todas as chaves possíveis. Dependendo do tamanho da chave que é usado para executar a criptografia, esse tipo de pesquisa é muito demorado usando até mesmo os computadores mais rápidos e, portanto, é impraticável. Chaves maiores são mais difíceis de decifrar. Embora a criptografia não impossibilitam, teoricamente, um adversário recuperar os dados criptografados, ele gere o custo de fazer isso. Se demorar três meses para executar uma pesquisa detalhada para recuperar dados que é significativos apenas para alguns dias, o método de pesquisa detalhada é impraticável.

A desvantagem de criptografia de chave secreta é que ele supõe que duas partes têm concordaram com uma chave e o IV e comunicadas seus valores. O IV não é considerado um segredo e pode ser transmitido em texto não criptografado com a mensagem. No entanto, a chave deve ser mantida em segredo de usuários não autorizados. Devido a esses problemas, criptografia de chave secreta geralmente é usada junto com a criptografia de chave pública para privada comunicar-se os valores da chave e IV.

Supondo que Alice e Bob é duas partes que desejam se comunicar através de um canal não seguro, eles podem usar criptografia de chave secreta da seguinte maneira: Alice e Bob concorda em usar um algoritmo específico (por exemplo, AES) com uma chave particular e o IV. Alice compõe uma mensagem e cria um fluxo de rede (talvez uma nomeada pipe ou rede email) no qual enviar a mensagem. Em seguida, ela criptografa o texto usando a chave e o IV e envia a mensagem criptografada e o IV para Bob através da intranet. Carlos recebe o texto criptografado e descriptografa-a usando o IV e acordados anteriormente a chave. Se a transmissão é interceptada, o interceptador não é possível recuperar a mensagem original, porque ele não sabe a chave. Nesse cenário, somente a chave deve permanecer secreta. Em um cenário do mundo real, Alice ou Bob gera uma chave secreta e usa criptografia de chave pública (assimétrica) para transferir a chave (simétrica) secreta para a outra parte. Para obter mais informações sobre a criptografia de chave pública, consulte a próxima seção.

O .NET Framework fornece as seguintes classes que implementam algoritmos de criptografia de chave secreta:

- <xref:System.Security.Cryptography.AesManaged> (introduzido no .NET Framework 3.5).

- <xref:System.Security.Cryptography.DESCryptoServiceProvider>.

- <xref:System.Security.Cryptography.HMACSHA1> (Isso é tecnicamente um algoritmo de chave de segredo porque ele representa o código de autenticação de mensagem que é calculado usando uma função de hash criptográfico, combinada com uma chave secreta. Ver [valores de Hash](#hash_values), mais adiante neste tópico.)

- <xref:System.Security.Cryptography.RC2CryptoServiceProvider>.

- <xref:System.Security.Cryptography.RijndaelManaged>.

- <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider>.

[Voltar ao início](#top)

<a name="public_key"></a>

## <a name="public-key-encryption"></a>Criptografia de chave pública

Criptografia de chave pública usa uma chave privada que deve ser mantida em segredo de usuários não autorizados e uma chave pública que pode se tornar pública para qualquer pessoa. A chave pública e a chave privada são matematicamente vinculados; dados criptografados com a chave pública podem ser descriptografados somente com a chave privada e os dados que estão assinados com a chave privada podem ser verificados somente com a chave pública. A chave pública pode ser disponibilizada para qualquer pessoa; ele é usado para criptografia de dados a serem enviados para o protetor da chave privada. Algoritmos de criptografia de chave pública também são conhecidos como algoritmos assimétricos porque uma chave é necessária para criptografar os dados e outra chave é necessária para descriptografar os dados. Uma regra básica de criptografia impede a reutilização da chave, e as duas chaves devem ser exclusivas para cada sessão de comunicação. No entanto, na prática, chaves assimétricas são geralmente de longa duração.

Duas partes (Alice e Bob) podem usar criptografia de chave pública da seguinte maneira: Primeiro, Alice gera um par de chaves pública/privada. Se Bob deseja enviar uma mensagem criptografada de Alice, ele pede sua chave pública. Alice envia sua chave pública Bob em uma rede não segura e Bob usa essa chave para criptografar uma mensagem. Bob envia a mensagem criptografada para Alice, e ela descriptografa usando sua chave privada. Se Bob recebida a chave de Alice por um canal não seguro, como uma rede pública, Bob está aberto a um ataque man-in-the-middle. Portanto, Carlos devem verificar com Alice que ele tenha uma cópia correta de sua chave pública.

Durante a transmissão de chave pública de Alice, um agente não autorizado pode interceptar a chave. Além disso, o mesmo agente pode interceptar a mensagem criptografada de Bob. No entanto, o agente não pode descriptografar a mensagem com a chave pública. A mensagem pode ser descriptografada somente com a chave privada de Alice, que não foram transmitida. Alice não usa sua chave privada para criptografar uma mensagem de resposta para Bob, porque qualquer pessoa com a chave pública pode descriptografar a mensagem. Se Alice quer enviar uma mensagem de volta para Bob, ela solicitará a sua chave pública de Bob e criptografa sua mensagem usando essa chave pública. Bob descriptografa a mensagem usando sua chave privada associada.

Nesse cenário, Alice e Bob use criptografia de chave pública (assimétrica) para transferir uma chave de segredo (simétrica) e usar a criptografia de chave secreta para o restante de sua sessão.

A lista a seguir oferece comparações entre os algoritmos de criptografia de chave pública e a chave secreta:

- Algoritmos de criptografia de chave pública usam um tamanho de buffer fixo, ao passo que algoritmos de criptografia de chave secreta usam um buffer de comprimento variável.

- Algoritmos de chave pública não podem ser usados os dados de cadeia juntos em fluxos a maneira como os algoritmos de chave secreta podem, porque apenas pequenas quantidades de dados podem ser criptografadas. Portanto, operações assimétricas não usam o mesmo modelo de streaming como operações simétricas.

- Criptografia de chave pública tem um keyspace muito maior (intervalo de valores possíveis para a chave) que a criptografia de chave secreta. Portanto, a criptografia de chave pública é menos suscetível a ataques completa que tente todas as chaves possíveis.

- As chaves públicas são fáceis de distribuir porque eles não precisam ser protegidos, desde que alguma forma existe para verificar a identidade do remetente.

- Alguns algoritmos de chave pública (como RSA e DSA, mas não Diffie-Hellman) podem ser usados para criar assinaturas digitais para verificar a identidade do remetente de dados.

- Algoritmos de chave pública forem muito lentos em comparação com os algoritmos de chave secreta e não são projetados para criptografar uma grande quantidade de dados. Algoritmos de chave pública são úteis apenas para transferir muito pequenas quantidades de dados. Normalmente, a criptografia de chave pública é usada para criptografar uma chave e IV a ser usado por um algoritmo de chave secreta. Depois que a chave e IV são transferidas, criptografia de chave secreta é usada para o restante da sessão.

O .NET Framework fornece as seguintes classes que implementam algoritmos de criptografia de chave pública:

- <xref:System.Security.Cryptography.DSACryptoServiceProvider>

- <xref:System.Security.Cryptography.RSACryptoServiceProvider>

- <xref:System.Security.Cryptography.ECDiffieHellman> (classe base)

- <xref:System.Security.Cryptography.ECDiffieHellmanCng>

- <xref:System.Security.Cryptography.ECDiffieHellmanCngPublicKey> (classe base)

- <xref:System.Security.Cryptography.ECDiffieHellmanKeyDerivationFunction> (classe base)

- <xref:System.Security.Cryptography.ECDsaCng>

RSA permite criptografia e assinatura, mas DSA pode ser usada apenas para a assinatura e Diffie-Hellman pode ser usado apenas para geração de chave. Em geral, algoritmos de chave pública são mais limitados em seus usos que algoritmos de chave privada.

[Voltar ao início](#top)

<a name="digital_signatures"></a>

## <a name="digital-signatures"></a>Assinaturas digitais

Algoritmos de chave pública também podem ser usados para assinaturas digitais de formulário. Assinaturas digitais para autenticar a identidade de um remetente (se você confiar a chave pública do remetente) e ajudar a proteger a integridade dos dados. Usando uma chave pública gerada por Alice, o destinatário dos dados de Alice pode verificar que Alice enviou comparando a assinatura digital para os dados de Alice e a chave pública de Alice.

Para usar a criptografia de chave pública para assinar digitalmente uma mensagem, Alice primeiro aplica um algoritmo de hash para a mensagem para criar um resumo da mensagem. O resumo da mensagem é uma representação compacta e exclusiva de dados. Alice, em seguida, criptografa o resumo da mensagem com sua chave privada para criar sua assinatura pessoal. Ao receber a mensagem e a assinatura, Bob descriptografa a assinatura usando a chave pública de Alice para recuperar o resumo da mensagem e os hashes de mensagem usando o mesmo algoritmo de hash que Alice é usada. Se o resumo da mensagem que Bob computa exatamente corresponder o resumo da mensagem recebido de Alice, Bob é garantido que a mensagem veio o detentor da chave privada e que os dados não foi modificados. Se Bob confia que Alice é o detentor da chave privada, ele sabe que a mensagem foi enviada por Alice.

> [!NOTE]
> Uma assinatura pode ser verificada por qualquer pessoa porque a chave pública do remetente é conhecimento comum e normalmente é incluído no formato de assinatura digital. Esse método não manterá a confidencialidade da mensagem; para a mensagem a ser secreta, ele também deve ser criptografado.

O .NET Framework fornece as seguintes classes que implementam algoritmos de assinatura digital:

- <xref:System.Security.Cryptography.DSACryptoServiceProvider>

- <xref:System.Security.Cryptography.RSACryptoServiceProvider>

- <xref:System.Security.Cryptography.ECDsa> (classe base)

- <xref:System.Security.Cryptography.ECDsaCng>

 [Voltar ao início](#top)

<a name="hash_values"></a>

## <a name="hash-values"></a>Valores de hash

Algoritmos de hash mapeiam valores binários de um comprimento arbitrário para menores valores binários de comprimento fixo, conhecido como valores de hash. Um valor de hash é uma representação numérica de uma parte dos dados. Se um parágrafo de texto não criptografado de hash e alterar até mesmo uma letra do parágrafo, um hash subsequente produzirá um valor diferente. Se o hash é criptograficamente forte, seu valor será alterado significativamente. Por exemplo, se um único bit de uma mensagem for alterado, uma função de hash forte pode produzir uma saída diferente em 50%. Muitos valores de entrada podem hash para o mesmo valor de saída. No entanto, é impraticável para encontrar duas entradas distintas esse hash com o mesmo valor.

Duas partes (Alice e Bob) poderiam usar uma função de hash para garantir a integridade da mensagem. Eles selecionaria um algoritmo de hash para assinar suas mensagens. Alice gravar uma mensagem e, em seguida, criar um hash da mensagem usando o algoritmo selecionado. Eles, em seguida, siga um dos seguintes métodos:

- Alice envia a mensagem de texto sem formatação e a mensagem de hash (assinatura digital) para Bob. Carlos recebem e hashes de mensagem e compara seu valor de hash para o valor de hash que ele recebeu de Alice. Se os valores de hash forem idênticos, a mensagem não foi alterada. Se os valores não forem idênticos, a mensagem foi alterada depois que ele escreveu Alice.

    Infelizmente, esse método não estabelece a autenticidade do remetente. Qualquer pessoa pode representar Alice e enviar uma mensagem para Bob. Eles podem usar o mesmo algoritmo de hash para assinar sua mensagem e tudo o que Bob pode determinar se é que a mensagem corresponda à sua assinatura. Isso é uma forma de um ataque man-in-the-middle. Para obter mais informações, consulte [geração CNG (Cryptography Next) exemplo de comunicação seguro](https://docs.microsoft.com/previous-versions/cc488018(v=vs.100)).

- Alice envia a mensagem de texto sem formatação para Bob, por um canal público não seguro. Ela envia a mensagem de hash para Bob por um canal seguro de particular. Bob recebe a mensagem de texto sem formatação, coloca em hash e compara o hash para o hash em particular troca. Se os hashes corresponderem, Bob sabe duas coisas:

    - A mensagem não foi alterada.

    - O remetente da mensagem (Alice) é autêntico.

    Para este sistema funcionar, Alice deve ocultar seu valor original de hash de todas as partes, exceto Carlos.

- Alice envia a mensagem de texto sem formatação para Bob, por um canal público não seguro e coloca a mensagem de hash em seu site podem ser exibido publicamente.

    Esse método evita a violação de mensagem, impedindo que qualquer pessoa modificar o valor de hash. Embora a mensagem e seu hash podem ser lidos por qualquer pessoa, o valor de hash pode ser alterado somente por Alice. Um invasor que deseja representar Alice exigiria acesso ao site de Web de Alice.

Nenhum dos métodos anteriores impedirá alguém de ler as mensagens de Alice, porque elas são transmitidas em texto sem formatação. Segurança completa normalmente requer assinaturas digitais (assinatura de mensagens) e criptografia.

O .NET Framework fornece as seguintes classes que implementam algoritmos de hash:

- <xref:System.Security.Cryptography.HMACSHA1>.

- <xref:System.Security.Cryptography.MACTripleDES>.

- <xref:System.Security.Cryptography.MD5CryptoServiceProvider>.

- <xref:System.Security.Cryptography.RIPEMD160>.

- <xref:System.Security.Cryptography.SHA1Managed>.

- <xref:System.Security.Cryptography.SHA256Managed>.

- <xref:System.Security.Cryptography.SHA384Managed>.

- <xref:System.Security.Cryptography.SHA512Managed>.

- Variantes HMAC de todos os algoritmos Secure Hash Algorithm (SHA), Message Digest 5 (MD5) e RIPEMD-160.

- Implementações de CryptoServiceProvider (wrappers de código gerenciado) de todos os algoritmos SHA.

- Implementações de próxima geração (CNG) de criptografia de todos os algoritmos MD5 e SHA.

> [!NOTE]
> Falhas de design de MD5 foram descobertas em 1996, e SHA-1 foi recomendado em vez disso. Em 2004, falhas adicionais foram descobertas e o algoritmo MD5 não é mais considerado seguro. O algoritmo SHA-1 também foi encontrado para ser inseguro e SHA-2 agora é recomendado em vez disso.

[Voltar ao início](#top)

<a name="random_numbers"></a>

## <a name="random-number-generation"></a>Geração de números aleatórios

Geração de números aleatórios é parte integrante de muitas operações criptográficas. Por exemplo, chaves de criptografia precisam ser tão aleatório possível para que ele seja impraticável para reproduzi-los. Geradores de números aleatórios criptográficos devem gerar uma saída é impraticável para prever com uma probabilidade de que é melhor do que a metade. Portanto, qualquer método de prever o próximo bit de saída não deve executar melhor do que a previsão aleatória. As classes no .NET Framework usam os geradores de números aleatórios para gerar chaves de criptografia.

O <xref:System.Security.Cryptography.RNGCryptoServiceProvider> classe é uma implementação de um algoritmo do gerador de números aleatórios.

[Voltar ao início](#top)

<a name="clickonce"></a>

## <a name="clickonce-manifests"></a>Manifestos do ClickOnce

No [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)], as classes de criptografia a seguir permitem que você obtenha e verifique se as informações sobre assinaturas de manifesto para aplicativos que são implantados usando [tecnologia ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment):

- O <xref:System.Security.Cryptography.ManifestSignatureInformation> classe obtém informações sobre uma assinatura de manifesto quando você usa seu <xref:System.Security.Cryptography.ManifestSignatureInformation.VerifySignature%2A> sobrecargas de método.

- Você pode usar o <xref:System.Security.ManifestKinds> enumeração para especificar quais manifestos para verificar. O resultado da verificação é um do <xref:System.Security.Cryptography.SignatureVerificationResult> valores de enumeração.

- O <xref:System.Security.Cryptography.ManifestSignatureInformationCollection> classe fornece uma coleção somente leitura de <xref:System.Security.Cryptography.ManifestSignatureInformation> objetos das assinaturas verificadas.

 Além disso, as classes a seguir fornecem informações específicas de assinatura:

- <xref:System.Security.Cryptography.StrongNameSignatureInformation> Contém as informações de assinatura de nome forte de um manifesto.

- <xref:System.Security.Cryptography.X509Certificates.AuthenticodeSignatureInformation> representa as informações de assinatura Authenticode de um manifesto.

- <xref:System.Security.Cryptography.X509Certificates.TimestampInformation> contém informações sobre o carimbo de hora em uma assinatura Authenticode.

- <xref:System.Security.Cryptography.X509Certificates.TrustStatus> Fornece uma maneira simples de verificar se uma assinatura Authenticode é confiável.

[Voltar ao início](#top)

<a name="suite_b"></a>

## <a name="suite-b-support"></a>Suporte para Suite B

O [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] suporta o conjunto de algoritmos criptográficos publicado pelo National Security Agency (NSA) Suite B. Para obter mais informações sobre o Suite B, consulte o [NSA Suite B criptografia folheto informativo](https://www.nsa.gov/what-we-do/information-assurance/).

Os seguintes algoritmos estão incluídos:

- Avançadas de algoritmo de criptografia AES (padrão) com tamanhos de chave de 128, 192, e 256 bits para criptografia.

- Proteja os algoritmos de Hash SHA-1, SHA-256, SHA-384 e SHA-512 para hash. (Os três últimos são geralmente agrupados juntos e conhecidos como SHA-2.)

- ECDSA Digital curva elíptica assinatura algoritmo (), usando curvas de módulos primos 521 bits, 384 bits e 256 bits para a assinatura. A documentação da NSA especificamente define esses curvas e os chama p-256, p-384 e p-521. Esse algoritmo é fornecido pela <xref:System.Security.Cryptography.ECDsaCng> classe. Ele permite que você se conectar com uma chave privada e verificar a assinatura com uma chave pública.

- Elíptica Diffie-Hellman algoritmo ECDH (curva), usando curvas de módulos primos 521 bits, 384 bits e 256 bits para a troca de chaves e o acordo secreto. Esse algoritmo é fornecido pela <xref:System.Security.Cryptography.ECDiffieHellmanCng> classe.

Wrappers de código gerenciado para o FIPS Federal Information Processing Standard () certificada implementações das implementações AES, SHA-256, SHA-384 e SHA-512 estão disponíveis na nova <xref:System.Security.Cryptography.AesCryptoServiceProvider>, <xref:System.Security.Cryptography.SHA256CryptoServiceProvider>, <xref:System.Security.Cryptography.SHA384CryptoServiceProvider>, e <xref:System.Security.Cryptography.SHA512CryptoServiceProvider> classes.

[Voltar ao início](#top)

<a name="cng"></a>

## <a name="cryptography-next-generation-cng-classes"></a>Classes de geração (CNG) próximo da criptografia

As classes de criptografia CNG (Next Generation) fornecem um wrapper gerenciado em torno das funções da CNG nativos. (A CNG é a substituição de CryptoAPI.) Essas classes têm "Cng" como parte de seus nomes. É fundamental para as classes de wrapper CNG o <xref:System.Security.Cryptography.CngKey> chave de classe de contêiner, que abstrai o armazenamento e o uso de chaves CNG. Essa classe permite que você armazene um par de chaves ou uma chave pública com segurança e fazer referência a ele usando um nome de cadeia de caracteres simples. O elíptica com base em curva <xref:System.Security.Cryptography.ECDsaCng> classe de assinatura e o <xref:System.Security.Cryptography.ECDiffieHellmanCng> pode usar a classe de criptografia <xref:System.Security.Cryptography.CngKey> objetos.

O <xref:System.Security.Cryptography.CngKey> classe é usada para uma variedade de operações adicionais, incluindo abrir, criar, excluir e exportar chaves. Ele também fornece acesso para o identificador de chave de base a ser usado ao chamar funções nativas diretamente.

O [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] também inclui uma variedade de classes CNG auxiliares, como o seguinte:

- <xref:System.Security.Cryptography.CngProvider> mantém um provedor de armazenamento.

- <xref:System.Security.Cryptography.CngAlgorithm> mantém um algoritmo CNG.

- <xref:System.Security.Cryptography.CngProperty> mantém as propriedades de chave usadas com frequência.

[Voltar ao início](#top)

<a name="related_topics"></a>

## <a name="related-topics"></a>Tópicos relacionados

|Título|Descrição|
|-----------|-----------------|
|[Modelo de criptografia](../../../docs/standard/security/cryptography-model.md)|Descreve como a criptografia é implementada na biblioteca de classes base.|
|[Passo a passo: Criando um aplicativo criptográfico](../../../docs/standard/security/walkthrough-creating-a-cryptographic-application.md)|Demonstra as tarefas básicas de criptografia e descriptografia.|
|[Configurando classes de criptografia](../../../docs/framework/configure-apps/configure-cryptography-classes.md)|Descreve como mapear nomes de algoritmo para classes de criptografia e identificadores de objeto do mapa para um algoritmo de criptografia.|
