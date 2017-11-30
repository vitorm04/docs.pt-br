---
title: 'Erro ao criar o manifesto do assembly: &lt;mensagem de erro&gt;'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30140
- vbc30140
helpviewer_keywords: BC30140
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d846ef88f0c36b49e79b9d11252fcef419dfa0ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="error-creating-assembly-manifest-lterror-messagegt"></a><span data-ttu-id="94cc4-102">Erro ao criar o manifesto do assembly: &lt;mensagem de erro&gt;</span><span class="sxs-lookup"><span data-stu-id="94cc4-102">Error creating assembly manifest: &lt;error message&gt;</span></span>
<span data-ttu-id="94cc4-103">O compilador [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] chama o Assembly Linker (Al.exe, também conhecido como Alink) para gerar um assembly com um manifesto.</span><span class="sxs-lookup"><span data-stu-id="94cc4-103">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler calls the Assembly Linker (Al.exe, also known as Alink) to generate an assembly with a manifest.</span></span> <span data-ttu-id="94cc4-104">O vinculador reportou um erro no estágio de pré-emissão da criação do assembly.</span><span class="sxs-lookup"><span data-stu-id="94cc4-104">The linker has reported an error in the pre-emission stage of creating the assembly.</span></span>  
  
 <span data-ttu-id="94cc4-105">Isso pode ocorrer se houver problemas com o arquivo de chave ou o contêiner de chave especificado.</span><span class="sxs-lookup"><span data-stu-id="94cc4-105">This can occur if there are problems with the key file or the key container specified.</span></span> <span data-ttu-id="94cc4-106">Para marcar totalmente um assembly, é necessário fornecer um arquivo de chave válido que contenha informações sobre as chaves públicas e privadas.</span><span class="sxs-lookup"><span data-stu-id="94cc4-106">To fully sign an assembly, you must provide a valid key file that contains information about the public and private keys.</span></span> <span data-ttu-id="94cc4-107">Para marcar um atraso em um assembly, é necessário marcar a caixa de seleção **Somente sinal de atraso** e fornecer um arquivo de chave válido que contenha informações sobre as informações de chave pública.</span><span class="sxs-lookup"><span data-stu-id="94cc4-107">To delay sign an assembly, you must select the **Delay sign only** check box and provide a valid key file that contains information about the public key information.</span></span> <span data-ttu-id="94cc4-108">A chave privada não é necessária quando um assembly estiver marcado com atraso.</span><span class="sxs-lookup"><span data-stu-id="94cc4-108">The private key is not necessary when an assembly is delay-signed.</span></span> <span data-ttu-id="94cc4-109">Para obter mais informações, consulte [como: assinar um Assembly (Visual Studio)](http://msdn.microsoft.com/en-us/f468a7d3-234c-4353-924d-8e0ae5896564).</span><span class="sxs-lookup"><span data-stu-id="94cc4-109">For more information, see [How to: Sign an Assembly (Visual Studio)](http://msdn.microsoft.com/en-us/f468a7d3-234c-4353-924d-8e0ae5896564).</span></span>  
  
 <span data-ttu-id="94cc4-110">**ID do erro:** BC30140</span><span class="sxs-lookup"><span data-stu-id="94cc4-110">**Error ID:** BC30140</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="94cc4-111">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="94cc4-111">To correct this error</span></span>  
  
1.  <span data-ttu-id="94cc4-112">Examine a mensagem de erro citada e consulte o tópico [Al.exe ferramenta erros e avisos](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) para erro AL1019 para obter mais explicações e conselhos</span><span class="sxs-lookup"><span data-stu-id="94cc4-112">Examine the quoted error message and consult the topic [Al.exe Tool Errors and Warnings](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) for error AL1019 further explanation and advice</span></span>  
  
2.  <span data-ttu-id="94cc4-113">Se o erro persistir, reúna informações sobre as circunstâncias e notifique o Microsoft Product Support Services.</span><span class="sxs-lookup"><span data-stu-id="94cc4-113">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94cc4-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="94cc4-114">See Also</span></span>  
 [<span data-ttu-id="94cc4-115">Como Assinar um Assembly (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="94cc4-115">How to: Sign an Assembly (Visual Studio)</span></span>](http://msdn.microsoft.com/en-us/f468a7d3-234c-4353-924d-8e0ae5896564)  
 [<span data-ttu-id="94cc4-116">Página de Assinatura, Designer de Projeto</span><span class="sxs-lookup"><span data-stu-id="94cc4-116">Signing Page, Project Designer</span></span>](/visualstudio/ide/reference/signing-page-project-designer)  
 [<span data-ttu-id="94cc4-117">Al.exe (Assembly Linker)</span><span class="sxs-lookup"><span data-stu-id="94cc4-117">Al.exe (Assembly Linker)</span></span>](https://msdn.microsoft.com/library/c405shex)  
 [<span data-ttu-id="94cc4-118">Ferramenta de Al.exe erros e avisos</span><span class="sxs-lookup"><span data-stu-id="94cc4-118">Al.exe Tool Errors and Warnings</span></span>](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b)  
 [<span data-ttu-id="94cc4-119">Fale conosco</span><span class="sxs-lookup"><span data-stu-id="94cc4-119">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
