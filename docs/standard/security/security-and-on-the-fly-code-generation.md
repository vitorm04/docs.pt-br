---
title: Segurança e geração de código durante a execução
description: Gerar código em nome de código de menor confiança que é executado em uma confiança superior é uma preocupação de segurança, especialmente quando um chamador pode influenciar a geração de código.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- code security, on-the-fly code generation
- on-the-fly code generation
- security [.NET Framework], on-the-fly code generation
- secure coding, on-the-fly code generation
ms.assetid: 6d221724-bb21-4d76-90c3-0ee2a2e69be2
ms.openlocfilehash: 34ebda27a81ca29ebb27a721b77b735a12be882e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186794"
---
# <a name="security-and-on-the-fly-code-generation"></a><span data-ttu-id="a30d8-103">Segurança e geração de código durante a execução</span><span class="sxs-lookup"><span data-stu-id="a30d8-103">Security and On-the-Fly Code Generation</span></span>
<span data-ttu-id="a30d8-104">Algumas bibliotecas operam gerando código e executando-o para executar alguma operação para o chamador.</span><span class="sxs-lookup"><span data-stu-id="a30d8-104">Some libraries operate by generating code and running it to perform some operation for the caller.</span></span> <span data-ttu-id="a30d8-105">O problema básico é gerar código em nome de código de menor confiança e executá-lo em uma confiança superior.</span><span class="sxs-lookup"><span data-stu-id="a30d8-105">The basic problem is generating code on behalf of lesser-trust code and running it at a higher trust.</span></span> <span data-ttu-id="a30d8-106">O problema se agrava quando o chamador pode influenciar a geração de código, então você deve garantir que apenas o código que você considera seguro seja gerado.</span><span class="sxs-lookup"><span data-stu-id="a30d8-106">The problem worsens when the caller can influence code generation, so you must ensure that only code you consider safe is generated.</span></span>  
  
 <span data-ttu-id="a30d8-107">Você precisa saber exatamente que código você está gerando o tempo todo.</span><span class="sxs-lookup"><span data-stu-id="a30d8-107">You need to know exactly what code you are generating at all times.</span></span> <span data-ttu-id="a30d8-108">Isso significa que você deve ter controles rigorosos sobre quaisquer valores que você obtenha de um usuário, sejam eles strings fechados com aspas (que devem ser escapadas para que eles não possam incluir elementos de código inesperados), identificadores (que devem ser verificados para verificar se eles são válidos identificadores), ou qualquer outra coisa.</span><span class="sxs-lookup"><span data-stu-id="a30d8-108">This means that you must have strict controls on any values that you get from a user, be they quote-enclosed strings (which should be escaped so they cannot include unexpected code elements), identifiers (which should be checked to verify that they are valid identifiers), or anything else.</span></span> <span data-ttu-id="a30d8-109">Os identificadores podem ser perigosos porque um conjunto compilado pode ser modificado para que seus identificadores contenham caracteres estranhos, o que provavelmente irá quebrá-lo (embora isso raramente seja uma vulnerabilidade de segurança).</span><span class="sxs-lookup"><span data-stu-id="a30d8-109">Identifiers can be dangerous because a compiled assembly can be modified so that its identifiers contain strange characters, which will probably break it (although this is rarely a security vulnerability).</span></span>  
  
 <span data-ttu-id="a30d8-110">Recomenda-se que você gere código com eitação de reflexão, o que muitas vezes ajuda a evitar muitos desses problemas.</span><span class="sxs-lookup"><span data-stu-id="a30d8-110">It is recommended that you generate code with reflection emit, which often helps you avoid many of these problems.</span></span>  
  
 <span data-ttu-id="a30d8-111">Ao compilar o código, considere se há alguma maneira de um programa malicioso modificá-lo.</span><span class="sxs-lookup"><span data-stu-id="a30d8-111">When you compile the code, consider whether there is some way a malicious program could modify it.</span></span> <span data-ttu-id="a30d8-112">Existe uma pequena janela de tempo durante a qual o código malicioso pode alterar o código-fonte no disco antes que o compilador o leia ou antes que seu código carregue o arquivo .dll?</span><span class="sxs-lookup"><span data-stu-id="a30d8-112">Is there a small window of time during which malicious code can change source code on disk before the compiler reads it or before your code loads the .dll file?</span></span> <span data-ttu-id="a30d8-113">Nesse caso, você deve proteger o diretório que contém esses arquivos, usando uma Lista de Controle de Acesso no sistema de arquivos, conforme apropriado.</span><span class="sxs-lookup"><span data-stu-id="a30d8-113">If so, you must protect the directory containing these files, using an Access Control List in the file system, as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a30d8-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="a30d8-114">See also</span></span>

- [<span data-ttu-id="a30d8-115">Diretrizes de codificação segura</span><span class="sxs-lookup"><span data-stu-id="a30d8-115">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
