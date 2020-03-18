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
ms.openlocfilehash: c1783a578d0b55b0b62a1ffb870802faca97623f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187004"
---
# <a name="cryptographic-services"></a>Serviços criptográficos

Redes públicas como a Internet não fornecem meios de comunicação segura entre entidades. A comunicação sobre essas redes é suscetível a ser lida ou mesmo modificada por terceiros não autorizados. A criptografia ajuda a proteger os dados de serem visualizados, fornece maneiras de detectar se os dados foram modificados e ajuda a fornecer um meio seguro de comunicação sobre canais não seguros. Por exemplo, os dados podem ser criptografados usando um algoritmo criptográfico, transmitido em um estado criptografado e posteriormente descriptografado pela parte pretendida. Se um terceiro interceptar os dados criptografados, será difícil decifrar.

No .NET Framework, as <xref:System.Security.Cryptography?displayProperty=nameWithType> classes no namespace gerenciam muitos detalhes de criptografia para você. Alguns são invólucros para a API de criptografia microsoft não gerenciada (CryptoAPI), enquanto outros são implementações puramente gerenciadas. Você não precisa ser um especialista em criptografia para usar essas aulas. Quando você cria uma nova instância de uma das classes de algoritmode criptografia, as chaves são geradas automaticamente para facilitar o uso, e as propriedades padrão são as mais seguras e seguras possíveis.

Essa visão geral fornece uma sinopse dos métodos e práticas de criptografia suportados pelo .NET Framework, incluindo os manifestos ClickOnce, O Suporte ao Conjunto B e criptografia Next Generation (CNG) introduzido no .NET Framework 3.5.

Para obter informações adicionais sobre criptografia e sobre serviços, componentes e ferramentas da Microsoft que permitem adicionar segurança criptográfica aos seus aplicativos, consulte a seção De desenvolvimento win32 e COM desta documentação.

## <a name="cryptographic-primitives"></a>Primitivos Criptográficos

Em uma situação típica onde a criptografia é usada, duas partes (Alice e Bob) se comunicam por um canal não seguro. Alice e Bob querem garantir que sua comunicação permaneça incompreensível por qualquer um que possa estar ouvindo. Além disso, como Alice e Bob estão em locais remotos, Alice deve ter certeza de que as informações que ela recebe de Bob não foram modificadas por ninguém durante a transmissão. Além disso, ela deve ter certeza de que a informação realmente se origina de Bob e não de alguém que está se passando por Bob.

A criptografia é usada para atingir os seguintes objetivos:

- Confidencialidade: Para ajudar a proteger a identidade ou os dados de um usuário de serem lidos.

- Integridade dos dados: Para ajudar a proteger os dados de serem alterados.

- Autenticação: Para garantir que os dados tenham origem em uma determinada parte.

- Não-repúdio: Para evitar que uma determinada parte negue que enviou uma mensagem.

Para alcançar esses objetivos, você pode usar uma combinação de algoritmos e práticas conhecidas como primitivos criptográficos para criar um esquema criptográfico. A tabela a seguir lista os primitivos criptográficos e seus usos.

|Primitivo criptográfico|Use|
|-----------------------------|---------|
|Criptografia de chave secreta (criptografia simétrica)|Realiza uma transformação nos dados para evitar que sejam lidos por terceiros. Esse tipo de criptografia usa uma única chave secreta compartilhada para criptografar e descriptografar dados.|
|Criptografia de chave pública (criptografia assimétrica)|Realiza uma transformação nos dados para evitar que sejam lidos por terceiros. Esse tipo de criptografia usa um par de chaves público/privado para criptografar e descriptografar dados.|
|Assinatura criptográfica|Ajuda a verificar se os dados são originários de uma parte específica, criando uma assinatura digital exclusiva para essa parte. Este processo também usa funções hash.|
|Hashes criptográficos|Mapeia dados de qualquer comprimento para uma seqüência de bytes de comprimento fixo. Hashes são estatisticamente únicos; uma seqüência diferente de dois bytes não terá hash para o mesmo valor.|

