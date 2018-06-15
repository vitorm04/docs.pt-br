---
title: Vulnerabilidades de tempo com a descriptografia simétrica de modo CBC usando preenchimento
description: Saiba como detectar e reduzir as vulnerabilidades de tempo com a descriptografia simétrica de modo de encadeamento de blocos de codificação (CBC) usando o preenchimento.
ms.date: 06/12/2018
author: blowdart
ms.author: mairaw
ms.openlocfilehash: a07acbb943c430f6e26bec44f55a5c84306da513
ms.sourcegitcommit: 73a662360bbe2f43c19aca1fbcc2565025c60cd8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2018
ms.locfileid: "35327446"
---
# <a name="timing-vulnerabilities-with-cbc-mode-symmetric-decryption-using-padding"></a><span data-ttu-id="af4f9-103">Vulnerabilidades de tempo com a descriptografia simétrica de modo CBC usando preenchimento</span><span class="sxs-lookup"><span data-stu-id="af4f9-103">Timing vulnerabilities with CBC-mode symmetric decryption using padding</span></span>

<span data-ttu-id="af4f9-104">Microsoft, com base na pesquisa de criptografia conhecida no momento, acredita que, exceto circunstâncias muito específicas, ele não é mais seguro descriptografar dados criptografados com o encadeamento de blocos de codificação modo CBC () de criptografia simétrica quando preenchimento verificável tiver sido aplicado sem primeiro garantir a integridade do texto codificado.</span><span class="sxs-lookup"><span data-stu-id="af4f9-104">Microsoft, based on currently known cryptographic research, believes that, except for very specific circumstances, it's no longer safe to decrypt data encrypted with the Cipher-Block-Chaining (CBC) mode of symmetric encryption when verifiable padding has been applied without first ensuring the integrity of the ciphertext.</span></span>

## <a name="introduction"></a><span data-ttu-id="af4f9-105">Introdução</span><span class="sxs-lookup"><span data-stu-id="af4f9-105">Introduction</span></span>

<span data-ttu-id="af4f9-106">Um ataque de preenchimento oracle é um tipo de ataque contra os dados criptografados que permite que o invasor descriptografar o conteúdo dos dados, sem conhecer a chave.</span><span class="sxs-lookup"><span data-stu-id="af4f9-106">A padding oracle attack is a type of attack against encrypted data that allows the attacker to decrypt the contents of the data, without knowing the key.</span></span>

<span data-ttu-id="af4f9-107">Um oracle se refere a um "dizer" que fornece um invasor saber se a ação que está executando está correta ou não.</span><span class="sxs-lookup"><span data-stu-id="af4f9-107">An oracle refers to a "tell" which gives an attacker information about whether the action they're executing is correct or not.</span></span> <span data-ttu-id="af4f9-108">Imagine um tabuleiro de jogo ou da placa de jogo com um filho.</span><span class="sxs-lookup"><span data-stu-id="af4f9-108">Imagine playing a board or card game with a child.</span></span> <span data-ttu-id="af4f9-109">Quando sua face acende com um grande Smiley porque ela acha que ela está prestes a fazer um bom movimento, que é um oracle.</span><span class="sxs-lookup"><span data-stu-id="af4f9-109">When her face lights up with a big smile because she thinks she's about to make a good move, that's an oracle.</span></span> <span data-ttu-id="af4f9-110">Você, como o adversário, pode usar esse oracle para planejar próximo movimento adequadamente.</span><span class="sxs-lookup"><span data-stu-id="af4f9-110">You, as the opponent, can use this oracle to plan your next move appropriately.</span></span>

<span data-ttu-id="af4f9-111">O preenchimento é um termo específico de criptografia.</span><span class="sxs-lookup"><span data-stu-id="af4f9-111">Padding is a specific cryptographic term.</span></span> <span data-ttu-id="af4f9-112">Algumas codificações, que são os algoritmos usados para criptografar os dados, trabalhar em blocos de dados onde cada bloco é um tamanho fixo.</span><span class="sxs-lookup"><span data-stu-id="af4f9-112">Some ciphers, which are the algorithms used to encrypt your data, work on blocks of data where each block is a fixed size.</span></span> <span data-ttu-id="af4f9-113">Se os dados que você deseja criptografar não o tamanho certo para preencher os blocos, seus dados são preenchidos até que ele faz.</span><span class="sxs-lookup"><span data-stu-id="af4f9-113">If the data you want to encrypt isn't the right size to fill the blocks, your data is padded until it does.</span></span> <span data-ttu-id="af4f9-114">Muitos formulários de preenchimento exigem que o preenchimento sempre esteja presente, mesmo se a entrada original era do tamanho correto.</span><span class="sxs-lookup"><span data-stu-id="af4f9-114">Many forms of padding require that padding to always be present, even if the original input was of the right size.</span></span> <span data-ttu-id="af4f9-115">Isso permite que o preenchimento deve sempre ser removido com segurança após a descriptografia.</span><span class="sxs-lookup"><span data-stu-id="af4f9-115">This allows the padding to always be safely removed upon decryption.</span></span>

<span data-ttu-id="af4f9-116">Reunindo os dois pontos, uma implementação de software com um oracle preenchimento revela se dados descriptografados tem preenchimento válido.</span><span class="sxs-lookup"><span data-stu-id="af4f9-116">Putting the two things together, a software implementation with a padding oracle reveals whether decrypted data has valid padding.</span></span> <span data-ttu-id="af4f9-117">O oracle pode ser algo simples, como retornar um valor que diz "Preenchimento inválido" ou algo mais complicado como tirar uma hora diferente, para processar um bloco válido em vez de um bloco inválido.</span><span class="sxs-lookup"><span data-stu-id="af4f9-117">The oracle could be something as simple as returning a value that says "Invalid padding" or something more complicated like taking a measurably different time to process a valid block as opposed to an invalid block.</span></span>

