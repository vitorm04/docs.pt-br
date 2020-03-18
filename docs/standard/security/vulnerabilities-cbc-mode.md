---
title: Vulnerabilidade de descriptografia CBC
description: Aprenda a detectar e mitigar vulnerabilidades de tempo com descriptografia simétrica do modo Cipher-Block-Chaining (CBC) usando preenchimento.
ms.date: 06/12/2018
author: blowdart
ms.openlocfilehash: 47520ea4c9c7d0ef4d79378c93c6ce1f2ba7dd6d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186091"
---
# <a name="timing-vulnerabilities-with-cbc-mode-symmetric-decryption-using-padding"></a>Vulnerabilidades de temporização com descriptografia simétrica no modo CBC usando preenchimento

A Microsoft acredita que não é mais seguro descriptografar dados criptografados com o modo de criptografia simétrica cipher-block-chaining (CBC) quando o preenchimento verificável foi aplicado sem antes garantir a integridade do texto cifrado, exceto por muito específico Circunstâncias. Este julgamento é baseado em pesquisas criptográficas atualmente conhecidas.

## <a name="introduction"></a>Introdução

Um ataque oracle de preenchimento é um tipo de ataque contra dados criptografados que permite ao invasor descriptografar o conteúdo dos dados, sem saber a chave.

Um oráculo refere-se a um "tell" que dá a um invasor informações sobre se a ação que eles estão executando está correta ou não. Imagine jogar tabuleiro ou jogo de cartas com uma criança. Quando seu rosto se ilumina com um grande sorriso porque eles pensam que estão prestes a fazer uma boa jogada, isso é um oráculo. Você, como oponente, pode usar este oráculo para planejar seu próximo movimento apropriadamente.

Preenchimento é um termo criptográfico específico. Algumas cifras, que são os algoritmos usados para criptografar seus dados, funcionam em blocos de dados onde cada bloco é um tamanho fixo. Se os dados que você deseja criptografar não forem do tamanho certo para preencher os blocos, seus dados são acolchoados até que o faça. Muitas formas de preenchimento exigem que o preenchimento esteja sempre presente, mesmo que a entrada original fosse do tamanho certo. Isso permite que o preenchimento seja sempre removido com segurança após a descriptografia.

Juntando as duas coisas, uma implementação de software com um oráculo de preenchimento revela se os dados descriptografados têm preenchimento válido. O oráculo pode ser algo tão simples quanto devolver um valor que diz "preenchimento inválido" ou algo mais complicado, como tomar um tempo mensuravelmente diferente para processar um bloco válido em vez de um bloco inválido.

As cifras baseadas em blocotêm outra propriedade, chamada mode, que determina a relação dos dados no primeiro bloco com os dados no segundo bloco, e assim por diante. Um dos modos mais utilizados é o CBC. O CBC introduz um bloco aleatório inicial, conhecido como Vetores de Inicialização (IV), e combina o bloco anterior com o resultado da criptografia estática para torná-lo de tal forma que criptografar a mesma mensagem com a mesma chave nem sempre produz a mesma saída criptografada.

Um invasor pode usar um oráculo de preenchimento, em combinação com a forma como os dados CBC são estruturados, para enviar mensagens ligeiramente alteradas para o código que expõe o oráculo, e continuar enviando dados até que o oráculo diga que os dados estão corretos. A partir dessa resposta, o invasor pode descriptografar a mensagem byte byte.

As redes de computadores modernas são de tão alta qualidade que um invasor pode detectar diferenças muito pequenas (menos de 0,1 ms) no tempo de execução em sistemas remotos.Aplicativos que estão assumindo que uma descriptografia bem-sucedida só pode acontecer quando os dados não foram adulterados podem ser vulneráveis a ataques de ferramentas que são projetadas para observar diferenças na descriptografia bem sucedida e mal sucedida. Embora essa diferença de tempo possa ser mais significativa em alguns idiomas ou bibliotecas do que em outros, acredita-se agora que esta é uma ameaça prática para todos os idiomas e bibliotecas quando a resposta do aplicativo à falha é levada em conta.

Este ataque depende da capacidade de alterar os dados criptografados e testar o resultado com o oráculo. A única maneira de mitigar totalmente o ataque é detectar alterações nos dados criptografados e se recusar a executar quaisquer ações nele. A maneira padrão de fazer isso é criar uma assinatura para os dados e validar essa assinatura antes de qualquer operação ser realizada. A assinatura deve ser verificável, não pode ser criada pelo invasor, caso contrário eles alterariam os dados criptografados e então calculariam uma nova assinatura com base nos dados alterados. Um tipo comum de assinatura apropriada é conhecido como um código de autenticação de mensagem com chave hash (HMAC). Um HMAC difere de um checkum em que ele leva uma chave secreta, conhecida apenas para a pessoa que produz o HMAC e para a pessoa que a valida. Sem a posse da chave, você não pode produzir um HMAC correto. Quando você recebe seus dados, você pega os dados criptografados, calcula o HMAC independentemente usando a chave secreta que você e o compartilhamento de remetente, em seguida, comparar o HMAC que eles enviaram com o que você calculou. Esta comparação deve ser tempo constante, caso contrário você adicionou outro oráculo detectável, permitindo um tipo diferente de ataque.

