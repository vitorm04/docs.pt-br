---
title: Segurança e geração de código durante a execução
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- code security, on-the-fly code generation
- on-the-fly code generation
- security [.NET Framework], on-the-fly code generation
- secure coding, on-the-fly code generation
ms.assetid: 6d221724-bb21-4d76-90c3-0ee2a2e69be2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ffb1081c80c31353ad38080ae16ef9f8a74b5481
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61860536"
---
# <a name="security-and-on-the-fly-code-generation"></a><span data-ttu-id="ee6ad-102">Segurança e geração de código durante a execução</span><span class="sxs-lookup"><span data-stu-id="ee6ad-102">Security and On-the-Fly Code Generation</span></span>
<span data-ttu-id="ee6ad-103">Algumas bibliotecas operam por geração de código e executá-lo para executar alguma operação para o chamador.</span><span class="sxs-lookup"><span data-stu-id="ee6ad-103">Some libraries operate by generating code and running it to perform some operation for the caller.</span></span> <span data-ttu-id="ee6ad-104">O problema básico é a geração de código em nome do código de confiança menor e executá-lo em uma relação de confiança mais alto.</span><span class="sxs-lookup"><span data-stu-id="ee6ad-104">The basic problem is generating code on behalf of lesser-trust code and running it at a higher trust.</span></span> <span data-ttu-id="ee6ad-105">O problema piora quando o chamador pode influenciar a geração de código, portanto, você deve garantir que somente o código que você considerar seguros é gerado.</span><span class="sxs-lookup"><span data-stu-id="ee6ad-105">The problem worsens when the caller can influence code generation, so you must ensure that only code you consider safe is generated.</span></span>  
  
 <span data-ttu-id="ee6ad-106">Você precisa saber exatamente o código que você está gerando em todos os momentos.</span><span class="sxs-lookup"><span data-stu-id="ee6ad-106">You need to know exactly what code you are generating at all times.</span></span> <span data-ttu-id="ee6ad-107">Isso significa que você deve ter controles estritos em quaisquer valores que você obteve de um usuário, sejam colocados de cotação de cadeias de caracteres (que devem ser substituídas para que elas não podem incluir elementos de código inesperado), identificadores (que devem ser verificados para verificar se eles são válidos identificadores), ou qualquer outra coisa.</span><span class="sxs-lookup"><span data-stu-id="ee6ad-107">This means that you must have strict controls on any values that you get from a user, be they quote-enclosed strings (which should be escaped so they cannot include unexpected code elements), identifiers (which should be checked to verify that they are valid identifiers), or anything else.</span></span> <span data-ttu-id="ee6ad-108">Identificadores podem ser perigosos porque um assembly compilado pode ser modificado para que seus identificadores contêm caracteres estranhos, o que provavelmente interromperá a ele (embora isso raramente é uma vulnerabilidade de segurança).</span><span class="sxs-lookup"><span data-stu-id="ee6ad-108">Identifiers can be dangerous because a compiled assembly can be modified so that its identifiers contain strange characters, which will probably break it (although this is rarely a security vulnerability).</span></span>  
  
 <span data-ttu-id="ee6ad-109">É recomendável que você gerar código com a reflexão emite, que geralmente ajuda a evitar muitos desses problemas.</span><span class="sxs-lookup"><span data-stu-id="ee6ad-109">It is recommended that you generate code with reflection emit, which often helps you avoid many of these problems.</span></span>  
  
 <span data-ttu-id="ee6ad-110">Quando você compila o código, considere se há alguma forma de que um programa mal-intencionado pode modificá-lo.</span><span class="sxs-lookup"><span data-stu-id="ee6ad-110">When you compile the code, consider whether there is some way a malicious program could modify it.</span></span> <span data-ttu-id="ee6ad-111">Há uma pequena janela de tempo durante o qual código mal-intencionado pode alterar o código-fonte no disco antes do compilador lê-lo ou antes de seu código carrega o arquivo. dll?</span><span class="sxs-lookup"><span data-stu-id="ee6ad-111">Is there a small window of time during which malicious code can change source code on disk before the compiler reads it or before your code loads the .dll file?</span></span> <span data-ttu-id="ee6ad-112">Nesse caso, você deve proteger o diretório que contém esses arquivos, usando uma lista de controle de acesso no sistema de arquivos, conforme apropriado.</span><span class="sxs-lookup"><span data-stu-id="ee6ad-112">If so, you must protect the directory containing these files, using an Access Control List in the file system, as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee6ad-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ee6ad-113">See also</span></span>

- [<span data-ttu-id="ee6ad-114">Diretrizes de codificação segura</span><span class="sxs-lookup"><span data-stu-id="ee6ad-114">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