<span data-ttu-id="af4f9-118">Codificações de bloco de outra propriedade, chamada de modo, o que determina a relação de dados no primeiro bloco para os dados no segundo bloco, e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="af4f9-118">Block-based ciphers have another property, called the mode, which determines the relationship of data in the first block to the data in the second block, and so on.</span></span> <span data-ttu-id="af4f9-119">Um dos modos mais comumente usados é CBC.</span><span class="sxs-lookup"><span data-stu-id="af4f9-119">One of the most commonly used modes is CBC.</span></span> <span data-ttu-id="af4f9-120">CBC apresenta um bloco aleatório inicial, conhecido como o vetor de inicialização (IV) e combina o bloco anterior com o resultado da criptografia estática para torná-lo, de modo que criptografar a mesma mensagem com a mesma chave sempre não produzem a mesma saída criptografada.</span><span class="sxs-lookup"><span data-stu-id="af4f9-120">CBC introduces an initial random block, known as the Initialization Vector (IV), and combines the previous block with the result of static encryption to make it such that encrypting the same message with the same key doesn't always produce the same encrypted output.</span></span>

<span data-ttu-id="af4f9-121">Um invasor pode usar um oracle preenchimento, em combinação com como CBC dados são estruturados, para enviar mensagens ligeiramente alteradas para o código que expõe o oracle e manter envio de dados até que o oracle informa os dados estão corretos.</span><span class="sxs-lookup"><span data-stu-id="af4f9-121">An attacker can use a padding oracle, in combination with how CBC data is structured, to send slightly changed messages to the code that exposes the oracle, and keep sending data until the oracle tells them the data is correct.</span></span> <span data-ttu-id="af4f9-122">Dessa resposta, o invasor pode descriptografar a mensagem byte por byte.</span><span class="sxs-lookup"><span data-stu-id="af4f9-122">From this response, the attacker can decrypt the message byte by byte.</span></span>

<span data-ttu-id="af4f9-123">Redes de computador modernos são de tal alta qualidade que um invasor pode detectar muito pequenas (menos de 0,1 ms) tempo de diferenças em execução em sistemas remotos.</span><span class="sxs-lookup"><span data-stu-id="af4f9-123">Modern computer networks are of such high quality that an attacker can detect very small (less than 0.1 ms) differences in execution time on remote systems.</span></span> <span data-ttu-id="af4f9-124">Aplicativos que supondo que uma descriptografia bem-sucedida só pode acontecer quando os dados não foram violados podem ser vulneráveis a ataques de ferramentas que são projetadas para observar as diferenças na descriptografia com e sem êxito.</span><span class="sxs-lookup"><span data-stu-id="af4f9-124">Applications that are assuming that a successful decryption can only happen when the data wasn't tampered with may be vulnerable to attack from tools that are designed to observe differences in successful and unsuccessful decryption.</span></span> <span data-ttu-id="af4f9-125">Essa diferença de tempo pode ser mais significativa em alguns idiomas ou bibliotecas do que outras pessoas, agora se acredita que se trata de uma ameaça prática para todos os idiomas e bibliotecas quando a resposta do aplicativo a falha é levada em conta.</span><span class="sxs-lookup"><span data-stu-id="af4f9-125">While this timing difference may be more significant in some languages or libraries than others, it's now believed that this is a practical threat for all languages and libraries when the application's response to failure is taken into account.</span></span>

<span data-ttu-id="af4f9-126">Esse ataque se baseia na capacidade de alterar os dados criptografados e testar o resultado com o oracle.</span><span class="sxs-lookup"><span data-stu-id="af4f9-126">This attack relies on the ability to change the encrypted data and test the result with the oracle.</span></span> <span data-ttu-id="af4f9-127">É a única maneira de reduzir totalmente o ataque de detectar alterações aos dados criptografados e recusar executar quaisquer ações sobre ela.</span><span class="sxs-lookup"><span data-stu-id="af4f9-127">The only way to fully mitigate the attack is to detect changes to the encrypted data and refuse to perform any actions on it.</span></span> <span data-ttu-id="af4f9-128">O modo padrão para fazer isso é criar uma assinatura para os dados e validar a assinatura antes de todas as operações são executadas.</span><span class="sxs-lookup"><span data-stu-id="af4f9-128">The standard way to do this is to create a signature for the data and validate that signature before any operations are performed.</span></span> <span data-ttu-id="af4f9-129">A assinatura deve ser verificada, ele não pode ser criado, o invasor, caso contrário, eles seriam alterar os dados criptografados e uma nova assinatura com base nos dados alterados de computação.</span><span class="sxs-lookup"><span data-stu-id="af4f9-129">The signature must be verifiable, it cannot be created by the attacker, otherwise they'd change the encrypted data, then compute a new signature based on the changed data.</span></span> <span data-ttu-id="af4f9-130">Um tipo comum de assinatura apropriada é conhecido como um código de autenticação de mensagem de hash com chave (HMAC).</span><span class="sxs-lookup"><span data-stu-id="af4f9-130">One common type of appropriate signature is known as a keyed-hash message authentication code (HMAC).</span></span> <span data-ttu-id="af4f9-131">Um HMAC é diferente de uma soma de verificação, que leva a uma chave secreta, conhecida somente para a pessoa que gera o HMAC e para a pessoa validá-lo.</span><span class="sxs-lookup"><span data-stu-id="af4f9-131">An HMAC differs from a checksum in that it takes a secret key, known only to the person producing the HMAC and to the person validating it.</span></span> <span data-ttu-id="af4f9-132">Sem posse da chave, você não pode produzir um HMAC correto.</span><span class="sxs-lookup"><span data-stu-id="af4f9-132">Without possession of the key, you can't produce a correct HMAC.</span></span> <span data-ttu-id="af4f9-133">Quando você receber seus dados, deve levar os dados criptografados, independentemente de computação o HMAC usando a chave secreta você e o compartilhamento de remetente e a comparação computado o HMAC eles enviado em relação a um.</span><span class="sxs-lookup"><span data-stu-id="af4f9-133">When you receive your data, you'd take the encrypted data, independently compute the HMAC using the secret key you and the sender share, then compare the HMAC they sent against the one you computed.</span></span> <span data-ttu-id="af4f9-134">Essa comparação deve ser constante tempo, caso contrário, você adicionou outro oracle detectável, permitindo que um tipo diferente de ataque.</span><span class="sxs-lookup"><span data-stu-id="af4f9-134">This comparison must be constant time, otherwise you've added another detectable oracle, allowing a different type of attack.</span></span>

