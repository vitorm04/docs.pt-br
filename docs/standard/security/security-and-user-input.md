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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 27818d5e1779cd6e10e11830f91a20a3e638639a
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44127739"
---
# <a name="security-and-user-input"></a><span data-ttu-id="4d26d-102">Segurança e entrada do usuário</span><span class="sxs-lookup"><span data-stu-id="4d26d-102">Security and User Input</span></span>
<span data-ttu-id="4d26d-103">Dados de usuário, que é qualquer tipo de entrada (dados de uma solicitação da Web ou URL de entrada para controles de um aplicativo do Microsoft Windows Forms e assim por diante), negativamente pode influenciar o código porque frequentemente esses dados são usados diretamente como parâmetros para chamar outro código.</span><span class="sxs-lookup"><span data-stu-id="4d26d-103">User data, which is any kind of input (data from a Web request or URL, input to controls of a Microsoft Windows Forms application, and so on), can adversely influence code because often that data is used directly as parameters to call other code.</span></span> <span data-ttu-id="4d26d-104">Essa situação é análoga ao código malicioso chame seu código com parâmetros estranhos e as mesmas precauções devem ser tomadas.</span><span class="sxs-lookup"><span data-stu-id="4d26d-104">This situation is analogous to malicious code calling your code with strange parameters, and the same precautions should be taken.</span></span> <span data-ttu-id="4d26d-105">Entrada do usuário é, na verdade, mais difícil tornar segura porque não há nenhum quadro de pilha para rastrear a presença de dados potencialmente não confiáveis.</span><span class="sxs-lookup"><span data-stu-id="4d26d-105">User input is actually harder to make safe because there is no stack frame to trace the presence of the potentially untrusted data.</span></span>  
  
 <span data-ttu-id="4d26d-106">Eles estão entre os bugs de segurança mais sutil e mais difíceis de localizar porque, embora eles podem existir em código aparentemente não relacionado à segurança, eles são um gateway para passar dados inválidos por meio de outro código.</span><span class="sxs-lookup"><span data-stu-id="4d26d-106">These are among the subtlest and hardest security bugs to find because, although they can exist in code that is seemingly unrelated to security, they are a gateway to pass bad data through to other code.</span></span> <span data-ttu-id="4d26d-107">Para procurar esses bugs, siga qualquer tipo de dados de entrada, imagine o que o intervalo de valores possíveis pode ser e considere se o código vendo esses dados pode lidar com todos esses casos.</span><span class="sxs-lookup"><span data-stu-id="4d26d-107">To look for these bugs, follow any kind of input data, imagine what the range of possible values might be, and consider whether the code seeing this data can handle all those cases.</span></span> <span data-ttu-id="4d26d-108">Você pode corrigir esses bugs por meio do intervalo de verificação e rejeitar qualquer entrada que o código não pode manipular.</span><span class="sxs-lookup"><span data-stu-id="4d26d-108">You can fix these bugs through range checking and rejecting any input the code cannot handle.</span></span>  
  
 <span data-ttu-id="4d26d-109">Algumas considerações importantes que envolvem dados de usuário incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="4d26d-109">Some important considerations involving user data include the following:</span></span>  
  
-   <span data-ttu-id="4d26d-110">Qualquer dado de usuário em uma resposta do servidor é executado no contexto do site do servidor no cliente.</span><span class="sxs-lookup"><span data-stu-id="4d26d-110">Any user data in a server response runs in the context of the server's site on the client.</span></span> <span data-ttu-id="4d26d-111">Se seu servidor Web usa dados de usuário e o insere na página da Web retornada, ele pode, por exemplo, incluir um  **\<script >** de marca e executar como se do servidor.</span><span class="sxs-lookup"><span data-stu-id="4d26d-111">If your Web server takes user data and inserts it into the returned Web page, it might, for example, include a **\<script>** tag and run as if from the server.</span></span>  
  
-   <span data-ttu-id="4d26d-112">Lembre-se de que o cliente pode solicitar qualquer URL.</span><span class="sxs-lookup"><span data-stu-id="4d26d-112">Remember that the client can request any URL.</span></span>  
  