## <a name="secret-key-encryption"></a>Criptografia de chave secreta

Algoritmos de criptografia de chave secreta usam uma única chave secreta para criptografar e descriptografar dados. Você deve proteger a chave do acesso por agentes não autorizados, porque qualquer parte que tenha a chave pode usá-la para descriptografar seus dados ou criptografar seus próprios dados, alegando que se originaram de você.

A criptografia de chave secreta também é referida como criptografia simétrica porque a mesma chave é usada para criptografia e descriptografia. Algoritmos de criptografia de chave secreta são muito rápidos (comparados com algoritmos de chave pública) e são adequados para realizar transformações criptográficas em grandes fluxos de dados. Algoritmos de criptografia assimétrica, como o RSA, são limitados matematicamente em quantos dados podem criptografar. Algoritmos de criptografia simétrica simétricas geralmente não têm esses problemas.

Um tipo de algoritmo de chave secreta chamado cifra de bloco é usado para criptografar um bloco de dados de cada vez. As cifras de blocos como Des (Data Encryption Standard, padrão de criptografia de dados), TripleDES e AES (Advanced Encryption Standard, padrão de criptografia avançado) transformam criptograficamente um bloco de entrada de *n* bytes em um bloco de saída de bytes criptografados. Se você quiser criptografar ou descriptografar uma seqüência de bytes, você tem que fazê-lo bloco por bloco. Como *n* é pequeno (8 bytes para DES e TripleDES; 16 bytes [o padrão], 24 bytes ou 32 bytes para AES), valores de dados que são maiores que *n* têm que ser criptografados um bloco de cada vez. Os valores de dados que são menores do que *n* devem ser expandidos para *n* para serem processados.

Uma forma simples de cifra de bloco é chamada de modo de codebook eletrônico (BCE). O modo BCE não é considerado seguro, porque não usa um vetor de inicialização para inicializar o primeiro bloco de texto simples. Para uma determinada chave secreta *k,* uma cifra de bloco simples que não usa um vetor de inicialização criptografará o mesmo bloco de entrada do texto simples no mesmo bloco de saída de texto cifrado. Portanto, se você tiver blocos duplicados em seu fluxo de texto de entrada, você terá blocos duplicados no fluxo de texto cifrado de saída. Esses blocos de saída duplicados alertam os usuários não autorizados à criptografia fraca que usou os algoritmos que poderiam ter sido empregados, e os possíveis modos de ataque. O modo de cifra do BCE é, portanto, bastante vulnerável à análise e, em última instância, à descoberta-chave.

As classes de cifra de bloco fornecidas na biblioteca de classe base usam um modo de encadeamento padrão chamado cumchaining de blocos de cifras (CBC), embora você possa alterar esse padrão se quiser.

As cifras CBC superam os problemas associados às cifras do BCE usando um vetor de inicialização (IV) para criptografar o primeiro bloco de texto simples. Cada bloco subseqüente de plaintext sofre`XOR`uma operação ou ( ) pouco exclusiva com o bloco de texto cifrado anterior antes de ser criptografado. Cada bloco de texto cifrado depende, portanto, de todos os blocos anteriores. Quando este sistema é usado, cabeçalhos de mensagens comuns que podem ser conhecidos por um usuário não autorizado não podem ser usados para fazer engenharia reversa de uma chave.

Uma maneira de comprometer dados criptografados com uma cifra CBC é realizar uma pesquisa exaustiva de todas as chaves possíveis. Dependendo do tamanho da chave que é usada para executar a criptografia, esse tipo de pesquisa é muito demorado usando até mesmo os computadores mais rápidos e, portanto, é inviável. Tamanhos de chave maiores são mais difíceis de decifrar. Embora a criptografia não torne teoricamente impossível para um adversário recuperar os dados criptografados, isso aumenta o custo de fazer isso. Se levar três meses para realizar uma pesquisa exaustiva para recuperar dados que são significativos apenas por alguns dias, o método de pesquisa exaustivo é impraticável.

