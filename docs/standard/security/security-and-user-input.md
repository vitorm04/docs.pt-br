---
title: Segurança e entrada do usuário
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET Framework], user input
- user input, security
- secure coding, user input
- code security, user input
ms.assetid: 9141076a-96c9-4b01-93de-366bb1d858bc
ms.openlocfilehash: 0d34b06b44241feb7d6e3c8f76447b861563cfdc
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705854"
---
# <a name="security-and-user-input"></a><span data-ttu-id="4e3f0-102">Segurança e entrada do usuário</span><span class="sxs-lookup"><span data-stu-id="4e3f0-102">Security and User Input</span></span>

<span data-ttu-id="4e3f0-103">Os dados do usuário, que são qualquer tipo de entrada (dados de uma solicitação da Web ou URL, entrada para controles de um aplicativo Microsoft Windows Forms e assim por diante) podem influenciar o código de forma adversa, pois geralmente esses dados são usados diretamente como parâmetros para chamar outro código.</span><span class="sxs-lookup"><span data-stu-id="4e3f0-103">User data, which is any kind of input (data from a Web request or URL, input to controls of a Microsoft Windows Forms application, and so on), can adversely influence code because often that data is used directly as parameters to call other code.</span></span> <span data-ttu-id="4e3f0-104">Essa situação é análoga ao código mal-intencionado que chama seu código com parâmetros estranhos e as mesmas precauções devem ser tomadas.</span><span class="sxs-lookup"><span data-stu-id="4e3f0-104">This situation is analogous to malicious code calling your code with strange parameters, and the same precautions should be taken.</span></span> <span data-ttu-id="4e3f0-105">A entrada do usuário é realmente mais difícil de se tornar segura, pois não há um quadro de pilha para rastrear a presença dos dados potencialmente não confiáveis.</span><span class="sxs-lookup"><span data-stu-id="4e3f0-105">User input is actually harder to make safe because there is no stack frame to trace the presence of the potentially untrusted data.</span></span>

<span data-ttu-id="4e3f0-106">Esses são os bugs de segurança mais sutis e difíceis de serem encontrados porque, embora possam existir em código que pareça não estar relacionado à segurança, eles são um gateway para passar dados inválidos para outro código.</span><span class="sxs-lookup"><span data-stu-id="4e3f0-106">These are among the subtlest and hardest security bugs to find because, although they can exist in code that is seemingly unrelated to security, they are a gateway to pass bad data through to other code.</span></span> <span data-ttu-id="4e3f0-107">Para procurar esses bugs, siga qualquer tipo de dado de entrada, imagine o que é o intervalo de possíveis valores e considere se o código que vê esses dados pode lidar com todos esses casos.</span><span class="sxs-lookup"><span data-stu-id="4e3f0-107">To look for these bugs, follow any kind of input data, imagine what the range of possible values might be, and consider whether the code seeing this data can handle all those cases.</span></span> <span data-ttu-id="4e3f0-108">Você pode corrigir esses bugs por meio da verificação de intervalo e rejeitar qualquer entrada que o código não possa manipular.</span><span class="sxs-lookup"><span data-stu-id="4e3f0-108">You can fix these bugs through range checking and rejecting any input the code cannot handle.</span></span>

<span data-ttu-id="4e3f0-109">Algumas considerações importantes envolvendo os dados do usuário incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="4e3f0-109">Some important considerations involving user data include the following:</span></span>

- <span data-ttu-id="4e3f0-110">Qualquer dado de usuário em uma resposta de servidor é executado no contexto do site do servidor no cliente.</span><span class="sxs-lookup"><span data-stu-id="4e3f0-110">Any user data in a server response runs in the context of the server's site on the client.</span></span> <span data-ttu-id="4e3f0-111">Se o seu servidor Web usa os dados do usuário e os insere na página da Web retornada, ele pode, por exemplo, incluir um **script de\<** marca e executar como se fosse no servidor.</span><span class="sxs-lookup"><span data-stu-id="4e3f0-111">If your Web server takes user data and inserts it into the returned Web page, it might, for example, include a **\<script>** tag and run as if from the server.</span></span>

- <span data-ttu-id="4e3f0-112">Lembre-se de que o cliente pode solicitar qualquer URL.</span><span class="sxs-lookup"><span data-stu-id="4e3f0-112">Remember that the client can request any URL.</span></span>