-   <span data-ttu-id="4d26d-113">Considere caminhos complicados ou é inválidos:</span><span class="sxs-lookup"><span data-stu-id="4d26d-113">Consider tricky or invalid paths:</span></span>  
  
    -   <span data-ttu-id="4d26d-114">.. \, caminhos extremamente longos.</span><span class="sxs-lookup"><span data-stu-id="4d26d-114">..\ , extremely long paths.</span></span>  
  
    -   <span data-ttu-id="4d26d-115">Uso de caracteres curinga (\*).</span><span class="sxs-lookup"><span data-stu-id="4d26d-115">Use of wild card characters (\*).</span></span>  
  
    -   <span data-ttu-id="4d26d-116">Expansão de token (% % token).</span><span class="sxs-lookup"><span data-stu-id="4d26d-116">Token expansion (%token%).</span></span>  
  
    -   <span data-ttu-id="4d26d-117">Formulários estranhos dos caminhos com significado especial.</span><span class="sxs-lookup"><span data-stu-id="4d26d-117">Strange forms of paths with special meaning.</span></span>  
  
    -   <span data-ttu-id="4d26d-118">Alternativa de nomes de fluxo de sistema de arquivos, como `filename::$DATA`.</span><span class="sxs-lookup"><span data-stu-id="4d26d-118">Alternate file system stream names such as `filename::$DATA`.</span></span>  
  
    -   <span data-ttu-id="4d26d-119">Curto versões dos nomes de arquivo, como `longfi~1` para `longfilename`.</span><span class="sxs-lookup"><span data-stu-id="4d26d-119">Short versions of file names such as `longfi~1` for `longfilename`.</span></span>  
  
-   <span data-ttu-id="4d26d-120">Lembre-se de que Eval(userdata) pode fazer qualquer coisa.</span><span class="sxs-lookup"><span data-stu-id="4d26d-120">Remember that Eval(userdata) can do anything.</span></span>  
  
-   <span data-ttu-id="4d26d-121">Tenha cuidado de associação tardia a um nome que inclui alguns dados do usuário.</span><span class="sxs-lookup"><span data-stu-id="4d26d-121">Be wary of late binding to a name that includes some user data.</span></span>  
  
-   <span data-ttu-id="4d26d-122">Se você estiver lidando com dados da Web, considere as diversas formas de escape que é permitido, incluindo:</span><span class="sxs-lookup"><span data-stu-id="4d26d-122">If you are dealing with Web data, consider the various forms of escapes that are permissible, including:</span></span>  
  
    -   <span data-ttu-id="4d26d-123">Escapa hexadecimal (% nn).</span><span class="sxs-lookup"><span data-stu-id="4d26d-123">Hexadecimal escapes (%nn).</span></span>  
  
    -   <span data-ttu-id="4d26d-124">Escapes de Unicode (% nnn).</span><span class="sxs-lookup"><span data-stu-id="4d26d-124">Unicode escapes (%nnn).</span></span>  
  
    -   <span data-ttu-id="4d26d-125">Escapa extensa de UTF-8 (% nn % nn).</span><span class="sxs-lookup"><span data-stu-id="4d26d-125">Overlong UTF-8 escapes (%nn%nn).</span></span>  
  
    -   <span data-ttu-id="4d26d-126">Escapes de duplos (% nn se torna mmnn %, onde % mm é o escape para '% s').</span><span class="sxs-lookup"><span data-stu-id="4d26d-126">Double escapes (%nn becomes %mmnn, where %mm is the escape for '%').</span></span>  
  
-   <span data-ttu-id="4d26d-127">Esteja atento a nomes de usuário que podem ter mais de um formato canônico.</span><span class="sxs-lookup"><span data-stu-id="4d26d-127">Be wary of user names that might have more than one canonical format.</span></span> <span data-ttu-id="4d26d-128">Por exemplo, você geralmente pode usar ambos o MYDOMAIN\\*nome de usuário* formulário ou o *username* @mydomain.example.com formulário.</span><span class="sxs-lookup"><span data-stu-id="4d26d-128">For example, you can often use either the MYDOMAIN\\*username* form or the *username*@mydomain.example.com form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d26d-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4d26d-129">See also</span></span>

- [<span data-ttu-id="4d26d-130">Diretrizes de codificação segura</span><span class="sxs-lookup"><span data-stu-id="4d26d-130">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