<span data-ttu-id="af4f9-135">Em resumo, usar preenchidas CBC codificações em bloco com segurança, você deve combiná-los com um HMAC (ou outra verificação de integridade de dados) que você validar usando uma comparação de tempo constante antes de tentar descriptografar os dados.</span><span class="sxs-lookup"><span data-stu-id="af4f9-135">In summary, to use padded CBC block ciphers safely, you must combine them with an HMAC (or another data integrity check) that you validate using a constant time comparison before trying to decrypt the data.</span></span> <span data-ttu-id="af4f9-136">Desde que todas as mensagens alteradas levam a mesma quantidade de tempo para produzir uma resposta, o ataque é impedido.</span><span class="sxs-lookup"><span data-stu-id="af4f9-136">Since all altered messages take the same amount time to produce a response, the attack is prevented.</span></span>

## <a name="who-is-vulnerable"></a><span data-ttu-id="af4f9-137">Quem é vulnerável</span><span class="sxs-lookup"><span data-stu-id="af4f9-137">Who is vulnerable</span></span>

<span data-ttu-id="af4f9-138">Essa vulnerabilidade se aplica a aplicativos gerenciados e nativos que estão executando seu próprio criptografia e descriptografia.</span><span class="sxs-lookup"><span data-stu-id="af4f9-138">This vulnerability applies to both managed and native applications that are performing their own encryption and decryption.</span></span> <span data-ttu-id="af4f9-139">Isso inclui, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="af4f9-139">This includes, for example:</span></span>

- <span data-ttu-id="af4f9-140">Um aplicativo que criptografa um cookie para descriptografia mais recente no servidor.</span><span class="sxs-lookup"><span data-stu-id="af4f9-140">An application that encrypts a cookie for later decryption on the server.</span></span>
- <span data-ttu-id="af4f9-141">Um aplicativo de banco de dados que fornece a capacidade dos usuários inserir dados em uma tabela cujas colunas são descriptografados posteriormente.</span><span class="sxs-lookup"><span data-stu-id="af4f9-141">A database application that provides the ability for users to insert data into a table whose columns are later decrypted.</span></span>
- <span data-ttu-id="af4f9-142">Um aplicativo de transferência de dados que se baseia em criptografia usando uma chave compartilhada para proteger os dados em trânsito.</span><span class="sxs-lookup"><span data-stu-id="af4f9-142">A data transfer application that relies on encryption using a shared key to protect the data in transit.</span></span>
- <span data-ttu-id="af4f9-143">Um aplicativo que criptografa e descriptografa mensagens "internos" o túnel TLS.</span><span class="sxs-lookup"><span data-stu-id="af4f9-143">An application that encrypts and decrypts messages "inside" the TLS tunnel.</span></span>

<span data-ttu-id="af4f9-144">Observe que usar TLS sozinho pode não proteger você nesses cenários.</span><span class="sxs-lookup"><span data-stu-id="af4f9-144">Note that using TLS alone may not protect you in these scenarios.</span></span>

<span data-ttu-id="af4f9-145">Um aplicativo vulnerável:</span><span class="sxs-lookup"><span data-stu-id="af4f9-145">A vulnerable application:</span></span>

- <span data-ttu-id="af4f9-146">Descriptografa os dados usando o modo de codificação CBC com um modo de preenchimento verificável, como PKCS #7 ou X.923 ANSI.</span><span class="sxs-lookup"><span data-stu-id="af4f9-146">Decrypts data using the CBC cipher mode with a verifiable padding mode, such as PKCS#7 or ANSI X.923.</span></span>
- <span data-ttu-id="af4f9-147">Executa a descriptografia sem ter executado uma verificação de integridade de dados (por meio de um MAC ou uma assinatura digital assimétrica).</span><span class="sxs-lookup"><span data-stu-id="af4f9-147">Performs the decryption without having performed a data integrity check (via a MAC or an asymmetric digital signature).</span></span>