Em resumo, para usar cifras de blocoCBC acolchoadas com segurança, você deve combiná-las com uma verificação de integridade de dados (ou outra verificação de integridade de dados) que você valida usando uma comparação de tempo constante antes de tentar descriptografar os dados. Uma vez que todas as mensagens alteradas levam o mesmo tempo para produzir uma resposta, o ataque é evitado.

## <a name="who-is-vulnerable"></a>Quem é vulnerável

Essa vulnerabilidade se aplica tanto a aplicativos gerenciados quanto aos nativos que estão executando sua própria criptografia e descriptografia. Isso inclui, por exemplo:

- Um aplicativo que criptografa um cookie para descriptografia posterior no servidor.
- Um aplicativo de banco de dados que fornece a capacidade de os usuários inserirem dados em uma tabela cujas colunas são posteriormente descriptografadas.
- Um aplicativo de transferência de dados que depende da criptografia usando uma chave compartilhada para proteger os dados em trânsito.
- Um aplicativo que criptografa e descriptografa mensagens "dentro" do túnel TLS.

Observe que o uso de TLS sozinho pode não protegê-lo nesses cenários.

Uma aplicação vulnerável:

- Descriptografa dados usando o modo de cifra CBC com um modo de preenchimento verificável, como PKCS#7 ou ANSI X.923.
- Realiza a descriptografia sem ter realizado uma verificação de integridade de dados (através de um MAC ou de uma assinatura digital assimétrica).

