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
ms.openlocfilehash: 858ee30479c959f30673725b4ba8088fcc2d8f3b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33581749"
---
# <a name="security-and-user-input"></a><span data-ttu-id="c8cf2-102">Segurança e entrada do usuário</span><span class="sxs-lookup"><span data-stu-id="c8cf2-102">Security and User Input</span></span>
<span data-ttu-id="c8cf2-103">Dados de usuário, que pode ser qualquer tipo de entrada (dados de uma solicitação da Web ou a URL de entrada para controles de um aplicativo do Microsoft Windows Forms e assim por diante), negativamente pode influenciar o código porque geralmente usados diretamente como parâmetros para chamar outro código.</span><span class="sxs-lookup"><span data-stu-id="c8cf2-103">User data, which is any kind of input (data from a Web request or URL, input to controls of a Microsoft Windows Forms application, and so on), can adversely influence code because often that data is used directly as parameters to call other code.</span></span> <span data-ttu-id="c8cf2-104">Essa situação é semelhante a chamar seu código com parâmetros estranhos um código mal-intencionado, e as mesmas precauções devem ser tomadas.</span><span class="sxs-lookup"><span data-stu-id="c8cf2-104">This situation is analogous to malicious code calling your code with strange parameters, and the same precautions should be taken.</span></span> <span data-ttu-id="c8cf2-105">Entrada do usuário é realmente difícil fazer seguro porque não há nenhum quadro de pilha para rastrear a presença de dados potencialmente não confiáveis.</span><span class="sxs-lookup"><span data-stu-id="c8cf2-105">User input is actually harder to make safe because there is no stack frame to trace the presence of the potentially untrusted data.</span></span>  
  
 <span data-ttu-id="c8cf2-106">Eles estão entre os bugs de segurança mais sutil e mais difícil localizar porque, embora eles podem existir em código aparentemente não relacionado à segurança, eles são um gateway para passar dados inválidos por meio de outro código.</span><span class="sxs-lookup"><span data-stu-id="c8cf2-106">These are among the subtlest and hardest security bugs to find because, although they can exist in code that is seemingly unrelated to security, they are a gateway to pass bad data through to other code.</span></span> <span data-ttu-id="c8cf2-107">Para procurar por esses erros, execute qualquer tipo de dados de entrada, imagine que o intervalo de valores possíveis pode ser e considere se o código de ver esses dados pode lidar com todos os casos.</span><span class="sxs-lookup"><span data-stu-id="c8cf2-107">To look for these bugs, follow any kind of input data, imagine what the range of possible values might be, and consider whether the code seeing this data can handle all those cases.</span></span> <span data-ttu-id="c8cf2-108">Você pode corrigir esses erros por meio de intervalo de verificação e rejeitar qualquer entrada que o código não pode tratar.</span><span class="sxs-lookup"><span data-stu-id="c8cf2-108">You can fix these bugs through range checking and rejecting any input the code cannot handle.</span></span>  
  
 <span data-ttu-id="c8cf2-109">Algumas considerações importantes que envolvem dados de usuário incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c8cf2-109">Some important considerations involving user data include the following:</span></span>  
  
-   <span data-ttu-id="c8cf2-110">Nenhum dado de usuário em uma resposta do servidor é executado no contexto do site do servidor no cliente.</span><span class="sxs-lookup"><span data-stu-id="c8cf2-110">Any user data in a server response runs in the context of the server's site on the client.</span></span> <span data-ttu-id="c8cf2-111">Se seu servidor Web usa dados de usuário e a insere na página da Web retornada, ele pode, por exemplo, incluir uma  **\<script >** marca e executar como se do servidor.</span><span class="sxs-lookup"><span data-stu-id="c8cf2-111">If your Web server takes user data and inserts it into the returned Web page, it might, for example, include a **\<script>** tag and run as if from the server.</span></span>  
  
-   <span data-ttu-id="c8cf2-112">Lembre-se de que o cliente pode solicitar qualquer URL.</span><span class="sxs-lookup"><span data-stu-id="c8cf2-112">Remember that the client can request any URL.</span></span>  
  