- <span data-ttu-id="4e3f0-113">Considere caminhos complicados ou inválidos:</span><span class="sxs-lookup"><span data-stu-id="4e3f0-113">Consider tricky or invalid paths:</span></span>

  - <span data-ttu-id="4e3f0-114">.. \, caminhos extremamente longos.</span><span class="sxs-lookup"><span data-stu-id="4e3f0-114">..\ , extremely long paths.</span></span>

  - <span data-ttu-id="4e3f0-115">Uso de caracteres curinga (\*).</span><span class="sxs-lookup"><span data-stu-id="4e3f0-115">Use of wild card characters (\*).</span></span>

  - <span data-ttu-id="4e3f0-116">Expansão de token (% token%).</span><span class="sxs-lookup"><span data-stu-id="4e3f0-116">Token expansion (%token%).</span></span>

  - <span data-ttu-id="4e3f0-117">Formas estranhas de caminhos com significado especial.</span><span class="sxs-lookup"><span data-stu-id="4e3f0-117">Strange forms of paths with special meaning.</span></span>

  - <span data-ttu-id="4e3f0-118">Nomes de fluxo do sistema de arquivos alternativos, como `filename::$DATA`.</span><span class="sxs-lookup"><span data-stu-id="4e3f0-118">Alternate file system stream names such as `filename::$DATA`.</span></span>

  - <span data-ttu-id="4e3f0-119">Versões curtas de nomes de arquivos, como `longfi~1` para `longfilename`.</span><span class="sxs-lookup"><span data-stu-id="4e3f0-119">Short versions of file names such as `longfi~1` for `longfilename`.</span></span>

- <span data-ttu-id="4e3f0-120">Lembre-se de que Eval (UserData) pode fazer qualquer coisa.</span><span class="sxs-lookup"><span data-stu-id="4e3f0-120">Remember that Eval(userdata) can do anything.</span></span>

- <span data-ttu-id="4e3f0-121">Tenha cuidado com a associação tardia a um nome que inclua alguns dados do usuário.</span><span class="sxs-lookup"><span data-stu-id="4e3f0-121">Be wary of late binding to a name that includes some user data.</span></span>

- <span data-ttu-id="4e3f0-122">Se você estiver lidando com dados da Web, considere as várias formas de escapes que são permitidas, incluindo:</span><span class="sxs-lookup"><span data-stu-id="4e3f0-122">If you are dealing with Web data, consider the various forms of escapes that are permissible, including:</span></span>

  - <span data-ttu-id="4e3f0-123">Escapes hexadecimais (% nn).</span><span class="sxs-lookup"><span data-stu-id="4e3f0-123">Hexadecimal escapes (%nn).</span></span>

  - <span data-ttu-id="4e3f0-124">Escapes Unicode (% nnn).</span><span class="sxs-lookup"><span data-stu-id="4e3f0-124">Unicode escapes (%nnn).</span></span>

  - <span data-ttu-id="4e3f0-125">Escapes UTF-8 longos (% nn% NN).</span><span class="sxs-lookup"><span data-stu-id="4e3f0-125">Overlong UTF-8 escapes (%nn%nn).</span></span>

  - <span data-ttu-id="4e3f0-126">Escapes duplos (% nn torna-se% mmnn, em que% mm é o escape para '% ').</span><span class="sxs-lookup"><span data-stu-id="4e3f0-126">Double escapes (%nn becomes %mmnn, where %mm is the escape for '%').</span></span>

- <span data-ttu-id="4e3f0-127">Tenha cuidado com nomes de usuário que possam ter mais de um formato canônico.</span><span class="sxs-lookup"><span data-stu-id="4e3f0-127">Be wary of user names that might have more than one canonical format.</span></span> <span data-ttu-id="4e3f0-128">Por exemplo, geralmente você pode usar o formulário de nome de *usuário* de\\de domínio ou o *nome de usuário*@mydomain.example.com formulário.</span><span class="sxs-lookup"><span data-stu-id="4e3f0-128">For example, you can often use either the MYDOMAIN\\*username* form or the *username*@mydomain.example.com form.</span></span>

## <a name="see-also"></a><span data-ttu-id="4e3f0-129">Veja também</span><span class="sxs-lookup"><span data-stu-id="4e3f0-129">See also</span></span>

- [<span data-ttu-id="4e3f0-130">Diretrizes de codificação segura</span><span class="sxs-lookup"><span data-stu-id="4e3f0-130">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
