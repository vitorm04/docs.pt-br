---
title: Vulnerabilidades de tempo com a descriptografia simétrica de modo CBC usando preenchimento
description: Saiba como detectar e reduzir as vulnerabilidades de tempo com a descriptografia simétrica de modo de encadeamento de blocos de codificação (CBC) usando o preenchimento.
ms.date: 06/12/2018
author: blowdart
ms.author: mairaw
ms.openlocfilehash: 26f4d19f591ac02d792bebbd648e90b07d84de56
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208679"
---
# <a name="timing-vulnerabilities-with-cbc-mode-symmetric-decryption-using-padding"></a>Vulnerabilidades de tempo com a descriptografia simétrica de modo CBC usando preenchimento

A Microsoft acredita que não é seguro descriptografar dados criptografados com o encadeamento de blocos de codificação modo CBC () de criptografia simétrica quando preenchimento verificável tiver sido aplicado sem primeiro garantir a integridade do texto codificado, exceto para muito específica circunstâncias. Este julgamento baseia-se a pesquisa de criptografia conhecida no momento. 

## <a name="introduction"></a>Introdução

Um ataque de preenchimento oracle é um tipo de ataque contra os dados criptografados que permite que o invasor descriptografar o conteúdo dos dados, sem conhecer a chave.

Um oracle se refere a um "dizer" que fornece um invasor saber se a ação que está executando está correta ou não. Imagine um tabuleiro de jogo ou da placa de jogo com um filho. Quando sua face acende com um grande Smiley porque ela acha que ela está prestes a fazer um bom movimento, que é um oracle. Você, como o adversário, pode usar esse oracle para planejar próximo movimento adequadamente.

O preenchimento é um termo específico de criptografia. Algumas codificações, que são os algoritmos usados para criptografar os dados, trabalhar em blocos de dados onde cada bloco é um tamanho fixo. Se os dados que você deseja criptografar não o tamanho certo para preencher os blocos, seus dados são preenchidos até que ele faz. Muitos formulários de preenchimento exigem que o preenchimento sempre esteja presente, mesmo se a entrada original era do tamanho correto. Isso permite que o preenchimento deve sempre ser removido com segurança após a descriptografia.

Reunindo os dois pontos, uma implementação de software com um oracle preenchimento revela se dados descriptografados tem preenchimento válido. O oracle pode ser algo simples, como retornar um valor que diz "Preenchimento inválido" ou algo mais complicado como tirar uma hora diferente, para processar um bloco válido em vez de um bloco inválido.

Codificações de bloco de outra propriedade, chamada de modo, o que determina a relação de dados no primeiro bloco para os dados no segundo bloco, e assim por diante. Um dos modos mais comumente usados é CBC. CBC apresenta um bloco aleatório inicial, conhecido como o vetor de inicialização (IV) e combina o bloco anterior com o resultado da criptografia estática para torná-lo, de modo que criptografar a mesma mensagem com a mesma chave sempre não produzem a mesma saída criptografada.

Um invasor pode usar um oracle preenchimento, em combinação com como CBC dados são estruturados, para enviar mensagens ligeiramente alteradas para o código que expõe o oracle e manter envio de dados até que o oracle informa os dados estão corretos. Dessa resposta, o invasor pode descriptografar a mensagem byte por byte.

Redes de computador modernos são de tal alta qualidade que um invasor pode detectar muito pequenas (menos de 0,1 ms) tempo de diferenças em execução em sistemas remotos. Aplicativos que supondo que uma descriptografia bem-sucedida só pode acontecer quando os dados não foram violados podem ser vulneráveis a ataques de ferramentas que são projetadas para observar as diferenças na descriptografia com e sem êxito. Essa diferença de tempo pode ser mais significativa em alguns idiomas ou bibliotecas do que outras pessoas, agora se acredita que se trata de uma ameaça prática para todos os idiomas e bibliotecas quando a resposta do aplicativo a falha é levada em conta.

