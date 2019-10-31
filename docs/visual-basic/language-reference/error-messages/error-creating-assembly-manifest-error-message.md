---
title: 'Erro na criação de manifesto do assembly: <error message>'
ms.date: 07/20/2015
f1_keywords:
- bc30140
- vbc30140
helpviewer_keywords:
- BC30140
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
ms.openlocfilehash: 7ccfb970a0e471b4a7e6808f041dfea2f386e7e9
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197128"
---
# <a name="error-creating-assembly-manifest-error-message"></a><span data-ttu-id="27c1c-102">Erro ao criar o manifesto do assembly: \<mensagem de erro ></span><span class="sxs-lookup"><span data-stu-id="27c1c-102">Error creating assembly manifest: \<error message></span></span>
<span data-ttu-id="27c1c-103">O compilador Visual Basic chama o vinculador do assembly (al. exe, também conhecido como ALink) para gerar um assembly com um manifesto.</span><span class="sxs-lookup"><span data-stu-id="27c1c-103">The Visual Basic compiler calls the Assembly Linker (Al.exe, also known as Alink) to generate an assembly with a manifest.</span></span> <span data-ttu-id="27c1c-104">O vinculador reportou um erro no estágio de pré-emissão da criação do assembly.</span><span class="sxs-lookup"><span data-stu-id="27c1c-104">The linker has reported an error in the pre-emission stage of creating the assembly.</span></span>  
  
 <span data-ttu-id="27c1c-105">Isso pode ocorrer se houver problemas com o arquivo de chave ou o contêiner de chave especificado.</span><span class="sxs-lookup"><span data-stu-id="27c1c-105">This can occur if there are problems with the key file or the key container specified.</span></span> <span data-ttu-id="27c1c-106">Para marcar totalmente um assembly, é necessário fornecer um arquivo de chave válido que contenha informações sobre as chaves públicas e privadas.</span><span class="sxs-lookup"><span data-stu-id="27c1c-106">To fully sign an assembly, you must provide a valid key file that contains information about the public and private keys.</span></span> <span data-ttu-id="27c1c-107">Para marcar um atraso em um assembly, é necessário marcar a caixa de seleção **Somente sinal de atraso** e fornecer um arquivo de chave válido que contenha informações sobre as informações de chave pública.</span><span class="sxs-lookup"><span data-stu-id="27c1c-107">To delay sign an assembly, you must select the **Delay sign only** check box and provide a valid key file that contains information about the public key information.</span></span> <span data-ttu-id="27c1c-108">A chave privada não é necessária quando um assembly estiver marcado com atraso.</span><span class="sxs-lookup"><span data-stu-id="27c1c-108">The private key is not necessary when an assembly is delay-signed.</span></span> <span data-ttu-id="27c1c-109">Para obter mais informações, consulte [Como assinar um assembly com um nome forte](../../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="27c1c-109">For more information, see [How to: Sign an Assembly with a Strong Name](../../../standard/assembly/sign-strong-name.md).</span></span>  
  
 <span data-ttu-id="27c1c-110">**ID do erro:** BC30140</span><span class="sxs-lookup"><span data-stu-id="27c1c-110">**Error ID:** BC30140</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="27c1c-111">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="27c1c-111">To correct this error</span></span>  
  
1. <span data-ttu-id="27c1c-112">Examine a mensagem de erro entre aspas e consulte o tópico [al. exe](../../../framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="27c1c-112">Examine the quoted error message and consult the topic [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span></span> <span data-ttu-id="27c1c-113">para ver o erro AL1019 mais explicações e conselhos</span><span class="sxs-lookup"><span data-stu-id="27c1c-113">for error AL1019 further explanation and advice</span></span>  
  
2. <span data-ttu-id="27c1c-114">Se o erro persistir, reúna informações sobre as circunstâncias e notifique o Microsoft Product Support Services.</span><span class="sxs-lookup"><span data-stu-id="27c1c-114">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27c1c-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="27c1c-115">See also</span></span>

- [<span data-ttu-id="27c1c-116">Como assinar um assembly com um nome forte</span><span class="sxs-lookup"><span data-stu-id="27c1c-116">How to: Sign an Assembly with a Strong Name</span></span>](../../../standard/assembly/sign-strong-name.md)
- [<span data-ttu-id="27c1c-117">Página de Assinatura, Designer de Projeto</span><span class="sxs-lookup"><span data-stu-id="27c1c-117">Signing Page, Project Designer</span></span>](/visualstudio/ide/reference/signing-page-project-designer)
- [<span data-ttu-id="27c1c-118">Al. exe</span><span class="sxs-lookup"><span data-stu-id="27c1c-118">Al.exe</span></span>](../../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="27c1c-119">Fale conosco</span><span class="sxs-lookup"><span data-stu-id="27c1c-119">Talk to Us</span></span>](/visualstudio/ide/feedback-options)
