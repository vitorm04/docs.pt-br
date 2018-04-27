---
title: 'Erro ao criar o manifesto do assembly: &lt;mensagem de erro&gt;'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30140
- vbc30140
helpviewer_keywords:
- BC30140
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4032bbcbf9924eb5aad4e2cb1a6e74df9a472eca
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="error-creating-assembly-manifest-lterror-messagegt"></a><span data-ttu-id="51a5c-102">Erro ao criar o manifesto do assembly: &lt;mensagem de erro&gt;</span><span class="sxs-lookup"><span data-stu-id="51a5c-102">Error creating assembly manifest: &lt;error message&gt;</span></span>
<span data-ttu-id="51a5c-103">O compilador do Visual Basic chama o vinculador de Assembly (Al.exe, também conhecido como Alink) para gerar um assembly com um manifesto.</span><span class="sxs-lookup"><span data-stu-id="51a5c-103">The Visual Basic compiler calls the Assembly Linker (Al.exe, also known as Alink) to generate an assembly with a manifest.</span></span> <span data-ttu-id="51a5c-104">O vinculador reportou um erro no estágio de pré-emissão da criação do assembly.</span><span class="sxs-lookup"><span data-stu-id="51a5c-104">The linker has reported an error in the pre-emission stage of creating the assembly.</span></span>  
  
 <span data-ttu-id="51a5c-105">Isso pode ocorrer se houver problemas com o arquivo de chave ou o contêiner de chave especificado.</span><span class="sxs-lookup"><span data-stu-id="51a5c-105">This can occur if there are problems with the key file or the key container specified.</span></span> <span data-ttu-id="51a5c-106">Para marcar totalmente um assembly, é necessário fornecer um arquivo de chave válido que contenha informações sobre as chaves públicas e privadas.</span><span class="sxs-lookup"><span data-stu-id="51a5c-106">To fully sign an assembly, you must provide a valid key file that contains information about the public and private keys.</span></span> <span data-ttu-id="51a5c-107">Para marcar um atraso em um assembly, é necessário marcar a caixa de seleção **Somente sinal de atraso** e fornecer um arquivo de chave válido que contenha informações sobre as informações de chave pública.</span><span class="sxs-lookup"><span data-stu-id="51a5c-107">To delay sign an assembly, you must select the **Delay sign only** check box and provide a valid key file that contains information about the public key information.</span></span> <span data-ttu-id="51a5c-108">A chave privada não é necessária quando um assembly estiver marcado com atraso.</span><span class="sxs-lookup"><span data-stu-id="51a5c-108">The private key is not necessary when an assembly is delay-signed.</span></span> <span data-ttu-id="51a5c-109">Para obter mais informações, consulte [Como assinar um assembly com um nome forte](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="51a5c-109">For more information, see [How to: Sign an Assembly with a Strong Name](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
 <span data-ttu-id="51a5c-110">**ID do erro:** BC30140</span><span class="sxs-lookup"><span data-stu-id="51a5c-110">**Error ID:** BC30140</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="51a5c-111">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="51a5c-111">To correct this error</span></span>  
  
1.  <span data-ttu-id="51a5c-112">Examine a mensagem de erro citada e consulte o tópico [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="51a5c-112">Examine the quoted error message and consult the topic [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span></span> <span data-ttu-id="51a5c-113">Erro AL1019 mais explicações e conselhos</span><span class="sxs-lookup"><span data-stu-id="51a5c-113">for error AL1019 further explanation and advice</span></span>  
  
2.  <span data-ttu-id="51a5c-114">Se o erro persistir, reúna informações sobre as circunstâncias e notifique o Microsoft Product Support Services.</span><span class="sxs-lookup"><span data-stu-id="51a5c-114">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51a5c-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="51a5c-115">See Also</span></span>  
 [<span data-ttu-id="51a5c-116">Como assinar um assembly com um nome forte</span><span class="sxs-lookup"><span data-stu-id="51a5c-116">How to: Sign an Assembly with a Strong Name</span></span>](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)  
 [<span data-ttu-id="51a5c-117">Página de Assinatura, Designer de Projeto</span><span class="sxs-lookup"><span data-stu-id="51a5c-117">Signing Page, Project Designer</span></span>](/visualstudio/ide/reference/signing-page-project-designer)  
 <span data-ttu-id="51a5c-118">[Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="51a5c-118">[Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span></span>  
 [<span data-ttu-id="51a5c-119">Fale conosco</span><span class="sxs-lookup"><span data-stu-id="51a5c-119">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