Esse ataque se baseia na capacidade de alterar os dados criptografados e testar o resultado com o oracle. É a única maneira de reduzir totalmente o ataque de detectar alterações aos dados criptografados e recusar executar quaisquer ações sobre ela. O modo padrão para fazer isso é criar uma assinatura para os dados e validar a assinatura antes de todas as operações são executadas. A assinatura deve ser verificada, ele não pode ser criado, o invasor, caso contrário, eles seriam alterar os dados criptografados e uma nova assinatura com base nos dados alterados de computação. Um tipo comum de assinatura apropriada é conhecido como um código de autenticação de mensagem de hash com chave (HMAC). Um HMAC é diferente de uma soma de verificação, que leva a uma chave secreta, conhecida somente para a pessoa que gera o HMAC e para a pessoa validá-lo. Sem posse da chave, você não pode produzir um HMAC correto. Quando você receber seus dados, deve levar os dados criptografados, independentemente de computação o HMAC usando a chave secreta você e o compartilhamento de remetente e a comparação computado o HMAC eles enviado em relação a um. Essa comparação deve ser constante tempo, caso contrário, você adicionou outro oracle detectável, permitindo que um tipo diferente de ataque.

Em resumo, usar preenchidas CBC codificações em bloco com segurança, você deve combiná-los com um HMAC (ou outra verificação de integridade de dados) que você validar usando uma comparação de tempo constante antes de tentar descriptografar os dados. Desde que todas as mensagens alteradas levam a mesma quantidade de tempo para produzir uma resposta, o ataque é impedido.

## <a name="who-is-vulnerable"></a>Quem é vulnerável

Essa vulnerabilidade se aplica a aplicativos gerenciados e nativos que estão executando seu próprio criptografia e descriptografia. Isso inclui, por exemplo:

- Um aplicativo que criptografa um cookie para descriptografia mais recente no servidor.
- Um aplicativo de banco de dados que fornece a capacidade dos usuários inserir dados em uma tabela cujas colunas são descriptografados posteriormente.
- Um aplicativo de transferência de dados que se baseia em criptografia usando uma chave compartilhada para proteger os dados em trânsito.
- Um aplicativo que criptografa e descriptografa mensagens "internos" o túnel TLS.

Observe que usar TLS sozinho pode não proteger você nesses cenários.

Um aplicativo vulnerável:

- Descriptografa os dados usando o modo de codificação CBC com um modo de preenchimento verificável, como PKCS #7 ou X.923 ANSI.
- Executa a descriptografia sem ter executado uma verificação de integridade de dados (por meio de um MAC ou uma assinatura digital assimétrica).