Isso também se aplica a aplicações construídas em cima de abstrações sobre esses primitivos, como a estrutura de Dados EnvelopedData (PKCS#7/CMS).

## <a name="related-areas-of-concern"></a>Áreas de preocupação relacionadas

Pesquisas levaram a Microsoft a se preocupar ainda mais com as mensagens CBC que são acolchoadas com preenchimento equivalente à ISO 10126 quando a mensagem tem uma estrutura de rodapé bem conhecida ou previsível. Por exemplo, conteúdo preparado as regras da Recomendação de Sintaxe e Processamento de Criptografia W3C XML (xmlenc, EncryptedXml). Embora a orientação do W3C para assinar a mensagem e depois criptografar fosse considerada apropriada na época, a Microsoft agora recomenda sempre fazer o sinal de criptografia em seguida.

Os desenvolvedores de aplicativos devem estar sempre atentos à verificação da aplicabilidade de uma chave de assinatura assimétrica, pois não há relação de confiança inerente entre uma chave assimétrica e uma mensagem arbitrária.

## <a name="details"></a>Detalhes

Historicamente, houve um consenso de que é importante tanto criptografar e autenticar dados importantes, usando meios como assinaturas de HMAC ou RSA. No entanto, houve uma orientação menos clara sobre como sequenciar as operações de criptografia e autenticação. Devido à vulnerabilidade detalhada neste artigo, a orientação da Microsoft agora é usar sempre o paradigma "criptografar-depois-assinar". Ou seja, primeiro criptografe dados usando uma chave simétrica, em seguida, calcule um MAC ou assinatura assimétrica sobre o texto cifrado (dados criptografados). Ao descriptografar dados, execute o inverso. Primeiro, confirme o MAC ou a assinatura do texto cifrado, em seguida, descriptografe-o.

Uma classe de vulnerabilidades conhecidas como "ataques oráculos de preenchimento" são conhecidas por existir em mais de 10 anos. Essas vulnerabilidades permitem que um invasor descriptografe dados criptografados por algoritmos de bloco simétricos, como AES e 3DES, usando não mais do que 4096 tentativas por bloco de dados. Essas vulnerabilidades fazem uso do fato de que as cifras de bloco são mais usadas com dados de preenchimento verificáveis no final. Descobriu-se que se um invasor pode adulterar o texto cifrado e descobrir se a adulteração causou um erro no formato do preenchimento no final, o invasor pode descriptografar os dados.

Inicialmente, os ataques práticos eram baseados em serviços que retornariam diferentes códigos de erro com base em se o preenchimento era válido, como o ASP.NET vulnerabilidade [MS10-070](/security-updates/SecurityBulletins/2010/ms10-070). No entanto, a Microsoft agora acredita que é prático realizar ataques semelhantes usando apenas as diferenças de tempo entre o processamento válido e o preenchimento inválido.

Desde que o esquema de criptografia empregue uma assinatura e que a verificação de assinatura seja realizada com um tempo de execução fixo para um determinado período de dados (independentemente do conteúdo), a integridade dos dados pode ser verificada sem emitir qualquer informação a um invasor através de um [canal lateral](https://en.wikipedia.org/wiki/Side-channel_attack). Uma vez que a verificação de integridade rejeita qualquer mensagem adulterada, a ameaça de preenchimento oráculo é atenuada.

## <a name="guidance"></a>Orientação

Em primeiro lugar, a Microsoft recomenda que todos os dados que têm confidencialidade sejam transmitidos através do TLS (Transport Layer Security, segurança da camada de transporte), o sucessor do Secure Sockets Layer (SSL).

Em seguida, analise sua aplicação para:

- Entenda precisamente qual criptografia você está realizando e que criptografia está sendo fornecida pelas plataformas e APIs que você está usando.
- Certifique-se de que cada uso em cada camada de um algoritmo de cifra de [bloco](https://en.wikipedia.org/wiki/Block_cipher#Notable_block_ciphers)simétrico , como AES e 3DES, no modo CBC incorpore o uso de uma verificação secreta de integridade de dados (uma assinatura assimétrica, um HMAC, ou para alterar o modo de cifra para um modo de [criptografia autenticada](https://en.wikipedia.org/wiki/Authenticated_encryption) (AE), como GCM ou CCM).

Com base na pesquisa atual, acredita-se geralmente que quando as etapas de autenticação e criptografia são executadas independentemente para modos de criptografia não-AE, autenticar o texto cifrado (cripto-então-sinal) é a melhor opção geral. No entanto, não há uma resposta correta para criptografia e essa generalização não é tão boa quanto conselhos direcionados de um criptógrafo profissional.

Aplicativos que não conseguem alterar seu formato de mensagens, mas executam descriptografia CBC não autenticada são encorajados a tentar incorporar mitigações como:

- Descriptografar sem permitir que o decodificador verifique ou remova o preenchimento:
  - Qualquer preenchimento que foi aplicado ainda precisa ser removido ou ignorado, você está movendo o fardo para sua aplicação.
  - A vantagem é que a verificação e remoção do preenchimento podem ser incorporadas em outra lógica de verificação de dados do aplicativo. Se a verificação de preenchimento e verificação de dados puderem ser feitas em tempo constante, a ameaça será reduzida.
  - Uma vez que a interpretação do preenchimento altera o comprimento da mensagem percebida, ainda pode haver informações de tempo emitidas a partir dessa abordagem.
- Alterar o modo de preenchimento de descriptografia para ISO10126:
  - O preenchimento de descriptografia ISO10126 é compatível com o preenchimento de criptografia PKCS7 e com o preenchimento de criptografia ANSIX923.
  - A alteração do modo reduz o preenchimento do conhecimento oráculo para 1 byte em vez de todo o bloco. No entanto, se o conteúdo tiver um rodapé bem conhecido, como um elemento XML de fechamento, os ataques relacionados podem continuar a atacar o resto da mensagem.
  - Isso também não impede a recuperação de texto simples em situações em que o invasor pode coagir o mesmo texto simples a ser criptografado várias vezes com uma troca de mensagens diferente.
- Gate a avaliação de uma chamada de descriptografia para amortecer o sinal de tempo:
  - O cálculo do tempo de espera deve ter um mínimo superior ao tempo máximo que a operação de descriptografia levaria para qualquer segmento de dados que contenha preenchimento.
  - Os cálculos de tempo devem ser feitos de acordo com a orientação na [aquisição de carimbos de tempo de alta resolução,](/windows/desktop/sysinfo/acquiring-high-resolution-time-stamps)não usando <xref:System.Environment.TickCount?displayProperty=nameWithType> (sujeito a rolagem/estouro) ou subtraindo dois carimbos de tempo do sistema (sujeitos a erros de ajuste ntp).
  - Os cálculos de tempo devem incluir a operação de descriptografia, incluindo todas as exceções potenciais em aplicativos gerenciados ou C++, não apenas acolchoados no final.
  - Se o sucesso ou falha ainda tiver sido determinado, o portão de tempo precisa retornar a falha quando expirar.
- Os serviços que estão realizando descriptografia não autenticada devem ter monitoramento para detectar que uma enxurrada de mensagens "inválidas" chegou.
  - Tenha em mente que este sinal carrega tanto falsos positivos (dados legitimamente corrompidos) quanto falsos negativos (espalhando o ataque por um tempo suficientemente longo para escapar da detecção).

## <a name="finding-vulnerable-code---native-applications"></a>Encontrar código vulnerável - aplicativos nativos

Para programas construídos contra a biblioteca Windows Cryptography: Next Generation (CNG):

- A chamada de descriptografia é para [BCryptDecrypt](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptdecrypt), especificando o `BCRYPT_BLOCK_PADDING` sinalizador.
- A alça-chave foi inicializada chamando [BCryptSetProperty](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptsetproperty) com [BCRYPT_CHAINING_MODE](/windows/desktop/SecCNG/cng-property-identifiers#BCRYPT_CHAINING_MODE) definido como `BCRYPT_CHAIN_MODE_CBC`.
  - Uma `BCRYPT_CHAIN_MODE_CBC` vez que é o padrão, o `BCRYPT_CHAINING_MODE`código afetado pode não ter atribuído nenhum valor para .

Para programas construídos contra a API criptográfica mais antiga do Windows:

- A chamada de descriptografia é `Final=TRUE`para [CryptDecrypt](/windows/desktop/api/wincrypt/nf-wincrypt-cryptdecrypt) com .
- A alça-chave foi inicializada chamando [CryptSetKeyParam](/windows/desktop/api/wincrypt/nf-wincrypt-cryptsetkeyparam) com [KP_MODE](/windows/desktop/api/wincrypt/nf-wincrypt-cryptgetkeyparam) definido como `CRYPT_MODE_CBC`.
  - Uma `CRYPT_MODE_CBC` vez que é o padrão, o `KP_MODE`código afetado pode não ter atribuído nenhum valor para .

## <a name="finding-vulnerable-code---managed-applications"></a>Encontrar código vulnerável - aplicativos gerenciados

- A chamada de descriptografia <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor> <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor(System.Byte[],System.Byte[])> é para <xref:System.Security.Cryptography.SymmetricAlgorithm?displayProperty=nameWithType>o ou métodos em .
  - Isso inclui os seguintes tipos derivados dentro do .NET, mas também pode incluir tipos de terceiros:
    - <xref:System.Security.Cryptography.Aes>
    - <xref:System.Security.Cryptography.AesCng>
    - <xref:System.Security.Cryptography.AesCryptoServiceProvider>
    - <xref:System.Security.Cryptography.AesManaged>
    - <xref:System.Security.Cryptography.DES>
    - <xref:System.Security.Cryptography.DESCryptoServiceProvider>
    - <xref:System.Security.Cryptography.RC2>
    - <xref:System.Security.Cryptography.RC2CryptoServiceProvider>
    - <xref:System.Security.Cryptography.Rijndael>
    - <xref:System.Security.Cryptography.RijndaelManaged>
    - <xref:System.Security.Cryptography.TripleDES>
    - <xref:System.Security.Cryptography.TripleDESCng>
    - <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider>
- A <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> propriedade foi <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType> <xref:System.Security.Cryptography.PaddingMode.ANSIX923?displayProperty=nameWithType>definida <xref:System.Security.Cryptography.PaddingMode.ISO10126?displayProperty=nameWithType>para, ou .
  - Uma <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType> vez que é o padrão, <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> o código afetado pode nunca ter atribuído a propriedade.
- A <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> propriedade foi definida para<xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType>
  - Uma <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType> vez que é o padrão, <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> o código afetado pode nunca ter atribuído a propriedade.

## <a name="finding-vulnerable-code---cryptographic-message-syntax"></a>Encontrar código vulnerável - sintaxe de mensagens criptográficas

Uma mensagem CMS EnvelopedData não autenticada cujo conteúdo criptografado usa o modo CBC de AES (2.16.840.1.101.3.4.1.2, 2.16.840.1.101.3.4.1.22, 2.16.840.1.101.3.4.1.42), DES (1.3.14.3.2.7), 3DES (1.2.840.113549.3.7) ou RC2 (1.2.840.113549.3.2) é rc2 (1.2.840.113549.3.2) é rc2 (1.2.840.113549.3.2) é rc2 (1.2.840.113549.3.2) é vulneráveis, bem como mensagens usando quaisquer outros algoritmos de cifra de bloco no modo CBC.

Embora as cifras de fluxo não sejam suscetíveis a essa vulnerabilidade em particular, a Microsoft recomenda sempre autenticar os dados ao inspecionar o valor do ContentEncryptionAlgorithm.

Para aplicações gerenciadas, uma bolha CMS EnvelopedData pode ser detectada <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.Decode(System.Byte[])?displayProperty=fullName>como qualquer valor que seja passado para .

Para aplicações nativas, uma bolha CMS EnvelopedData pode ser detectada como qualquer valor fornecido a uma [CMSG_TYPE_PARAM](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsggetparam) alça `CMSG_ENVELOPED` CMS via [CryptMsgUpdate](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgupdate) cuja CMSG_TYPE_PARAM resultante é e/ou a alça CMS é posteriormente enviada uma `CMSG_CTRL_DECRYPT` instrução via [CryptMsgControl](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgcontrol).

## <a name="vulnerable-code-example---managed"></a>Exemplo de código vulnerável - gerenciado

Este método lê um cookie e descriptografa-o e nenhuma verificação de integridade de dados é visível. Portanto, o conteúdo de um cookie lido por este método pode ser atacado pelo usuário que o recebeu, ou por qualquer invasor que tenha obtido o valor do cookie criptografado.

```csharp
private byte[] DecryptCookie(string cookieName)
{
    HttpCookie cookie = Request.Cookies[cookieName];

    if (cookie == null)
    {
        return null;
    }

    using (ICryptoTransform decryptor = _aes.CreateDecryptor())
    using (MemoryStream memoryStream = new MemoryStream())
    using (CryptoStream cryptoStream =
        new CryptoStream(memoryStream, decryptor, CryptoStreamMode.Write))
    {
        byte[] readCookie = Convert.FromBase64String(cookie.Value);
        cryptoStream.Write(readCookie, 0, readCookie.Length);
        cryptoStream.FlushFinalBlock();
        return memoryStream.ToArray();
    }
}
```

## <a name="example-code-following-recommended-practices---managed"></a>Exemplo de código seguindo práticas recomendadas - gerenciado

O código de amostra a seguir usa um formato de mensagem não padrão de

`cipher_algorithm_id || hmac_algorithm_id || hmac_tag || iv || ciphertext`

onde `cipher_algorithm_id` os `hmac_algorithm_id` identificadores e algoritmos são representações locais de aplicação (não padrão) desses algoritmos. Esses identificadores podem fazer sentido em outras partes do seu protocolo de mensagens existente, em vez de como um bytestream concatenado.

Este exemplo também usa uma única chave mestra para derivar uma chave de criptografia e uma chave HMAC. Isso é fornecido tanto como uma conveniência para transformar um aplicativo com chave singly em um aplicativo com duas chaves, quanto para incentivar a manutenção das duas chaves como valores diferentes. Ele ainda garante que a chave HMAC e a chave de criptografia não podem sair da sincronização.

Esta amostra não aceita <xref:System.IO.Stream> um para criptografia ou descriptografia. O formato de dados atual dificulta `hmac_tag` a criptografia de um passe porque o valor precede o texto cifrado. No entanto, este formato foi escolhido porque mantém todos os elementos de tamanho fixo no início para manter o analisador mais simples. Com esse formato de dados, é possível descriptografar um passe, embora um implementador seja advertido a ligar para getHashAndReset e verificar o resultado antes de chamar TransformFinalBlock. Se a criptografia de streaming é importante, então um modo AE diferente pode ser necessário.

```csharp
// ==++==
//
//   Copyright (c) Microsoft Corporation.  All rights reserved.
//
//   Shared under the terms of the Microsoft Public License,
//   https://opensource.org/licenses/MS-PL
//
// ==--==

using System;
using System.Diagnostics;
using System.IO;
using System.Runtime.CompilerServices;
using System.Security.Cryptography;

namespace Microsoft.Examples.Cryptography
{
    public enum AeCipher : byte
    {
        Unknown,
        Aes256CbcPkcs7,
    }

    public enum AeMac : byte
    {
        Unknown,
        HMACSHA256,
        HMACSHA384,
    }

    /// <summary>
    /// Provides extension methods to make HashAlgorithm look like .NET Core's
    /// IncrementalHash
    /// </summary>
    internal static class IncrementalHashExtensions
    {
        public static void AppendData(this HashAlgorithm hash, byte[] data)
        {
            hash.TransformBlock(data, 0, data.Length, null, 0);
        }

        public static void AppendData(
            this HashAlgorithm hash,
            byte[] data,
            int offset,
            int length)
        {
            hash.TransformBlock(data, offset, length, null, 0);
        }

        public static byte[] GetHashAndReset(this HashAlgorithm hash)
        {
            hash.TransformFinalBlock(Array.Empty<byte>(), 0, 0);
            return hash.Hash;
        }
    }

    public static partial class AuthenticatedEncryption
    {
        /// <summary>
        /// Use <paramref name="masterKey"/> to derive two keys (one cipher, one HMAC)
        /// to provide authenticated encryption for <paramref name="message"/>.
        /// </summary>
        /// <param name="masterKey">The master key from which other keys derive.</param>
        /// <param name="message">The message to encrypt</param>
        /// <returns>
        /// A concatenation of
        /// [cipher algorithm+chainmode+padding][mac algorithm][authtag][IV][ciphertext],
        /// suitable to be passed to <see cref="Decrypt"/>.
        /// </returns>
        /// <remarks>
        /// <paramref name="masterKey"/> should be a 128-bit (or bigger) value generated
        /// by a secure random number generator, such as the one returned from
        /// <see cref="RandomNumberGenerator.Create()"/>.
        /// This implementation chooses to block deficient inputs by length, but does not
        /// make any attempt at discerning the randomness of the key.
        ///
        /// If the master key is being input by a prompt (like a password/passphrase)
        /// then it should be properly turned into keying material via a Key Derivation
        /// Function like PBKDF2, represented by Rfc2898DeriveBytes. A 'password' should
        /// never be simply turned to bytes via an Encoding class and used as a key.
        /// </remarks>
        public static byte[] Encrypt(byte[] masterKey, byte[] message)
        {
            if (masterKey == null)
                throw new ArgumentNullException(nameof(masterKey));
            if (masterKey.Length < 16)
                throw new ArgumentOutOfRangeException(
                    nameof(masterKey),
                    "Master Key must be at least 128 bits (16 bytes)");
            if (message == null)
                throw new ArgumentNullException(nameof(message));

            // First, choose an encryption scheme.
            AeCipher aeCipher = AeCipher.Aes256CbcPkcs7;

            // Second, choose an authentication (message integrity) scheme.
            //
            // In this example we use the master key length to change from HMACSHA256 to
            // HMACSHA384, but that is completely arbitrary. This mostly represents a
            // "cryptographic needs change over time" scenario.
            AeMac aeMac = masterKey.Length < 48 ? AeMac.HMACSHA256 : AeMac.HMACSHA384;

            // It's good to be able to identify what choices were made when a message was
            // encrypted, so that the message can later be decrypted. This allows for
            // future versions to add support for new encryption schemes, but still be
            // able to read old data. A practice known as "cryptographic agility".
            //
            // This is similar in practice to PKCS#7 messaging, but this uses a
            // private-scoped byte rather than a public-scoped Object IDentifier (OID).
            // Please note that the scheme in this example adheres to no particular
            // standard, and is unlikely to survive to a more complete implementation in
            // the .NET Framework.
            //
            // You may be well-served by prepending a version number byte to this
            // message, but may want to avoid the value 0x30 (the leading byte value for
            // DER-encoded structures such as X.509 certificates and PKCS#7 messages).
            byte[] algorithmChoices = { (byte)aeCipher, (byte)aeMac };
            byte[] iv;
            byte[] cipherText;
            byte[] tag;

            // Using our algorithm choices, open an HMAC (as an authentication tag
            // generator) and a SymmetricAlgorithm which use different keys each derived
            // from the same master key.
            //
            // A custom implementation may very well have distinctly managed secret keys
            // for the MAC and cipher, this example merely demonstrates the master to
            // derived key methodology to encourage key separation from the MAC and
            // cipher keys.
            using (HMAC tagGenerator = GetMac(aeMac, masterKey))
            {
                using (SymmetricAlgorithm cipher = GetCipher(aeCipher, masterKey))
                using (ICryptoTransform encryptor = cipher.CreateEncryptor())
                {
                    // Since no IV was provided, a random one has been generated
                    // during the call to CreateEncryptor.
                    //
                    // But note that it only does the auto-generation once. If the cipher
                    // object were used again, a call to GenerateIV would have been
                    // required.
                    iv = cipher.IV;

                    cipherText = Transform(encryptor, message, 0, message.Length);
                }

                // The IV and ciphertest both need to be included in the MAC to prevent
                // tampering.
                //
                // By including the algorithm identifiers, we have technically moved from
                // simple Authenticated Encryption (AE) to Authenticated Encryption with
                // Additional Data (AEAD). By including the algorithm identifiers in the
                // MAC, it becomes harder for an attacker to change them as an attempt to
                // perform a downgrade attack.
                //
                // If you've added a data format version field, it can also be included
                // in the MAC to further inhibit an attacker's options for confusing the
                // data processor into believing the tampered message is valid.
                tagGenerator.AppendData(algorithmChoices);
                tagGenerator.AppendData(iv);
                tagGenerator.AppendData(cipherText);
                tag = tagGenerator.GetHashAndReset();
            }

            // Build the final result as the concatenation of everything except the keys.
            int totalLength =
                algorithmChoices.Length +
                tag.Length +
                iv.Length +
                cipherText.Length;

            byte[] output = new byte[totalLength];
            int outputOffset = 0;

            Append(algorithmChoices, output, ref outputOffset);
            Append(tag, output, ref outputOffset);
            Append(iv, output, ref outputOffset);
            Append(cipherText, output, ref outputOffset);

            Debug.Assert(outputOffset == output.Length);
            return output;
        }

        /// <summary>
        /// Reads a message produced by <see cref="Encrypt"/> after verifying it hasn't
        /// been tampered with.
        /// </summary>
        /// <param name="masterKey">The master key from which other keys derive.</param>
        /// <param name="cipherText">
        /// The output of <see cref="Encrypt"/>: a concatenation of a cipher ID, mac ID,
        /// authTag, IV, and cipherText.
        /// </param>
        /// <returns>The decrypted content.</returns>
        /// <exception cref="ArgumentNullException">
        /// <paramref name="masterKey"/> is <c>null</c>.
        /// </exception>
        /// <exception cref="ArgumentNullException">
        /// <paramref name="cipherText"/> is <c>null</c>.
        /// </exception>
        /// <exception cref="CryptographicException">
        /// <paramref name="cipherText"/> identifies unknown algorithms, is not long
        /// enough, fails a data integrity check, or fails to decrypt.
        /// </exception>
        /// <remarks>
        /// <paramref name="masterKey"/> should be a 128-bit (or larger) value
        /// generated by a secure random number generator, such as the one returned from
        /// <see cref="RandomNumberGenerator.Create()"/>. This implementation chooses to
        /// block deficient inputs by length, but doesn't make any attempt at
        /// discerning the randomness of the key.
        ///
        /// If the master key is being input by a prompt (like a password/passphrase),
        /// then it should be properly turned into keying material via a Key Derivation
        /// Function like PBKDF2, represented by Rfc2898DeriveBytes. A 'password' should
        /// never be simply turned to bytes via an Encoding class and used as a key.
        /// </remarks>
        public static byte[] Decrypt(byte[] masterKey, byte[] cipherText)
        {
            // This example continues the .NET practice of throwing exceptions for
            // failures. If you consider message tampering to be normal (and thus
            // "not exceptional") behavior, you may like the signature
            // bool Decrypt(byte[] messageKey, byte[] cipherText, out byte[] message)
            // better.
            if (masterKey == null)
                throw new ArgumentNullException(nameof(masterKey));
            if (masterKey.Length < 16)
                throw new ArgumentOutOfRangeException(
                    nameof(masterKey),
                    "Master Key must be at least 128 bits (16 bytes)");
            if (cipherText == null)
                throw new ArgumentNullException(nameof(cipherText));

            // The format of this message is assumed to be public, so there's no harm in
            // saying ahead of time that the message makes no sense.
            if (cipherText.Length < 2)
            {
                throw new CryptographicException();
            }

            // Use the message algorithm headers to determine what cipher algorithm and
            // MAC algorithm are going to be used. Since the same Key Derivation
            // Functions (KDFs) are being used in Decrypt as Encrypt, the keys are also
            // the same.
            AeCipher aeCipher = (AeCipher)cipherText[0];
            AeMac aeMac = (AeMac)cipherText[1];

            using (SymmetricAlgorithm cipher = GetCipher(aeCipher, masterKey))
            using (HMAC tagGenerator = GetMac(aeMac, masterKey))
            {
                int blockSizeInBytes = cipher.BlockSize / 8;
                int tagSizeInBytes = tagGenerator.HashSize / 8;
                int headerSizeInBytes = 2;
                int tagOffset = headerSizeInBytes;
                int ivOffset = tagOffset + tagSizeInBytes;
                int cipherTextOffset = ivOffset + blockSizeInBytes;
                int cipherTextLength = cipherText.Length - cipherTextOffset;
                int minLen = cipherTextOffset + blockSizeInBytes;

                // Again, the minimum length is still assumed to be public knowledge,
                // nothing has leaked out yet. The minimum length couldn't just be calculated
                // without reading the header.
                if (cipherText.Length < minLen)
                {
                    throw new CryptographicException();
                }

                // It's very important that the MAC be calculated and verified before
                // proceeding to decrypt the ciphertext, as this prevents any sort of
                // information leaking out to an attacker.
                //
                // Don't include the tag in the calculation, though.

                // First, everything before the tag (the cipher and MAC algorithm ids)
                tagGenerator.AppendData(cipherText, 0, tagOffset);

                // Skip the data before the tag and the tag, then read everything that
                // remains.
                tagGenerator.AppendData(
                    cipherText,
                    tagOffset + tagSizeInBytes,
                    cipherText.Length - tagSizeInBytes - tagOffset);

                byte[] generatedTag = tagGenerator.GetHashAndReset();

                // The time it took to get to this point has so far been a function only
                // of the length of the data, or of non-encrypted values (e.g. it could
                // take longer to prepare the *key* for the HMACSHA384 MAC than the
                // HMACSHA256 MAC, but the algorithm choice wasn't a secret).
                //
                // If the verification of the authentication tag aborts as soon as a
                // difference is found in the byte arrays then your program may be
                // acting as a timing oracle which helps an attacker to brute-force the
                // right answer for the MAC. So, it's very important that every possible
                // "no" (2^256-1 of them for HMACSHA256) be evaluated in as close to the
                // same amount of time as possible. For this, we call CryptographicEquals
                if (!CryptographicEquals(
                    generatedTag,
                    0,
                    cipherText,
                    tagOffset,
                    tagSizeInBytes))
                {
                    // Assuming every tampered message (of the same length) took the same
                    // amount of time to process, we can now safely say
                    // "this data makes no sense" without giving anything away.
                    throw new CryptographicException();
                }

                // Restore the IV into the symmetricAlgorithm instance.
                byte[] iv = new byte[blockSizeInBytes];
                Buffer.BlockCopy(cipherText, ivOffset, iv, 0, iv.Length);
                cipher.IV = iv;

                using (ICryptoTransform decryptor = cipher.CreateDecryptor())
                {
                    return Transform(
                        decryptor,
                        cipherText,
                        cipherTextOffset,
                        cipherTextLength);
                }
            }
        }

        private static byte[] Transform(
            ICryptoTransform transform,
            byte[] input,
            int inputOffset,
            int inputLength)
        {
            // Many of the implementations of ICryptoTransform report true for
            // CanTransformMultipleBlocks, and when the entire message is available in
            // one shot this saves on the allocation of the CryptoStream and the
            // intermediate structures it needs to properly chunk the message into blocks
            // (since the underlying stream won't always return the number of bytes
            // needed).
            if (transform.CanTransformMultipleBlocks)
            {
                return transform.TransformFinalBlock(input, inputOffset, inputLength);
            }

            // If our transform couldn't do multiple blocks at once, let CryptoStream
            // handle the chunking.
            using (MemoryStream messageStream = new MemoryStream())
            using (CryptoStream cryptoStream =
                new CryptoStream(messageStream, transform, CryptoStreamMode.Write))
            {
                cryptoStream.Write(input, inputOffset, inputLength);
                cryptoStream.FlushFinalBlock();
                return messageStream.ToArray();
            }
        }

        /// <summary>
        /// Open a properly configured <see cref="SymmetricAlgorithm"/> conforming to the
        /// scheme identified by <paramref name="aeCipher"/>.
        /// </summary>
        /// <param name="aeCipher">The cipher mode to open.</param>
        /// <param name="masterKey">The master key from which other keys derive.</param>
        /// <returns>
        /// A SymmetricAlgorithm object with the right key, cipher mode, and padding
        /// mode; or <c>null</c> on unknown algorithms.
        /// </returns>
        private static SymmetricAlgorithm GetCipher(AeCipher aeCipher, byte[] masterKey)
        {
            SymmetricAlgorithm symmetricAlgorithm;

            switch (aeCipher)
            {
                case AeCipher.Aes256CbcPkcs7:
                    symmetricAlgorithm = Aes.Create();
                    // While 256-bit, CBC, and PKCS7 are all the default values for these
                    // properties, being explicit helps comprehension more than it hurts
                    // performance.
                    symmetricAlgorithm.KeySize = 256;
                    symmetricAlgorithm.Mode = CipherMode.CBC;
                    symmetricAlgorithm.Padding = PaddingMode.PKCS7;
                    break;
                default:
                    // An algorithm we don't understand
                    throw new CryptographicException();
            }

            // Instead of using the master key directly, derive a key for our chosen
            // HMAC algorithm based upon the master key.
            //
            // Since none of the symmetric encryption algorithms currently in .NET
            // support key sizes greater than 256-bit, we can use HMACSHA256 with
            // NIST SP 800-108 5.1 (Counter Mode KDF) to derive a value that is
            // no smaller than the key size, then Array.Resize to trim it down as
            // needed.

            using (HMAC hmac = new HMACSHA256(masterKey))
            {
                // i=1, Label=ASCII(cipher)
                byte[] cipherKey = hmac.ComputeHash(
                    new byte[] { 1, 99, 105, 112, 104, 101, 114 });

                // Resize the array to the desired keysize. KeySize is in bits,
                // and Array.Resize wants the length in bytes.
                Array.Resize(ref cipherKey, symmetricAlgorithm.KeySize / 8);

                symmetricAlgorithm.Key = cipherKey;
            }

            return symmetricAlgorithm;
        }

        /// <summary>
        /// Open a properly configured <see cref="HMAC"/> conforming to the scheme
        /// identified by <paramref name="aeMac"/>.
        /// </summary>
        /// <param name="aeMac">The message authentication mode to open.</param>
        /// <param name="masterKey">The master key from which other keys derive.</param>
        /// <returns>
        /// An HMAC object with the proper key, or <c>null</c> on unknown algorithms.
        /// </returns>
        private static HMAC GetMac(AeMac aeMac, byte[] masterKey)
        {
            HMAC hmac;

            switch (aeMac)
            {
                case AeMac.HMACSHA256:
                    hmac = new HMACSHA256();
                    break;
                case AeMac.HMACSHA384:
                    hmac = new HMACSHA384();
                    break;
                default:
                    // An algorithm we don't understand
                    throw new CryptographicException();
            }

            // Instead of using the master key directly, derive a key for our chosen
            // HMAC algorithm based upon the master key.
            // Since the output size of the HMAC is the same as the ideal key size for
            // the HMAC, we can use the master key over a fixed input once to perform
            // NIST SP 800-108 5.1 (Counter Mode KDF):
            hmac.Key = masterKey;

            // i=1, Context=ASCII(MAC)
            byte[] newKey = hmac.ComputeHash(new byte[] { 1, 77, 65, 67 });

            hmac.Key = newKey;
            return hmac;
        }

        // A simple helper method to ensure that the offset (writePos) always moves
        // forward with new data.
        private static void Append(byte[] newData, byte[] combinedData, ref int writePos)
        {
            Buffer.BlockCopy(newData, 0, combinedData, writePos, newData.Length);
            writePos += newData.Length;
        }

        /// <summary>
        /// Compare the contents of two arrays in an amount of time which is only
        /// dependent on <paramref name="length"/>.
        /// </summary>
        /// <param name="a">An array to compare to <paramref name="b"/>.</param>
        /// <param name="aOffset">
        /// The starting position within <paramref name="a"/> for comparison.
        /// </param>
        /// <param name="b">An array to compare to <paramref name="a"/>.</param>
        /// <param name="bOffset">
        /// The starting position within <paramref name="b"/> for comparison.
        /// </param>
        /// <param name="length">
        /// The number of bytes to compare between <paramref name="a"/> and
        /// <paramref name="b"/>.</param>
        /// <returns>
        /// <c>true</c> if both <paramref name="a"/> and <paramref name="b"/> have
        /// sufficient length for the comparison and all of the applicable values are the
        /// same in both arrays; <c>false</c> otherwise.
        /// </returns>
        /// <remarks>
        /// An "insufficient data" <c>false</c> response can happen early, but otherwise
        /// a <c>true</c> or <c>false</c> response take the same amount of time.
        /// </remarks>
        [MethodImpl(MethodImplOptions.NoInlining | MethodImplOptions.NoOptimization)]
        private static bool CryptographicEquals(
            byte[] a,
            int aOffset,
            byte[] b,
            int bOffset,
            int length)
        {
            Debug.Assert(a != null);
            Debug.Assert(b != null);
            Debug.Assert(length >= 0);

            int result = 0;

            if (a.Length - aOffset < length || b.Length - bOffset < length)
            {
                return false;
            }

            unchecked
            {
                for (int i = 0; i < length; i++)
                {
                    // Bitwise-OR of subtraction has been found to have the most
                    // stable execution time.
                    //
                    // This cannot overflow because bytes are 1 byte in length, and
                    // result is 4 bytes.
                    // The OR propagates all set bytes, so the differences are only
                    // present in the lowest byte.
                    result = result | (a[i + aOffset] - b[i + bOffset]);
                }
            }

            return result == 0;
        }
    }
}
```