A desvantagem da criptografia de chave secreta é que presume que duas partes concordaram com uma chave e iv, e comunicaram seus valores. O IV não é considerado um segredo e pode ser transmitido em texto simples com a mensagem. No entanto, a chave deve ser mantida em segredo de usuários não autorizados. Por causa desses problemas, a criptografia de chave secreta é frequentemente usada em conjunto com a criptografia de chave pública para comunicar privadamente os valores da chave e iv.

Assumindo que Alice e Bob são duas partes que querem se comunicar por um canal não seguro, eles podem usar criptografia de chave secreta da seguinte forma: Alice e Bob concordam em usar um algoritmo em particular (AES, por exemplo) com uma chave particular e IV. Alice compõe uma mensagem e cria um fluxo de rede (talvez um canal ou e-mail de rede nomeado) no qual enviar a mensagem. Em seguida, ela criptografa o texto usando a chave e iv, e envia a mensagem criptografada e IV para Bob sobre a intranet. Bob recebe o texto criptografado e descriptografa-o usando a chave IV e previamente acordada. Se a transmissão for interceptada, o interceptador não poderá recuperar a mensagem original, porque eles não sabem a chave. Neste cenário, apenas a chave deve permanecer em segredo. Em um cenário do mundo real, alice ou Bob gera uma chave secreta e usa criptografia de chave pública (assimétrica) para transferir a chave secreta (simétrica) para a outra parte. Para obter mais informações sobre criptografia de chave pública, consulte a próxima seção.

O .NET Framework fornece as seguintes classes que implementam algoritmos de criptografia de chave secreta:

- <xref:System.Security.Cryptography.AesManaged>(introduzido no Quadro .NET 3.5).

- <xref:System.Security.Cryptography.DESCryptoServiceProvider>.