Isso também se aplica a aplicativos criados sobre abstrações sobre esses primitivos, como a estrutura de EnvelopedData sintaxe de mensagem criptografada (PKCS #7/CMS).

## <a name="related-areas-of-concern"></a>Relacionados áreas de interesse

Pesquisa levou Microsoft ainda mais se preocupar com as mensagens de CBC são preenchidas com preenchimento quando a mensagem tem uma estrutura bem conhecido ou previsível rodapé 10126 ISO equivalente. Por exemplo, conteúdo preparado com as regras da sintaxe de criptografia do W3C XML e recomendação de processamento (xmlenc, EncryptedXml). Embora a orientação do W3C para assinar a mensagem, em seguida, criptografar foi considerada apropriada no momento, a Microsoft recomenda agora sempre fazendo logon criptografar, em seguida.

Os desenvolvedores de aplicativos devem estar sempre atentos ao verificar a aplicabilidade de uma chave de assinatura assimétrica, pois não há nenhuma relação de confiança inerente entre uma chave assimétrica e uma mensagem arbitrária.

## <a name="details"></a>Detalhes

Historicamente, tem sido consenso é importante criptografar e autenticar dados importantes, usando meios, como assinaturas HMAC ou RSA. No entanto, houve menos orientação clara sobre como sequenciar as operações de criptografia e autenticação. Devido à vulnerabilidade de detalhadas neste artigo, diretrizes da Microsoft é usar sempre o paradigma "criptografar-then-sign". Ou seja, primeiro criptografar dados usando uma chave simétrica e computa um MAC ou a assinatura assimétrica sobre o texto cifrado (dados criptografados). Quando a descriptografia de dados, execute o inverso. Primeiro, confirme o endereço MAC ou assinatura do texto codificado e descriptografá-lo.

Uma classe de vulnerabilidades conhecidas como "preenchimento oracle ataques" comprovadamente existe há mais de 10 anos. Essas vulnerabilidades permitem que um invasor descriptografar dados criptografados por algoritmos de bloco simétrico, como AES e 3DES, usar não mais do que 4096 tentativas por um bloco de dados. Essas vulnerabilidades fazer uso do fato de que bloqueiam as codificações são usados com mais frequência com dados de preenchimento verificável no final. Foi encontrado que, se um invasor pode violar o texto cifrado e descobrir se a violação causou um erro no formato de preenchimento no final, o invasor poderá descriptografar os dados.

Inicialmente, ataques práticos baseadas nos serviços que retornam os códigos de erro diferentes com base em se preenchimento foi válido, como a vulnerabilidade do ASP.NET [MS10-070](https://technet.microsoft.com/library/security/ms10-070.aspx). No entanto, a Microsoft agora acredita que é prático conduzir ataques semelhantes usando apenas as diferenças no intervalo entre processamento preenchimento válido e inválido.

Contanto que o esquema de criptografia emprega uma assinatura e que a verificação da assinatura é executada com um tempo de execução fixo para um determinado comprimento de dados (independentemente do conteúdo), a integridade dos dados pode ser verificada sem emitir todas as informações para um o invasor por meio de um [canal do lado do](https://en.wikipedia.org/wiki/Side-channel_attack). Desde que a verificação de integridade rejeita qualquer mensagem violada, a ameaça de oracle preenchimento é reduzida.

## <a name="guidance"></a>Diretrizes

Primeiramente, a Microsoft recomenda que todos os dados que tem a confidencialidade precisam ser transmitidos pela segurança TLS (Transport Layer), o sucessor ao protocolo (SSL).

Em seguida, analise seu aplicativo:

- Compreenda precisamente o que estiver executando a criptografia e que a criptografia está sendo fornecida, as plataformas e APIs que você está usando.
- Ter certeza de que cada uso em cada camada de um simétrica [algoritmo de codificação de bloco](https://en.wikipedia.org/wiki/Block_cipher#Notable_block_ciphers), como AES e 3DES, no modo CBC incorporar o uso de uma verificação de integridade de dados com a chave secreta (uma assinatura assimétrica, um HMAC, ou para alterar o modo de codificação para um [autenticado criptografia](https://en.wikipedia.org/wiki/Authenticated_encryption) modo (AE) como GCM ou CCM).

Com base na pesquisa atual, acredita-se que, quando as etapas de autenticação e criptografia são executadas de maneira independente para modos de não-AE de criptografia, autenticação do texto cifrado (criptografar-then-entrada) é a melhor opção geral. No entanto, há uma resposta correta se aplicam à criptografia e este generalização não é tão bons quanto direcionado conselhos de um profissional criptógrafo.

Aplicativos que não é possível alterar o formato de mensagens, mas executar descriptografia de CBC não autenticada são incentivados a tentar incorporar atenuações, como:

- Descriptografar sem permitir o descriptografador verificar ou remover preenchimento:
  - O preenchimento que foi aplicado ainda precisa ser removidos ou ignorados, você está movendo a carga em seu aplicativo.
  - A vantagem é que a verificação de preenchimento e remoção podem ser incorporadas em outra lógica de verificação de dados de aplicativo. Se a verificação de preenchimento e a verificação de dados podem ser feitos no horário constante, a ameaça é reduzida.
  - Como a interpretação do preenchimento altera o comprimento da mensagem percebido, pode ainda ser emitidas a partir dessa abordagem de informações de tempo.
- Altere o modo de preenchimento de descriptografia para ISO10126:
  - Preenchimento de descriptografia ISO10126 é compatível com preenchimento de criptografia PKCS7 e ANSIX923 preenchimento de criptografia.
  - Alterando o modo reduz o conhecimento do oracle de preenchimento de 1 byte, em vez do bloco inteiro. No entanto, se o conteúdo tiver um rodapé conhecido, como um elemento XML de fechamento ataques relacionados podem continuar atacar o resto da mensagem.
  - Isso também não impede que a recuperação de texto sem formatação em situações em que o invasor pode forçar o mesmo texto não criptografado a serem criptografados várias vezes com um deslocamento de mensagem diferentes.
- A avaliação de uma chamada de descriptografia para Umedeça o sinal de intervalo de porta:
  - O cálculo de tempo de espera deve ter no mínimo exceder a quantidade máxima de tempo que a operação de descriptografia seria necessário para nenhum segmento de dados que contém o preenchimento.
  - Cálculos de tempo devem ser feitos de acordo com as orientações em [adquirir os carimbos de hora de alta resolução](https://msdn.microsoft.com/library/windows/desktop/dn55340.aspx), não usando <xref:System.Environment.TickCount?displayProperty=nameWithType> (sujeito a roll-over/estouro) ou subtraindo duas carimbos de hora do sistema (sujeitos ao ajuste de NTP erros).
  - Cálculos de tempo devem ser incluindo a operação de descriptografia, incluindo todas as exceções potenciais em gerenciado ou aplicativos do C++, não apenas preenchidos no final.
  - Se o êxito ou a falha foi determinada ainda, a porta de tempo deve retornar falha quando ela expirar.
- Serviços que estão executando a descriptografia não autenticada devem ter em vigor para detectar que um fluxo de mensagens "inválidos" ficou por meio de monitoramento.
  - Tenha em mente que este sinal executa (dados corrompidos de forma legítima) de falsos positivos e falsos negativos (distribuindo o ataque em um tempo longo o suficiente para evitar a detecção).

## <a name="finding-vulnerable-code---native-applications"></a>Localizando código vulnerável - aplicativos nativos

Para programas criados em relação a criptografia do Windows: biblioteca de Next Generation (CNG):

- A chamada de descriptografia é [BCryptDecrypt](https://msdn.microsoft.com/library/windows/desktop/aa375391.aspx), especificando o `BCRYPT_BLOCK_PADDING` sinalizador.
- O identificador de chave foi inicializado chamando [BCryptSetProperty](https://msdn.microsoft.com/library/windows/desktop/aa375504.aspx) com [BCRYPT_CHAINING_MODE](https://msdn.microsoft.com/library/windows/desktop/aa376211.aspx#BCRYPT_CHAINING_MODE) definido como `BCRYPT_CHAIN_MODE_CBC`.
  - Como `BCRYPT_CHAIN_MODE_CBC` é o padrão, afetado código pode não ter atribuído qualquer valor para `BCRYPT_CHAINING_MODE`.

Para programas criados com a API de criptografia mais antigas do Windows:

- A chamada de descriptografia é [CryptDecrypt](https://msdn.microsoft.com/library/windows/desktop/aa379913.aspx) com `Final=TRUE`.
- O identificador de chave foi inicializado chamando [CryptSetKeyParam](https://msdn.microsoft.com/library/windows/desktop/aa380272.aspx) com [KP_MODE](https://msdn.microsoft.com/library/windows/desktop/aa379949.aspx#KP_MODE) definido como `CRYPT_MODE_CBC`.
  - Como `CRYPT_MODE_CBC` é o padrão, afetado código pode não ter atribuído qualquer valor para `KP_MODE`.

## <a name="finding-vulnerable-code---managed-applications"></a>Localizando código vulnerável - de aplicativos gerenciados

- A chamada de descriptografia é o <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor> ou <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor(System.Byte[],System.Byte[])> métodos em <xref:System.Security.Cryptography.SymmetricAlgorithm?displayProperty=nameWithType>.
  - Isso inclui os seguintes tipos derivados no .NET, mas também pode incluir tipos de terceiros:
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
- O <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> propriedade foi definida como <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType>, <xref:System.Security.Cryptography.PaddingMode.ANSIX923?displayProperty=nameWithType>, ou <xref:System.Security.Cryptography.PaddingMode.ISO10126?displayProperty=nameWithType>.
  - Como <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType> é o padrão, afetado nunca pode ter atribuído o código de <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> propriedade.
- O <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> propriedade foi definida como <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType>
  - Como <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType> é o padrão, afetado nunca pode ter atribuído o código de <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> propriedade.

## <a name="finding-vulnerable-code---cryptographic-message-syntax"></a>Localizando código vulnerável - sintaxe de mensagem criptografada

Uma mensagem não autenticada de CMS EnvelopedData cujo conteúdo criptografado usa o modo de AES (2.16.840.1.101.3.4.1.2, 2.16.840.1.101.3.4.1.22, 2.16.840.1.101.3.4.1.42), o DES (1.3.14.3.2.7), o 3DES CBC (1.2.840.113549.3.7) ou RC2 (1.2.840.113549.3.2) é vulnerável, bem como mensagens usando outros algoritmos de criptografia de bloco no modo CBC.

Enquanto codificações de fluxo não são suscetíveis a essa vulnerabilidade em particular, a Microsoft recomenda a autenticação sempre os dados em inspecionando o valor de ContentEncryptionAlgorithm.

Para aplicativos gerenciados, um EnvelopedData CMS blob pode ser detectado como qualquer valor que é passado para <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.Decode(System.Byte[])?displayProperty=fullName>.

Para aplicativos nativos, um blob de CMS EnvelopedData pode ser detectado como qualquer valor fornecido para um identificador CMS via [CryptMsgUpdate](https://msdn.microsoft.com/library/windows/desktop/aa380231.aspx) cujo resultante [CMSG_TYPE_PARAM](https://msdn.microsoft.com/library/windows/desktop/aa380227.aspx) é `CMSG_ENVELOPED` e/ou o identificador CMS é posteriormente, enviados um `CMSG_CTRL_DECRYPT` instrução via [CryptMsgControl](https://msdn.microsoft.com/library/windows/desktop/aa380220.aspx).

## <a name="vulnerable-code-example---managed"></a>Exemplo de código vulnerável - gerenciado

Esse método lê um cookie e descriptografa-a e nenhuma verificação de integridade de dados fica visível. Portanto, o conteúdo de um cookie que é lido por esse método pode ser atacado por usuário que recebeu ou por qualquer invasor obtém o valor do cookie criptografado.

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

## <a name="example-code-following-recommended-practices---managed"></a>Exemplo a seguir do código práticas - gerenciado

O código de exemplo a seguir usa um formato de mensagem não padrão de

`cipher_algorithm_id || hmac_algorithm_id || hmac_tag || iv || ciphertext`

onde o `cipher_algorithm_id` e `hmac_algorithm_id` identificadores de algoritmo são representações (não-padrão) de aplicativo local desses algoritmos. Esses identificadores podem fazer sentido em outras partes do seu protocolo de mensagens existente em vez de como um fluxo de bytes concatenado vazio.

Este exemplo também usa uma única chave mestra para derivar uma chave de criptografia e uma chave HMAC. Isso é fornecido como uma conveniência para ativar um aplicativo individualmente organizado em um aplicativo com chave dupla e a fim de incentivar mantendo as duas chaves diferentes como valores. Ela ainda mais garante que a chave HMAC e a chave de criptografia não é possível obter fora de sincronização.

Este exemplo não aceita um <xref:System.IO.Stream> para criptografia ou descriptografia. Torna de formato de dados atual um passo criptografar difícil porque o `hmac_tag` valor precede o texto cifrado. No entanto, esse formato foi escolhido porque ele mantém todos os elementos de tamanho fixo no início para manter o analisador mais simples. Com este formato de dados, um passo descriptografar é possível, embora um implementador é evitaram chamar GetHashAndReset e verifique se o resultado antes de chamar TransformFinalBlock. Se a criptografia de streaming for importante, um modo AE diferente pode ser necessário.

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
