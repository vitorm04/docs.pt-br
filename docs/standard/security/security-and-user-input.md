---
title: Segurança e entrada do usuário
description: Seu código pode passar dados inseridos pelo usuário como parâmetros para outro código, o que pode afetar a segurança. Você pode fazer verificação de intervalo para rejeitar entrada problemática.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET Framework], user input
- user input, security
- secure coding, user input
- code security, user input
ms.assetid: 9141076a-96c9-4b01-93de-366bb1d858bc
ms.openlocfilehash: fa9f8d4708e928c51e446d8369c9b4556fc6fb77
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186103"
---
# <a name="security-and-user-input"></a><span data-ttu-id="d749c-104">Segurança e entrada do usuário</span><span class="sxs-lookup"><span data-stu-id="d749c-104">Security and User Input</span></span>

<span data-ttu-id="d749c-105">Os dados do usuário, que é qualquer tipo de entrada (dados de uma solicitação da Web ou URL, entrada para controles de um aplicativo Microsoft Windows Forms, e assim por diante), podem influenciar negativamente o código porque muitas vezes esses dados são usados diretamente como parâmetros para chamar outro código.</span><span class="sxs-lookup"><span data-stu-id="d749c-105">User data, which is any kind of input (data from a Web request or URL, input to controls of a Microsoft Windows Forms application, and so on), can adversely influence code because often that data is used directly as parameters to call other code.</span></span> <span data-ttu-id="d749c-106">Esta situação é análoga ao código malicioso chamando seu código com parâmetros estranhos, e as mesmas precauções devem ser tomadas.</span><span class="sxs-lookup"><span data-stu-id="d749c-106">This situation is analogous to malicious code calling your code with strange parameters, and the same precautions should be taken.</span></span> <span data-ttu-id="d749c-107">A entrada do usuário é realmente mais difícil de tornar segura porque não há um quadro de pilha para rastrear a presença dos dados potencialmente não confiáveis.</span><span class="sxs-lookup"><span data-stu-id="d749c-107">User input is actually harder to make safe because there is no stack frame to trace the presence of the potentially untrusted data.</span></span>

<span data-ttu-id="d749c-108">Estes estão entre os bugs de segurança mais sutis e difíceis de encontrar porque, embora possam existir em códigos aparentemente não relacionados à segurança, eles são uma porta de entrada para passar dados ruins para outro código.</span><span class="sxs-lookup"><span data-stu-id="d749c-108">These are among the subtlest and hardest security bugs to find because, although they can exist in code that is seemingly unrelated to security, they are a gateway to pass bad data through to other code.</span></span> <span data-ttu-id="d749c-109">Para procurar esses bugs, siga qualquer tipo de dados de entrada, imagine qual seria o alcance dos valores possíveis e considere se o código que vê esses dados pode lidar com todos esses casos.</span><span class="sxs-lookup"><span data-stu-id="d749c-109">To look for these bugs, follow any kind of input data, imagine what the range of possible values might be, and consider whether the code seeing this data can handle all those cases.</span></span> <span data-ttu-id="d749c-110">Você pode corrigir esses bugs através da verificação de alcance e rejeitando qualquer entrada que o código não possa lidar.</span><span class="sxs-lookup"><span data-stu-id="d749c-110">You can fix these bugs through range checking and rejecting any input the code cannot handle.</span></span>

<span data-ttu-id="d749c-111">Algumas considerações importantes envolvendo dados do usuário incluem:</span><span class="sxs-lookup"><span data-stu-id="d749c-111">Some important considerations involving user data include the following:</span></span>

- <span data-ttu-id="d749c-112">Qualquer dado de usuário em uma resposta de servidor é executado no contexto do site do servidor no cliente.</span><span class="sxs-lookup"><span data-stu-id="d749c-112">Any user data in a server response runs in the context of the server's site on the client.</span></span> <span data-ttu-id="d749c-113">Se o servidor da Web pega os dados do usuário e os insere na página da Web retornada, ele pode, por exemplo, incluir um \*\* \<script>\*\* tag e executado como se fosse do servidor.</span><span class="sxs-lookup"><span data-stu-id="d749c-113">If your Web server takes user data and inserts it into the returned Web page, it might, for example, include a **\<script>** tag and run as if from the server.</span></span>