- <xref:System.Security.Cryptography.HMACSHA1>(Este é tecnicamente um algoritmo de chave secreta porque representa o código de autenticação de mensagens que é calculado usando uma função de hash criptográfica combinada com uma chave secreta. Consulte [Hash Values](#hash-values), mais tarde neste tópico.)

- <xref:System.Security.Cryptography.RC2CryptoServiceProvider>.

- <xref:System.Security.Cryptography.RijndaelManaged>.

- <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider>.

## <a name="public-key-encryption"></a>Criptografia de chave pública

A criptografia de chave pública usa uma chave privada que deve ser mantida em segredo de usuários não autorizados e uma chave pública que pode ser divulgada para qualquer pessoa. A chave pública e a chave privada estão matematicamente ligadas; os dados criptografados com a chave pública só podem ser descriptografados com a chave privada, e os dados assinados com a chave privada só podem ser verificados com a chave pública. A chave pública pode ser disponibilizada para qualquer pessoa; ele é usado para criptografar dados a serem enviados ao guardião da chave privada. Algoritmos criptográficos de chave pública também são conhecidos como algoritmos assimétricos porque uma chave é necessária para criptografar dados, e outra chave é necessária para descriptografar dados. Uma regra criptográfica básica proíbe o reaproveitamento de chaves, e ambas as chaves devem ser únicas para cada sessão de comunicação. No entanto, na prática, as chaves assimétricas são geralmente de longa duração.

Duas partes (Alice e Bob) podem usar criptografia de chave pública da seguinte forma: Primeiro, Alice gera um par de chaves públicas/privadas. Se Bob quer enviar uma mensagem criptografada para Alice, ele pede a chave pública dela. Alice envia a Bob sua chave pública sobre uma rede não segura, e Bob usa essa chave para criptografar uma mensagem. Bob envia a mensagem criptografada para Alice, e ela a decodifica usando sua chave privada. Se Bob recebeu a chave de Alice por um canal não seguro, como uma rede pública, Bob está aberto a um ataque de homem no meio. Portanto, Bob deve verificar com Alice que ele tem uma cópia correta de sua chave pública.

Durante a transmissão da chave pública de Alice, um agente não autorizado pode interceptar a chave. Além disso, o mesmo agente pode interceptar a mensagem criptografada de Bob. No entanto, o agente não pode descriptografar a mensagem com a chave pública. A mensagem só pode ser decodificada com a chave privada de Alice, que não foi transmitida. Alice não usa sua chave privada para criptografar uma mensagem de resposta para Bob, porque qualquer um com a chave pública poderia descriptografar a mensagem. Se Alice quer enviar uma mensagem de volta para Bob, ela pede bob sua chave pública e criptografa sua mensagem usando essa chave pública. Bob então descriptografa a mensagem usando sua chave privada associada.

Neste cenário, Alice e Bob usam criptografia de chave pública (assimétrica) para transferir uma chave secreta (simétrica) e usar criptografia de chave secreta para o restante de sua sessão.

A lista a seguir oferece comparações entre algoritmos criptográficos de chave pública e chave secreta:

- Algoritmos criptográficos de chave pública usam um tamanho de buffer fixo, enquanto algoritmos criptográficos de chave secreta usam um buffer de comprimento variável.

- Algoritmos de chave pública não podem ser usados para acorrentar dados em fluxos da maneira que algoritmos de chave secreta podem, porque apenas pequenas quantidades de dados podem ser criptografadas. Portanto, as operações assimétricas não utilizam o mesmo modelo de streaming que as operações simétricas.

- A criptografia de chave pública tem um espaço-chave muito maior (alcance de valores possíveis para a chave) do que a criptografia de chave secreta. Portanto, a criptografia de chave pública é menos suscetível a ataques exaustivos que tentam todas as chaves possíveis.

- As chaves públicas são fáceis de distribuir porque não precisa ser protegida, desde que exista alguma forma de verificar a identidade do remetente.

- Alguns algoritmos de chave pública (como RSA e DSA, mas não Diffie-Hellman) podem ser usados para criar assinaturas digitais para verificar a identidade do remetente de dados.

- Algoritmos de chave pública são muito lentos em comparação com algoritmos de chave secreta, e não são projetados para criptografar grandes quantidades de dados. Algoritmos de chave pública são úteis apenas para transferir quantidades muito pequenas de dados. Normalmente, a criptografia de chave pública é usada para criptografar uma chave e iv para ser usada por um algoritmo de chave secreta. Depois que a chave e a IV são transferidas, a criptografia de chave secreta é usada para o restante da sessão.

O .NET Framework fornece as seguintes classes que implementam algoritmos de criptografia de chave pública:

- <xref:System.Security.Cryptography.DSACryptoServiceProvider>

- <xref:System.Security.Cryptography.RSACryptoServiceProvider>

- <xref:System.Security.Cryptography.ECDiffieHellman>(classe base)

- <xref:System.Security.Cryptography.ECDiffieHellmanCng>

- <xref:System.Security.Cryptography.ECDiffieHellmanCngPublicKey>(classe base)

- <xref:System.Security.Cryptography.ECDiffieHellmanKeyDerivationFunction>(classe base)

- <xref:System.Security.Cryptography.ECDsaCng>

O RSA permite tanto a criptografia quanto a assinatura, mas o DSA pode ser usado apenas para assinar, e diffie-Hellman pode ser usado apenas para geração de chaves. Em geral, algoritmos de chave pública são mais limitados em seus usos do que algoritmos de chave privada.

## <a name="digital-signatures"></a>Assinaturas Digitais

Algoritmos de chave pública também podem ser usados para formar assinaturas digitais. As assinaturas digitais autenticam a identidade de um remetente (se você confiar na chave pública do remetente) e ajudam a proteger a integridade dos dados. Usando uma chave pública gerada por Alice, o destinatário dos dados de Alice pode verificar que Alice enviou comparando a assinatura digital com os dados de Alice e a chave pública de Alice.

Para usar a criptografia de chave pública para assinar digitalmente uma mensagem, Alice primeiro aplica um algoritmo de hash à mensagem para criar uma digestão de mensagem. O digerir da mensagem é uma representação compacta e única de dados. Alice então criptografa a mensagem digere com sua chave privada para criar sua assinatura pessoal. Ao receber a mensagem e a assinatura, Bob descriptografa a assinatura usando a chave pública de Alice para recuperar a mensagem e hashes a mensagem usando o mesmo algoritmo de hash que Alice usou. Se a mensagem digerir que Bob computa corresponde exatamente à mensagem de digestão recebida de Alice, Bob está certo de que a mensagem veio do possuidor da chave privada e que os dados não foram modificados. Se Bob confia que Alice é a dona da chave privada, ele sabe que a mensagem veio de Alice.

> [!NOTE]
> Uma assinatura pode ser verificada por qualquer pessoa porque a chave pública do remetente é de conhecimento comum e é tipicamente incluída no formato de assinatura digital. Este método não retém o sigilo da mensagem; para que a mensagem seja secreta, ela também deve ser criptografada.

O .NET Framework fornece as seguintes classes que implementam algoritmos de assinatura digital:

- <xref:System.Security.Cryptography.DSACryptoServiceProvider>

- <xref:System.Security.Cryptography.RSACryptoServiceProvider>

- <xref:System.Security.Cryptography.ECDsa>(classe base)

- <xref:System.Security.Cryptography.ECDsaCng>

## <a name="hash-values"></a>Valores de Hash

Algoritmos hash mapeiam valores binários de um comprimento arbitrário para valores binários menores de um comprimento fixo, conhecidos como valores de hash. Um valor de hash é uma representação numérica de um pedaço de dados. Se você hash um parágrafo de texto simples e alterar até mesmo uma letra do parágrafo, um hash subseqüente produzirá um valor diferente. Se o hash for criptograficamente forte, seu valor mudará significativamente. Por exemplo, se um único pedaço de mensagem for alterado, uma forte função hash pode produzir uma saída que difere em 50%. Muitos valores de entrada podem hash para o mesmo valor de saída. No entanto, é computacionalmente inviável encontrar duas entradas distintas que hash para o mesmo valor.

Duas partes (Alice e Bob) poderiam usar uma função hash para garantir a integridade da mensagem. Eles escolheriam um algoritmo hash para assinar suas mensagens. Alice escreveria uma mensagem e criaria um hash dessa mensagem usando o algoritmo selecionado. Eles seguiriam então um dos seguintes métodos:

- Alice envia a mensagem de texto simples e a mensagem hashed (assinatura digital) para Bob. Bob recebe e hashes a mensagem e compara seu valor hash com o valor de hash que ele recebeu de Alice. Se os valores de hash forem idênticos, a mensagem não foi alterada. Se os valores não são idênticos, a mensagem foi alterada depois que Alice a escreveu.

  Infelizmente, este método não estabelece a autenticidade do remetente. Qualquer um pode se passar por Alice e mandar uma mensagem ao Bob. Eles podem usar o mesmo algoritmo hash para assinar sua mensagem, e tudo o que Bob pode determinar é que a mensagem corresponde à sua assinatura. Esta é uma forma de um ataque homem-no-meio. Para obter mais informações, consulte [Cryptography Next Generation (CNG) Secure Communication Example](https://docs.microsoft.com/previous-versions/cc488018(v=vs.100)).

- Alice envia a mensagem de texto simples para Bob sobre um canal público não seguro. Ela envia a mensagem hashed para Bob sobre um canal privado seguro. Bob recebe a mensagem de texto simples, hashes-lo, e compara o hash com o hash privado trocado. Se os hashes coincidirem, Bob sabe duas coisas:

  - A mensagem não foi alterada.

  - O remetente da mensagem (Alice) é autêntico.

  Para que este sistema funcione, Alice deve esconder seu valor original de hash de todas as partes, exceto Bob.

- Alice envia a mensagem de texto simples para Bob por um canal público não seguro e coloca a mensagem hashed em seu site publicamente visível.

  Este método evita a adulteração de mensagens, impedindo que qualquer pessoa modifique o valor de hash. Embora a mensagem e seu hash possam ser lidos por qualquer um, o valor do hash só pode ser alterado por Alice. Um agressor que quer se passar por Alice precisaria de acesso ao site da Alice.

Nenhum dos métodos anteriores impedirá alguém de ler as mensagens de Alice, porque elas são transmitidas em texto simples. A segurança total normalmente requer assinaturas digitais (assinatura de mensagens) e criptografia.

O .NET Framework fornece as seguintes classes que implementam algoritmos de hashing:

- <xref:System.Security.Cryptography.HMACSHA1>.

- <xref:System.Security.Cryptography.MACTripleDES>.

- <xref:System.Security.Cryptography.MD5CryptoServiceProvider>.

- <xref:System.Security.Cryptography.RIPEMD160>.

- <xref:System.Security.Cryptography.SHA1Managed>.

- <xref:System.Security.Cryptography.SHA256Managed>.

- <xref:System.Security.Cryptography.SHA384Managed>.

- <xref:System.Security.Cryptography.SHA512Managed>.

- Variantes HMAC de todos os algoritmos Secure Hash Algorithm (SHA), Message Digest 5 (MD5) e RIPEMD-160.

- Implementações do CryptoServiceProvider (invólucros de código gerenciado) de todos os algoritmos SHA.

- Implementações de criptografia Next Generation (CNG) de todos os algoritmos MD5 e SHA.

> [!NOTE]
> Falhas de design MD5 foram descobertas em 1996, e SHA-1 foi recomendado em vez disso. Em 2004, falhas adicionais foram descobertas, e o algoritmo MD5 não é mais considerado seguro. O algoritmo SHA-1 também foi considerado inseguro, e o SHA-2 agora é recomendado.

## <a name="random-number-generation"></a>Geração de números aleatórios

A geração de números aleatórios é parte integrante de muitas operações criptográficas. Por exemplo, as chaves criptográficas precisam ser o mais aleatórias possível para que seja inviável reproduzi-las. Geradores de números aleatórios criptográficos devem gerar saída que é computacionalmente inviável de prever com uma probabilidade que é melhor do que a metade. Portanto, qualquer método de prever a próxima broca de saída não deve ter um desempenho melhor do que a adivinhação aleatória. As classes do Quadro .NET usam geradores de números aleatórios para gerar chaves criptográficas.

A <xref:System.Security.Cryptography.RNGCryptoServiceProvider> classe é uma implementação de um algoritmo gerador de números aleatórios.

## <a name="clickonce-manifests"></a>ClickOnce Manifests

No Quadro .NET 3.5, as seguintes classes de criptografia permitem obter e verificar informações sobre assinaturas manifestas para aplicativos que são implantados usando a [tecnologia ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment):

- A <xref:System.Security.Cryptography.ManifestSignatureInformation> classe obtém informações sobre uma <xref:System.Security.Cryptography.ManifestSignatureInformation.VerifySignature%2A> assinatura manifesto quando você usa suas sobrecargas de método.

- Você pode <xref:System.Security.ManifestKinds> usar a enumeração para especificar quais manifestos verificar. O resultado da verificação <xref:System.Security.Cryptography.SignatureVerificationResult> é um dos valores de enumeração.

- A <xref:System.Security.Cryptography.ManifestSignatureInformationCollection> classe fornece uma coleção <xref:System.Security.Cryptography.ManifestSignatureInformation> somente de objetos das assinaturas verificadas.

 Além disso, as seguintes classes fornecem informações específicas de assinatura:

- <xref:System.Security.Cryptography.StrongNameSignatureInformation>possui a informação de assinatura de nome forte para um manifesto.

- <xref:System.Security.Cryptography.X509Certificates.AuthenticodeSignatureInformation>representa as informações de assinatura do Authenticode para um manifesto.

- <xref:System.Security.Cryptography.X509Certificates.TimestampInformation>contém informações sobre o carimbo de hora em uma assinatura Authenticode.

- <xref:System.Security.Cryptography.X509Certificates.TrustStatus>fornece uma maneira simples de verificar se uma assinatura Authenticode é confiável.

## <a name="suite-b-support"></a>Suporte da Suíte B

O .NET Framework 3.5 suporta o conjunto B de algoritmos criptográficos publicado pela Agência Nacional de Segurança (NSA). Para obter mais informações sobre o Suite B, consulte o [Relatório de Fatos de Criptografia do Conjunto B da NSA](https://www.nsa.gov/what-we-do/information-assurance/).

Os seguintes algoritmos estão incluídos:

- Algoritmo Advanced Encryption Standard (AES) com tamanhos de chave de 128, 192 e 256 bits para criptografia.

- Algoritmos Hash Seguros SHA-1, SHA-256, SHA-384 e SHA-512 para hash. (Os três últimos são geralmente agrupados e referidos como SHA-2.)

- Algoritmo de Assinatura Digital da Curva Elíptica (ECDSA), usando curvas de 256 bits, 384 bits e 521 bits de moduli prime para assinar. A documentação da NSA define especificamente essas curvas, e as chama de P-256, P-384 e P-521. Este algoritmo é fornecido <xref:System.Security.Cryptography.ECDsaCng> pela classe. Ele permite que você assine com uma chave privada e verifique a assinatura com uma chave pública.

- Algoritmo de Curva Elíptica Diffie-Hellman (ECDH), usando curvas de 256 bits, 384 bits e 521 bits de moduli prime para a troca de chaves e acordo secreto. Este algoritmo é fornecido <xref:System.Security.Cryptography.ECDiffieHellmanCng> pela classe.

Os invólucros de código gerenciados para as implementações certificadas fips (Federal Information Processing Standard, padrão federal de processamento de informações) <xref:System.Security.Cryptography.AesCryptoServiceProvider> <xref:System.Security.Cryptography.SHA256CryptoServiceProvider>das <xref:System.Security.Cryptography.SHA384CryptoServiceProvider>implementações ae, SHA-256, SHA-384 e SHA-512 estão disponíveis nas novas , e <xref:System.Security.Cryptography.SHA512CryptoServiceProvider> classes.

## <a name="cryptography-next-generation-cng-classes"></a>Cryptography Next Generation (CNG) Classes

As classes Cryptography Next Generation (CNG) fornecem um invólucro gerenciado em torno das funções nativas do GNV. (O GNV é o substituto do CryptoAPI.) Essas classes têm "Cng" como parte de seus nomes. Central para as classes de <xref:System.Security.Cryptography.CngKey> invólucro de GNV é a classe de recipiente chave, que abstrai o armazenamento e o uso de chaves de GNV. Esta classe permite que você armazene um par de chaves ou uma chave pública com segurança e consulte-a usando um nome de seqüência simples. A classe de assinatura <xref:System.Security.Cryptography.ECDsaCng> baseada em <xref:System.Security.Cryptography.ECDiffieHellmanCng> curvas elípticas e a classe de criptografia podem usar <xref:System.Security.Cryptography.CngKey> objetos.

A <xref:System.Security.Cryptography.CngKey> classe é usada para uma variedade de operações adicionais, incluindo abertura, criação, exclusão e exportação de chaves. Ele também fornece acesso à alça de chave subjacente para usar ao chamar funções nativas diretamente.

O .NET Framework 3.5 também inclui uma variedade de classes de GNV de suporte, como as seguintes:

- <xref:System.Security.Cryptography.CngProvider>mantém um provedor de armazenamento chave.

- <xref:System.Security.Cryptography.CngAlgorithm>mantém um algoritmo de GNV.

- <xref:System.Security.Cryptography.CngProperty>mantém propriedades-chave freqüentemente usadas.

## <a name="related-topics"></a>Tópicos Relacionados

|Title|Descrição|
|-----------|-----------------|
|[Modelo de criptografia](../../../docs/standard/security/cryptography-model.md)|Descreve como a criptografia é implementada na biblioteca de classe base.|
|[Instruções passo a passo: criando um aplicativo criptográfico](../../../docs/standard/security/walkthrough-creating-a-cryptographic-application.md)|Demonstra tarefas básicas de criptografia e descriptografia.|
|[Configurando classes de criptografia](../../../docs/framework/configure-apps/configure-cryptography-classes.md)|Descreve como mapear nomes de algoritmos para classes criptográficas e mapear identificadores de objetos para um algoritmo criptográfico.|