-   <span data-ttu-id="c8cf2-113">Considere os caminhos de difícil ou é inválidos:</span><span class="sxs-lookup"><span data-stu-id="c8cf2-113">Consider tricky or invalid paths:</span></span>  
  
    -   <span data-ttu-id="c8cf2-114">.. \, caminhos extremamente longos.</span><span class="sxs-lookup"><span data-stu-id="c8cf2-114">..\ , extremely long paths.</span></span>  
  
    -   <span data-ttu-id="c8cf2-115">Uso de caracteres curinga (\*).</span><span class="sxs-lookup"><span data-stu-id="c8cf2-115">Use of wild card characters (\*).</span></span>  
  
    -   <span data-ttu-id="c8cf2-116">Expansão de token (% % de token).</span><span class="sxs-lookup"><span data-stu-id="c8cf2-116">Token expansion (%token%).</span></span>  
  
    -   <span data-ttu-id="c8cf2-117">Formulários estranhos dos caminhos com significado especial.</span><span class="sxs-lookup"><span data-stu-id="c8cf2-117">Strange forms of paths with special meaning.</span></span>  
  
    -   <span data-ttu-id="c8cf2-118">Alternativas de nomes de fluxo de sistema de arquivos, como `filename::$DATA`.</span><span class="sxs-lookup"><span data-stu-id="c8cf2-118">Alternate file system stream names such as `filename::$DATA`.</span></span>  
  
    -   <span data-ttu-id="c8cf2-119">Abreviada versões dos nomes de arquivo, como `longfi~1` para `longfilename`.</span><span class="sxs-lookup"><span data-stu-id="c8cf2-119">Short versions of file names such as `longfi~1` for `longfilename`.</span></span>  
  
-   <span data-ttu-id="c8cf2-120">Lembre-se de que Eval(userdata) pode fazer nada.</span><span class="sxs-lookup"><span data-stu-id="c8cf2-120">Remember that Eval(userdata) can do anything.</span></span>  
  
-   <span data-ttu-id="c8cf2-121">Tenha cuidado de associação tardia a um nome que inclui alguns dados do usuário.</span><span class="sxs-lookup"><span data-stu-id="c8cf2-121">Be wary of late binding to a name that includes some user data.</span></span>  
  
-   <span data-ttu-id="c8cf2-122">Se você estiver lidando com dados da Web, considere as várias formas de escapa é permitidas, incluindo:</span><span class="sxs-lookup"><span data-stu-id="c8cf2-122">If you are dealing with Web data, consider the various forms of escapes that are permissible, including:</span></span>  
  
    -   <span data-ttu-id="c8cf2-123">Escapes hexadecimais (% nn).</span><span class="sxs-lookup"><span data-stu-id="c8cf2-123">Hexadecimal escapes (%nn).</span></span>  
  
    -   <span data-ttu-id="c8cf2-124">Escapes de Unicode (% nnn).</span><span class="sxs-lookup"><span data-stu-id="c8cf2-124">Unicode escapes (%nnn).</span></span>  
  
    -   <span data-ttu-id="c8cf2-125">Escapes de UTF-8 extensa (% nn % nn).</span><span class="sxs-lookup"><span data-stu-id="c8cf2-125">Overlong UTF-8 escapes (%nn%nn).</span></span>  
  
    -   <span data-ttu-id="c8cf2-126">Escapes de duplos (% nn se torna mmnn %, onde % mm é o escape para '% s').</span><span class="sxs-lookup"><span data-stu-id="c8cf2-126">Double escapes (%nn becomes %mmnn, where %mm is the escape for '%').</span></span>  
  
-   <span data-ttu-id="c8cf2-127">Tenha cuidado dos nomes de usuário que podem ter mais de um formato canônico.</span><span class="sxs-lookup"><span data-stu-id="c8cf2-127">Be wary of user names that might have more than one canonical format.</span></span> <span data-ttu-id="c8cf2-128">Por exemplo, você pode usar o domínio de MYDOMAIN geralmente\\*username* formulário ou o *username* @mydomain.example.com formulário.</span><span class="sxs-lookup"><span data-stu-id="c8cf2-128">For example, you can often use either the MYDOMAIN\\*username* form or the *username*@mydomain.example.com form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8cf2-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c8cf2-129">See Also</span></span>  
 [<span data-ttu-id="c8cf2-130">Diretrizes de codificação segura</span><span class="sxs-lookup"><span data-stu-id="c8cf2-130">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