- <span data-ttu-id="d749c-114">Lembre-se que o cliente pode solicitar qualquer URL.</span><span class="sxs-lookup"><span data-stu-id="d749c-114">Remember that the client can request any URL.</span></span>

- <span data-ttu-id="d749c-115">Considere caminhos complicados ou inválidos:</span><span class="sxs-lookup"><span data-stu-id="d749c-115">Consider tricky or invalid paths:</span></span>

  - <span data-ttu-id="d749c-116">.. \ , caminhos extremamente longos.</span><span class="sxs-lookup"><span data-stu-id="d749c-116">..\ , extremely long paths.</span></span>

  - <span data-ttu-id="d749c-117">Uso de caracteres curinga (\*).</span><span class="sxs-lookup"><span data-stu-id="d749c-117">Use of wild card characters (\*).</span></span>

  - <span data-ttu-id="d749c-118">Expansão do token (%token%).</span><span class="sxs-lookup"><span data-stu-id="d749c-118">Token expansion (%token%).</span></span>

  - <span data-ttu-id="d749c-119">Estranhas formas de caminhos com significado especial.</span><span class="sxs-lookup"><span data-stu-id="d749c-119">Strange forms of paths with special meaning.</span></span>

  - <span data-ttu-id="d749c-120">Nomes de fluxo de `filename::$DATA`sistema de arquivos alternativos, tais como .</span><span class="sxs-lookup"><span data-stu-id="d749c-120">Alternate file system stream names such as `filename::$DATA`.</span></span>

  - <span data-ttu-id="d749c-121">Versões curtas de `longfi~1` `longfilename`nomes de arquivos, como para .</span><span class="sxs-lookup"><span data-stu-id="d749c-121">Short versions of file names such as `longfi~1` for `longfilename`.</span></span>

- <span data-ttu-id="d749c-122">Lembre-se que Eval (userdata) pode fazer qualquer coisa.</span><span class="sxs-lookup"><span data-stu-id="d749c-122">Remember that Eval(userdata) can do anything.</span></span>

- <span data-ttu-id="d749c-123">Tenha cuidado com a vinculação tardia a um nome que inclua alguns dados do usuário.</span><span class="sxs-lookup"><span data-stu-id="d749c-123">Be wary of late binding to a name that includes some user data.</span></span>

- <span data-ttu-id="d749c-124">Se você está lidando com dados da Web, considere as várias formas de fugas que são permitidas, incluindo:</span><span class="sxs-lookup"><span data-stu-id="d749c-124">If you are dealing with Web data, consider the various forms of escapes that are permissible, including:</span></span>

  - <span data-ttu-id="d749c-125">Fugas hexadecimais (%nn).</span><span class="sxs-lookup"><span data-stu-id="d749c-125">Hexadecimal escapes (%nn).</span></span>

  - <span data-ttu-id="d749c-126">Fugas unicode (%nnn).</span><span class="sxs-lookup"><span data-stu-id="d749c-126">Unicode escapes (%nnn).</span></span>

  - <span data-ttu-id="d749c-127">Fugas de UTF-8 long overlong (%nn%nn).</span><span class="sxs-lookup"><span data-stu-id="d749c-127">Overlong UTF-8 escapes (%nn%nn).</span></span>

  - <span data-ttu-id="d749c-128">Fugas duplas (%nn torna-se %mmnn, onde %mm é a fuga para '%').</span><span class="sxs-lookup"><span data-stu-id="d749c-128">Double escapes (%nn becomes %mmnn, where %mm is the escape for '%').</span></span>

- <span data-ttu-id="d749c-129">Desconfie de nomes de usuários que possam ter mais de um formato canônico.</span><span class="sxs-lookup"><span data-stu-id="d749c-129">Be wary of user names that might have more than one canonical format.</span></span> <span data-ttu-id="d749c-130">Por exemplo, muitas vezes você\\pode usar o formulário*mydomain username* ou o formulário *de nome de* @mydomain.example.com usuário.</span><span class="sxs-lookup"><span data-stu-id="d749c-130">For example, you can often use either the MYDOMAIN\\*username* form or the *username*@mydomain.example.com form.</span></span>

## <a name="see-also"></a><span data-ttu-id="d749c-131">Confira também</span><span class="sxs-lookup"><span data-stu-id="d749c-131">See also</span></span>

- [<span data-ttu-id="d749c-132">Diretrizes de codificação segura</span><span class="sxs-lookup"><span data-stu-id="d749c-132">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