<span data-ttu-id="af4f9-148">Isso também se aplica a aplicativos criados sobre abstrações sobre esses primitivos, como a estrutura de EnvelopedData sintaxe de mensagem criptografada (PKCS #7/CMS).</span><span class="sxs-lookup"><span data-stu-id="af4f9-148">This also applies to applications built on top of abstractions over top of these primitives, such as the Cryptographic Message Syntax (PKCS#7/CMS) EnvelopedData structure.</span></span>

## <a name="related-areas-of-concern"></a><span data-ttu-id="af4f9-149">Relacionados áreas de interesse</span><span class="sxs-lookup"><span data-stu-id="af4f9-149">Related areas of concern</span></span>

<span data-ttu-id="af4f9-150">Pesquisa levou Microsoft ainda mais se preocupar com as mensagens de CBC são preenchidas com preenchimento quando a mensagem tem uma estrutura bem conhecido ou previsível rodapé 10126 ISO equivalente.</span><span class="sxs-lookup"><span data-stu-id="af4f9-150">Research has led Microsoft to be further concerned about CBC messages that are padded with ISO 10126-equivalent padding when the message has a well-known or predictable footer structure.</span></span> <span data-ttu-id="af4f9-151">Por exemplo, conteúdo preparado com as regras da sintaxe de criptografia do W3C XML e recomendação de processamento (xmlenc, EncryptedXml).</span><span class="sxs-lookup"><span data-stu-id="af4f9-151">For example, content prepared under the rules of the W3C XML Encryption Syntax and Processing Recommendation (xmlenc, EncryptedXml).</span></span> <span data-ttu-id="af4f9-152">Embora a orientação do W3C para assinar a mensagem, em seguida, criptografar foi considerada apropriada no momento, a Microsoft recomenda agora sempre fazendo logon criptografar, em seguida.</span><span class="sxs-lookup"><span data-stu-id="af4f9-152">While the W3C guidance to sign the message then encrypt was considered appropriate at the time, Microsoft now recommends always doing encrypt-then-sign.</span></span>

<span data-ttu-id="af4f9-153">Os desenvolvedores de aplicativos devem estar sempre atentos ao verificar a aplicabilidade de uma chave de assinatura assimétrica, pois não há nenhuma relação de confiança inerente entre uma chave assimétrica e uma mensagem arbitrária.</span><span class="sxs-lookup"><span data-stu-id="af4f9-153">Application developers should always be mindful of verifying the applicability of an asymmetric signature key, as there's no inherent trust relationship between an asymmetric key and an arbitrary message.</span></span>

## <a name="details"></a><span data-ttu-id="af4f9-154">Detalhes</span><span class="sxs-lookup"><span data-stu-id="af4f9-154">Details</span></span>

<span data-ttu-id="af4f9-155">Historicamente, tem sido consenso é importante criptografar e autenticar dados importantes, usando meios, como assinaturas HMAC ou RSA.</span><span class="sxs-lookup"><span data-stu-id="af4f9-155">Historically, there has been consensus that it's important to both encrypt and authenticate important data, using means such as HMAC or RSA signatures.</span></span> <span data-ttu-id="af4f9-156">No entanto, houve menos orientação clara sobre como sequenciar as operações de criptografia e autenticação.</span><span class="sxs-lookup"><span data-stu-id="af4f9-156">However, there has been less clear guidance as to how to sequence the encryption and authentication operations.</span></span> <span data-ttu-id="af4f9-157">Devido à vulnerabilidade de detalhadas neste artigo, diretrizes da Microsoft é usar sempre o paradigma "criptografar-then-sign".</span><span class="sxs-lookup"><span data-stu-id="af4f9-157">Due to the vulnerability detailed in this article, Microsoft's guidance is now to always use the "encrypt-then-sign" paradigm.</span></span> <span data-ttu-id="af4f9-158">Ou seja, primeiro criptografar dados usando uma chave simétrica e computa um MAC ou a assinatura assimétrica sobre o texto cifrado (dados criptografados).</span><span class="sxs-lookup"><span data-stu-id="af4f9-158">That is, first encrypt data using a symmetric key, then compute a MAC or asymmetric signature over the ciphertext (encrypted data).</span></span> <span data-ttu-id="af4f9-159">Quando a descriptografia de dados, execute o inverso.</span><span class="sxs-lookup"><span data-stu-id="af4f9-159">When decrypting data, perform the reverse.</span></span> <span data-ttu-id="af4f9-160">Primeiro, confirme o endereço MAC ou assinatura do texto codificado e descriptografá-lo.</span><span class="sxs-lookup"><span data-stu-id="af4f9-160">First, confirm the MAC or signature of the ciphertext, then decrypt it.</span></span>

<span data-ttu-id="af4f9-161">Uma classe de vulnerabilidades conhecidas como "preenchimento oracle ataques" comprovadamente existe há mais de 10 anos.</span><span class="sxs-lookup"><span data-stu-id="af4f9-161">A class of vulnerabilities known as "padding oracle attacks" have been known to exist for over 10 years.</span></span> <span data-ttu-id="af4f9-162">Essas vulnerabilidades permitem que um invasor descriptografar dados criptografados por algoritmos de bloco simétrico, como AES e 3DES, usar não mais do que 4096 tentativas por um bloco de dados.</span><span class="sxs-lookup"><span data-stu-id="af4f9-162">These vulnerabilities allow an attacker to decrypt data encrypted by symmetric block algorithms, such as AES and 3DES, using no more than 4096 attempts per block of data.</span></span> <span data-ttu-id="af4f9-163">Essas vulnerabilidades fazer uso do fato de que bloqueiam as codificações são usados com mais frequência com dados de preenchimento verificável no final.</span><span class="sxs-lookup"><span data-stu-id="af4f9-163">These vulnerabilities make use of the fact that block ciphers are most frequently used with verifiable padding data at the end.</span></span> <span data-ttu-id="af4f9-164">Foi encontrado que, se um invasor pode violar o texto cifrado e descobrir se a violação causou um erro no formato de preenchimento no final, o invasor poderá descriptografar os dados.</span><span class="sxs-lookup"><span data-stu-id="af4f9-164">It was found that if an attacker can tamper with ciphertext and find out whether the tampering caused an error in the format of the padding at the end, the attacker can decrypt the data.</span></span>

<span data-ttu-id="af4f9-165">Inicialmente, ataques práticos baseadas nos serviços que retornam os códigos de erro diferentes com base em se preenchimento foi válido, como a vulnerabilidade do ASP.NET [MS10-070](https://technet.microsoft.com/library/security/ms10-070.aspx).</span><span class="sxs-lookup"><span data-stu-id="af4f9-165">Initially, practical attacks were based on services that would return different error codes based on whether padding was valid, such as the ASP.NET vulnerability [MS10-070](https://technet.microsoft.com/library/security/ms10-070.aspx).</span></span> <span data-ttu-id="af4f9-166">No entanto, a Microsoft agora acredita que é prático conduzir ataques semelhantes usando apenas as diferenças no intervalo entre processamento preenchimento válido e inválido.</span><span class="sxs-lookup"><span data-stu-id="af4f9-166">However, Microsoft now believes that it's practical to conduct similar attacks using only the differences in timing between processing valid and invalid padding.</span></span>

<span data-ttu-id="af4f9-167">Contanto que o esquema de criptografia emprega uma assinatura e que a verificação da assinatura é executada com um tempo de execução fixo para um determinado comprimento de dados (independentemente do conteúdo), a integridade dos dados pode ser verificada sem emitir todas as informações para um o invasor por meio de um [canal do lado do](https://en.wikipedia.org/wiki/Side-channel_attack).</span><span class="sxs-lookup"><span data-stu-id="af4f9-167">Provided that the encryption scheme employs a signature and that the signature verification is performed with a fixed runtime for a given length of data (irrespective of the contents), the data integrity can be verified without emitting any information to an attacker via a [side channel](https://en.wikipedia.org/wiki/Side-channel_attack).</span></span> <span data-ttu-id="af4f9-168">Desde que a verificação de integridade rejeita qualquer mensagem violada, a ameaça de oracle preenchimento é reduzida.</span><span class="sxs-lookup"><span data-stu-id="af4f9-168">Since the integrity check rejects any tampered messages, the padding oracle threat is mitigated.</span></span>

## <a name="guidance"></a><span data-ttu-id="af4f9-169">Diretrizes</span><span class="sxs-lookup"><span data-stu-id="af4f9-169">Guidance</span></span>

<span data-ttu-id="af4f9-170">Primeiramente, a Microsoft recomenda que todos os dados que tem a confidencialidade precisam ser transmitidos pela segurança TLS (Transport Layer), o sucessor ao protocolo (SSL).</span><span class="sxs-lookup"><span data-stu-id="af4f9-170">First and foremost, Microsoft recommends that any data that has confidentiality needs be transmitted over Transport Layer Security (TLS), the successor to Secure Sockets Layer (SSL).</span></span>

<span data-ttu-id="af4f9-171">Em seguida, analise seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="af4f9-171">Next, analyze your application to:</span></span>

- <span data-ttu-id="af4f9-172">Compreenda precisamente o que estiver executando a criptografia e que a criptografia está sendo fornecida, as plataformas e APIs que você está usando.</span><span class="sxs-lookup"><span data-stu-id="af4f9-172">Understand precisely what encryption you're performing and what encryption is being provided by the platforms and APIs you're using.</span></span>
- <span data-ttu-id="af4f9-173">Ter certeza de que cada uso em cada camada de um simétrica [algoritmo de codificação de bloco](https://en.wikipedia.org/wiki/Block_cipher#Notable_block_ciphers), como AES e 3DES, no modo CBC incorporar o uso de uma verificação de integridade de dados com a chave secreta (uma assinatura assimétrica, um HMAC, ou para alterar o modo de codificação para um [autenticado criptografia](https://en.wikipedia.org/wiki/Authenticated_encryption) modo (AE) como GCM ou CCM).</span><span class="sxs-lookup"><span data-stu-id="af4f9-173">Be certain that each usage at each layer of a symmetric [block cipher algorithm](https://en.wikipedia.org/wiki/Block_cipher#Notable_block_ciphers), such as AES and 3DES, in CBC mode incorporate the use of a secret-keyed data integrity check (an asymmetric signature, an HMAC, or to change the cipher mode to an [authenticated encryption](https://en.wikipedia.org/wiki/Authenticated_encryption) (AE) mode such as GCM or CCM).</span></span>

<span data-ttu-id="af4f9-174">Com base na pesquisa atual, acredita-se que, quando as etapas de autenticação e criptografia são executadas de maneira independente para modos de não-AE de criptografia, autenticação do texto cifrado (criptografar-then-entrada) é a melhor opção geral.</span><span class="sxs-lookup"><span data-stu-id="af4f9-174">Based on the current research, it's generally believed that when the authentication and encryption steps are performed independently for non-AE modes of encryption, authenticating the ciphertext (encrypt-then-sign) is the best general option.</span></span> <span data-ttu-id="af4f9-175">No entanto, há uma resposta correta se aplicam à criptografia e este generalização não é tão bons quanto direcionado conselhos de um profissional criptógrafo.</span><span class="sxs-lookup"><span data-stu-id="af4f9-175">However, there's no one-size-fits-all correct answer to cryptography and this generalization isn't as good as directed advice from a professional cryptographer.</span></span>

<span data-ttu-id="af4f9-176">Aplicativos que não é possível alterar o formato de mensagens, mas executar descriptografia de CBC não autenticada são incentivados a tentar incorporar atenuações, como:</span><span class="sxs-lookup"><span data-stu-id="af4f9-176">Applications that are unable to change their messaging format but perform unauthenticated CBC decryption are encouraged to try to incorporate mitigations such as:</span></span>

- <span data-ttu-id="af4f9-177">Descriptografar sem permitir o descriptografador verificar ou remover preenchimento:</span><span class="sxs-lookup"><span data-stu-id="af4f9-177">Decrypt without allowing the decryptor to verify or remove padding:</span></span>
  - <span data-ttu-id="af4f9-178">O preenchimento que foi aplicado ainda precisa ser removidos ou ignorados, você está movendo a carga em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="af4f9-178">Any padding that was applied still needs to be removed or ignored, you're moving the burden into your application.</span></span>
  - <span data-ttu-id="af4f9-179">A vantagem é que a verificação de preenchimento e remoção podem ser incorporadas em outra lógica de verificação de dados de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="af4f9-179">The benefit is that the padding verification and removal can be incorporated into other application data verification logic.</span></span> <span data-ttu-id="af4f9-180">Se a verificação de preenchimento e a verificação de dados podem ser feitos no horário constante, a ameaça é reduzida.</span><span class="sxs-lookup"><span data-stu-id="af4f9-180">If the padding verification and data verification can be done in constant time, the threat is reduced.</span></span>
  - <span data-ttu-id="af4f9-181">Como a interpretação do preenchimento altera o comprimento da mensagem percebido, pode ainda ser emitidas a partir dessa abordagem de informações de tempo.</span><span class="sxs-lookup"><span data-stu-id="af4f9-181">Since the interpretation of the padding changes the perceived message length, there may still be timing information emitted from this approach.</span></span>
- <span data-ttu-id="af4f9-182">Altere o modo de preenchimento de descriptografia para ISO10126:</span><span class="sxs-lookup"><span data-stu-id="af4f9-182">Change the decryption padding mode to ISO10126:</span></span>
  - <span data-ttu-id="af4f9-183">Preenchimento de descriptografia ISO10126 é compatível com preenchimento de criptografia PKCS7 e ANSIX923 preenchimento de criptografia.</span><span class="sxs-lookup"><span data-stu-id="af4f9-183">ISO10126 decryption padding is compatible with both PKCS7 encryption padding and ANSIX923 encryption padding.</span></span>
  - <span data-ttu-id="af4f9-184">Alterando o modo reduz o conhecimento do oracle de preenchimento de 1 byte, em vez do bloco inteiro.</span><span class="sxs-lookup"><span data-stu-id="af4f9-184">Changing the mode reduces the padding oracle knowledge to 1 byte instead of the entire block.</span></span> <span data-ttu-id="af4f9-185">No entanto, se o conteúdo tiver um rodapé conhecido, como um elemento XML de fechamento ataques relacionados podem continuar atacar o resto da mensagem.</span><span class="sxs-lookup"><span data-stu-id="af4f9-185">However, if the content has a well-known footer, such as a closing XML element, related attacks can continue to attack the rest of the message.</span></span>
  - <span data-ttu-id="af4f9-186">Isso também não impede que a recuperação de texto sem formatação em situações em que o invasor pode forçar o mesmo texto não criptografado a serem criptografados várias vezes com um deslocamento de mensagem diferentes.</span><span class="sxs-lookup"><span data-stu-id="af4f9-186">This also doesn't prevent plaintext recovery in situations where the attacker can coerce the same plaintext to be encrypted multiple times with a different message offset.</span></span>
- <span data-ttu-id="af4f9-187">A avaliação de uma chamada de descriptografia para Umedeça o sinal de intervalo de porta:</span><span class="sxs-lookup"><span data-stu-id="af4f9-187">Gate the evaluation of a decryption call to dampen the timing signal:</span></span>
  - <span data-ttu-id="af4f9-188">O cálculo de tempo de espera deve ter no mínimo exceder a quantidade máxima de tempo que a operação de descriptografia seria necessário para nenhum segmento de dados que contém o preenchimento.</span><span class="sxs-lookup"><span data-stu-id="af4f9-188">The computation of hold time must have a minimum in excess of the maximum amount of time the decryption operation would take for any data segment that contains padding.</span></span>
  - <span data-ttu-id="af4f9-189">Cálculos de tempo devem ser feitos de acordo com as orientações em [adquirir os carimbos de hora de alta resolução](https://msdn.microsoft.com/library/windows/desktop/dn55340.aspx), não usando <xref:System.Environment.TickCount?displayProperty=nameWithType> (sujeito a roll-over/estouro) ou subtraindo duas carimbos de hora do sistema (sujeitos ao ajuste de NTP erros).</span><span class="sxs-lookup"><span data-stu-id="af4f9-189">Time computations should be done according to the guidance in [Acquiring high-resolution time stamps](https://msdn.microsoft.com/library/windows/desktop/dn55340.aspx), not by using <xref:System.Environment.TickCount?displayProperty=nameWithType> (subject to roll-over/overflow) or subtracting two system timestamps (subject to NTP adjustment errors).</span></span>
  - <span data-ttu-id="af4f9-190">Cálculos de tempo devem ser incluindo a operação de descriptografia, incluindo todas as exceções potenciais em gerenciado ou aplicativos do C++, não apenas preenchidos no final.</span><span class="sxs-lookup"><span data-stu-id="af4f9-190">Time computations must be inclusive of the decryption operation including all potential exceptions in managed or C++ applications, not just padded onto the end.</span></span>
  - <span data-ttu-id="af4f9-191">Se o êxito ou a falha foi determinada ainda, a porta de tempo deve retornar falha quando ela expirar.</span><span class="sxs-lookup"><span data-stu-id="af4f9-191">If success or failure has been determined yet, the timing gate needs to return failure when it expires.</span></span>
- <span data-ttu-id="af4f9-192">Serviços que estão executando a descriptografia não autenticada devem ter em vigor para detectar que um fluxo de mensagens "inválidos" ficou por meio de monitoramento.</span><span class="sxs-lookup"><span data-stu-id="af4f9-192">Services that are performing unauthenticated decryption should have monitoring in place to detect that a flood of "invalid" messages has come through.</span></span>
  - <span data-ttu-id="af4f9-193">Tenha em mente que este sinal executa (dados corrompidos de forma legítima) de falsos positivos e falsos negativos (distribuindo o ataque em um tempo longo o suficiente para evitar a detecção).</span><span class="sxs-lookup"><span data-stu-id="af4f9-193">Bear in mind that this signal carries both false positives (legitimately corrupted data) and false negatives (spreading out the attack over a sufficiently long time to evade detection).</span></span>

## <a name="finding-vulnerable-code---native-applications"></a><span data-ttu-id="af4f9-194">Localizando código vulnerável - aplicativos nativos</span><span class="sxs-lookup"><span data-stu-id="af4f9-194">Finding vulnerable code - native applications</span></span>

<span data-ttu-id="af4f9-195">Para programas criados em relação a criptografia do Windows: biblioteca de Next Generation (CNG):</span><span class="sxs-lookup"><span data-stu-id="af4f9-195">For programs built against the Windows Cryptography: Next Generation (CNG) library:</span></span>

- <span data-ttu-id="af4f9-196">A chamada de descriptografia é [BCryptDecrypt](https://msdn.microsoft.com/library/windows/desktop/aa375391.aspx), especificando o `BCRYPT_BLOCK_PADDING` sinalizador.</span><span class="sxs-lookup"><span data-stu-id="af4f9-196">The decryption call is to [BCryptDecrypt](https://msdn.microsoft.com/library/windows/desktop/aa375391.aspx), specifying the `BCRYPT_BLOCK_PADDING` flag.</span></span>
- <span data-ttu-id="af4f9-197">O identificador de chave foi inicializado chamando [BCryptSetProperty](https://msdn.microsoft.com/library/windows/desktop/aa375504.aspx) com [BCRYPT_CHAINING_MODE](https://msdn.microsoft.com/library/windows/desktop/aa376211.aspx#BCRYPT_CHAINING_MODE) definido como `BCRYPT_CHAIN_MODE_CBC`.</span><span class="sxs-lookup"><span data-stu-id="af4f9-197">The key handle has been initialized by calling [BCryptSetProperty](https://msdn.microsoft.com/library/windows/desktop/aa375504.aspx) with [BCRYPT_CHAINING_MODE](https://msdn.microsoft.com/library/windows/desktop/aa376211.aspx#BCRYPT_CHAINING_MODE) set to `BCRYPT_CHAIN_MODE_CBC`.</span></span>
  - <span data-ttu-id="af4f9-198">Como `BCRYPT_CHAIN_MODE_CBC` é o padrão, afetado código pode não ter atribuído qualquer valor para `BCRYPT_CHAINING_MODE`.</span><span class="sxs-lookup"><span data-stu-id="af4f9-198">Since `BCRYPT_CHAIN_MODE_CBC` is the default, affected code may not have assigned any value for `BCRYPT_CHAINING_MODE`.</span></span>

<span data-ttu-id="af4f9-199">Para programas criados com a API de criptografia mais antigas do Windows:</span><span class="sxs-lookup"><span data-stu-id="af4f9-199">For programs built against the older Windows Cryptographic API:</span></span>

- <span data-ttu-id="af4f9-200">A chamada de descriptografia é [CryptDecrypt](https://msdn.microsoft.com/library/windows/desktop/aa379913.aspx) com `Final=TRUE`.</span><span class="sxs-lookup"><span data-stu-id="af4f9-200">The decryption call is to [CryptDecrypt](https://msdn.microsoft.com/library/windows/desktop/aa379913.aspx) with `Final=TRUE`.</span></span>
- <span data-ttu-id="af4f9-201">O identificador de chave foi inicializado chamando [CryptSetKeyParam](https://msdn.microsoft.com/library/windows/desktop/aa380272.aspx) com [KP_MODE](https://msdn.microsoft.com/library/windows/desktop/aa379949.aspx#KP_MODE) definido como `CRYPT_MODE_CBC`.</span><span class="sxs-lookup"><span data-stu-id="af4f9-201">The key handle has been initialized by calling [CryptSetKeyParam](https://msdn.microsoft.com/library/windows/desktop/aa380272.aspx) with [KP_MODE](https://msdn.microsoft.com/library/windows/desktop/aa379949.aspx#KP_MODE) set to `CRYPT_MODE_CBC`.</span></span>
  - <span data-ttu-id="af4f9-202">Como `CRYPT_MODE_CBC` é o padrão, afetado código pode não ter atribuído qualquer valor para `KP_MODE`.</span><span class="sxs-lookup"><span data-stu-id="af4f9-202">Since `CRYPT_MODE_CBC` is the default, affected code may not have assigned any value for `KP_MODE`.</span></span>

## <a name="finding-vulnerable-code---managed-applications"></a><span data-ttu-id="af4f9-203">Localizando código vulnerável - de aplicativos gerenciados</span><span class="sxs-lookup"><span data-stu-id="af4f9-203">Finding vulnerable code - managed applications</span></span>

- <span data-ttu-id="af4f9-204">A chamada de descriptografia é o <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor> ou <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor(System.Byte[],System.Byte[])> métodos em <xref:System.Security.Cryptography.SymmetricAlgorithm?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="af4f9-204">The decryption call is to the <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor> or <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor(System.Byte[],System.Byte[])> methods on <xref:System.Security.Cryptography.SymmetricAlgorithm?displayProperty=nameWithType>.</span></span>
  - <span data-ttu-id="af4f9-205">Isso inclui os seguintes tipos derivados no .NET, mas também pode incluir tipos de terceiros:</span><span class="sxs-lookup"><span data-stu-id="af4f9-205">This includes the following derived types within the .NET, but may also include third-party types:</span></span>
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
- <span data-ttu-id="af4f9-206">O <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> propriedade foi definida como <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType>, <xref:System.Security.Cryptography.PaddingMode.ANSIX923?displayProperty=nameWithType>, ou <xref:System.Security.Cryptography.PaddingMode.ISO10126?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="af4f9-206">The <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> property was set to <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType>, <xref:System.Security.Cryptography.PaddingMode.ANSIX923?displayProperty=nameWithType>, or <xref:System.Security.Cryptography.PaddingMode.ISO10126?displayProperty=nameWithType>.</span></span>
  - <span data-ttu-id="af4f9-207">Como <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType> é o padrão, afetado nunca pode ter atribuído o código de <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="af4f9-207">Since <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType> is the default, affected code may never have assigned the <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> property.</span></span>
- <span data-ttu-id="af4f9-208">O <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> propriedade foi definida como <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="af4f9-208">The <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> property was set to <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType></span></span>
  - <span data-ttu-id="af4f9-209">Como <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType> é o padrão, afetado nunca pode ter atribuído o código de <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="af4f9-209">Since <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType> is the default, affected code may never have assigned the <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> property.</span></span>

## <a name="finding-vulnerable-code---cryptographic-message-syntax"></a><span data-ttu-id="af4f9-210">Localizando código vulnerável - sintaxe de mensagem criptografada</span><span class="sxs-lookup"><span data-stu-id="af4f9-210">Finding vulnerable code - cryptographic message syntax</span></span>

<span data-ttu-id="af4f9-211">Uma mensagem não autenticada de CMS EnvelopedData cujo conteúdo criptografado usa o modo de AES (2.16.840.1.101.3.4.1.2, 2.16.840.1.101.3.4.1.22, 2.16.840.1.101.3.4.1.42), o DES (1.3.14.3.2.7), o 3DES CBC (1.2.840.113549.3.7) ou RC2 (1.2.840.113549.3.2) é vulnerável, bem como mensagens usando outros algoritmos de criptografia de bloco no modo CBC.</span><span class="sxs-lookup"><span data-stu-id="af4f9-211">An unauthenticated CMS EnvelopedData message whose encrypted content uses the CBC mode of AES (2.16.840.1.101.3.4.1.2, 2.16.840.1.101.3.4.1.22, 2.16.840.1.101.3.4.1.42), DES (1.3.14.3.2.7), 3DES (1.2.840.113549.3.7) or RC2 (1.2.840.113549.3.2) is vulnerable, as well as messages using any other block cipher algorithms in CBC mode.</span></span>

<span data-ttu-id="af4f9-212">Enquanto codificações de fluxo não são suscetíveis a essa vulnerabilidade em particular, a Microsoft recomenda a autenticação sempre os dados em inspecionando o valor de ContentEncryptionAlgorithm.</span><span class="sxs-lookup"><span data-stu-id="af4f9-212">While stream ciphers aren't susceptible to this particular vulnerability, Microsoft recommends always authenticating the data over inspecting the ContentEncryptionAlgorithm value.</span></span>

<span data-ttu-id="af4f9-213">Para aplicativos gerenciados, um EnvelopedData CMS blob pode ser detectado como qualquer valor que é passado para <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.Decode(System.Byte[])?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="af4f9-213">For managed applications, a CMS EnvelopedData blob can be detected as any value that is passed to <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.Decode(System.Byte[])?displayProperty=fullName>.</span></span>

<span data-ttu-id="af4f9-214">Para aplicativos nativos, um blob de CMS EnvelopedData pode ser detectado como qualquer valor fornecido para um identificador CMS via [CryptMsgUpdate](https://msdn.microsoft.com/library/windows/desktop/aa380231.aspx) cujo resultante [CMSG_TYPE_PARAM](https://msdn.microsoft.com/library/windows/desktop/aa380227.aspx) é `CMSG_ENVELOPED` e/ou o identificador CMS é posteriormente, enviados um `CMSG_CTRL_DECRYPT` instrução via [CryptMsgControl](https://msdn.microsoft.com/library/windows/desktop/aa380220.aspx).</span><span class="sxs-lookup"><span data-stu-id="af4f9-214">For native applications, a CMS EnvelopedData blob can be detected as any value provided to a CMS handle via [CryptMsgUpdate](https://msdn.microsoft.com/library/windows/desktop/aa380231.aspx) whose resulting [CMSG_TYPE_PARAM](https://msdn.microsoft.com/library/windows/desktop/aa380227.aspx) is `CMSG_ENVELOPED` and/or the CMS handle is later sent a `CMSG_CTRL_DECRYPT` instruction via [CryptMsgControl](https://msdn.microsoft.com/library/windows/desktop/aa380220.aspx).</span></span>

## <a name="vulnerable-code-example---managed"></a><span data-ttu-id="af4f9-215">Exemplo de código vulnerável - gerenciado</span><span class="sxs-lookup"><span data-stu-id="af4f9-215">Vulnerable code example - managed</span></span>

<span data-ttu-id="af4f9-216">Esse método lê um cookie e descriptografa-a e nenhuma verificação de integridade de dados fica visível.</span><span class="sxs-lookup"><span data-stu-id="af4f9-216">This method reads a cookie and decrypts it and no data integrity check is visible.</span></span> <span data-ttu-id="af4f9-217">Portanto, o conteúdo de um cookie que é lido por esse método pode ser atacado por usuário que recebeu ou por qualquer invasor obtém o valor do cookie criptografado.</span><span class="sxs-lookup"><span data-stu-id="af4f9-217">Therefore, the contents of a cookie that is read by this method can be attacked by the user who received it, or by any attacker who has obtained the encrypted cookie value.</span></span>

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

## <a name="example-code-following-recommended-practices---managed"></a><span data-ttu-id="af4f9-218">Exemplo a seguir do código práticas - gerenciado</span><span class="sxs-lookup"><span data-stu-id="af4f9-218">Example code following recommended practices - managed</span></span>

<span data-ttu-id="af4f9-219">O código de exemplo a seguir usa um formato de mensagem não padrão de</span><span class="sxs-lookup"><span data-stu-id="af4f9-219">The following sample code uses a non-standard message format of</span></span>

`cipher_algorithm_id || hmac_algorithm_id || hmac_tag || iv || ciphertext`

<span data-ttu-id="af4f9-220">onde o `cipher_algorithm_id` e `hmac_algorithm_id` identificadores de algoritmo são representações (não-padrão) de aplicativo local desses algoritmos.</span><span class="sxs-lookup"><span data-stu-id="af4f9-220">where the `cipher_algorithm_id` and `hmac_algorithm_id` algorithm identifiers are application-local (non-standard) representations of those algorithms.</span></span> <span data-ttu-id="af4f9-221">Esses identificadores podem fazer sentido em outras partes do seu protocolo de mensagens existente em vez de como um fluxo de bytes concatenado vazio.</span><span class="sxs-lookup"><span data-stu-id="af4f9-221">These identifiers may make sense in other parts of your existing messaging protocol instead of as a bare concatenated bytestream.</span></span>

<span data-ttu-id="af4f9-222">Este exemplo também usa uma única chave mestra para derivar uma chave de criptografia e uma chave HMAC.</span><span class="sxs-lookup"><span data-stu-id="af4f9-222">This example also uses a single master key to derive both an encryption key and an HMAC key.</span></span> <span data-ttu-id="af4f9-223">Isso é fornecido como uma conveniência para ativar um aplicativo individualmente organizado em um aplicativo com chave dupla e a fim de incentivar mantendo as duas chaves diferentes como valores.</span><span class="sxs-lookup"><span data-stu-id="af4f9-223">This is provided both as a convenience for turning a singly-keyed application into a dual-keyed application, and to encourage keeping the two keys as different values.</span></span> <span data-ttu-id="af4f9-224">Ela ainda mais garante que a chave HMAC e a chave de criptografia não é possível obter fora de sincronização.</span><span class="sxs-lookup"><span data-stu-id="af4f9-224">It further guarantees that the HMAC key and encryption key can't get out of synchronization.</span></span>

<span data-ttu-id="af4f9-225">Este exemplo não aceita um <xref:System.IO.Stream> para criptografia ou descriptografia.</span><span class="sxs-lookup"><span data-stu-id="af4f9-225">This sample doesn't accept a <xref:System.IO.Stream> for either encryption or decryption.</span></span> <span data-ttu-id="af4f9-226">Torna de formato de dados atual um passo criptografar difícil porque o `hmac_tag` valor precede o texto cifrado.</span><span class="sxs-lookup"><span data-stu-id="af4f9-226">The current data format makes one-pass encrypt difficult because the `hmac_tag` value precedes the ciphertext.</span></span> <span data-ttu-id="af4f9-227">No entanto, esse formato foi escolhido porque ele mantém todos os elementos de tamanho fixo no início para manter o analisador mais simples.</span><span class="sxs-lookup"><span data-stu-id="af4f9-227">However, this format was chosen because it keeps all of the fixed-size elements at the beginning to keep the parser simpler.</span></span> <span data-ttu-id="af4f9-228">Com este formato de dados, um passo descriptografar é possível, embora um implementador é evitaram chamar GetHashAndReset e verifique se o resultado antes de chamar TransformFinalBlock.</span><span class="sxs-lookup"><span data-stu-id="af4f9-228">With this data format, one-pass decrypt is possible, though an implementer is cautioned to call GetHashAndReset and verify the result before calling TransformFinalBlock.</span></span> <span data-ttu-id="af4f9-229">Se a criptografia de streaming for importante, um modo AE diferente pode ser necessário.</span><span class="sxs-lookup"><span data-stu-id="af4f9-229">If streaming encryption is important, then a different AE mode may be required.</span></span>

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
