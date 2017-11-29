---
title: "Não é possível emitir o assembly: &lt;mensagem de erro&gt;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords: BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9dcf3d4bec379faa5783ca17847b91f9739df598
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="unable-to-emit-assembly-lterror-messagegt"></a><span data-ttu-id="9c06c-102">Não é possível emitir o assembly: &lt;mensagem de erro&gt;</span><span class="sxs-lookup"><span data-stu-id="9c06c-102">Unable to emit assembly: &lt;error message&gt;</span></span>
<span data-ttu-id="9c06c-103">O compilador [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] chama o Assembly Linker (Al.exe, também conhecido como Alink) para gerar um assembly com um manifesto, com o vinculador relatando um erro no estágio de emissão da criação do assembly.</span><span class="sxs-lookup"><span data-stu-id="9c06c-103">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler calls the Assembly Linker (Al.exe, also known as Alink) to generate an assembly with a manifest, with the linker reporting an error in the emission stage of creating the assembly.</span></span>  
  
 <span data-ttu-id="9c06c-104">**ID do erro:** BC30145</span><span class="sxs-lookup"><span data-stu-id="9c06c-104">**Error ID:** BC30145</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9c06c-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="9c06c-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="9c06c-106">Examine a mensagem de erro citada e consulte o tópico [Al.exe ferramenta erros e avisos](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) para obter mais explicações e conselhos.</span><span class="sxs-lookup"><span data-stu-id="9c06c-106">Examine the quoted error message and consult the topic [Al.exe Tool Errors and Warnings](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) for further explanation and advice.</span></span>  
  
2.  <span data-ttu-id="9c06c-107">Tente assinar o assembly manualmente, usando o [Al.exe (Assembly Linker)](https://msdn.microsoft.com/library/c405shex) ou [Sn.exe (ferramenta de nome forte)](https://msdn.microsoft.com/library/k5b5tt23).</span><span class="sxs-lookup"><span data-stu-id="9c06c-107">Try signing the assembly manually, using either the [Al.exe (Assembly Linker)](https://msdn.microsoft.com/library/c405shex) or the [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23).</span></span>  
  
3.  <span data-ttu-id="9c06c-108">Se o erro persistir, reúna informações sobre as circunstâncias e notifique o Microsoft Product Support Services.</span><span class="sxs-lookup"><span data-stu-id="9c06c-108">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
### <a name="to-sign-the-assembly-manually"></a><span data-ttu-id="9c06c-109">Para assinar o assembly manualmente</span><span class="sxs-lookup"><span data-stu-id="9c06c-109">To sign the assembly manually</span></span>  
  
1.  <span data-ttu-id="9c06c-110">Use o [Sn.exe (ferramenta de nome forte)](https://msdn.microsoft.com/library/k5b5tt23) para criar um arquivo de par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="9c06c-110">Use the [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23) to create a public/private key pair file.</span></span>  
  
     <span data-ttu-id="9c06c-111">Esse arquivo tem a extensão .snk.</span><span class="sxs-lookup"><span data-stu-id="9c06c-111">This file has a .snk extension.</span></span>  
  
2.  <span data-ttu-id="9c06c-112">Exclua a referência COM que está gerando o erro no projeto.</span><span class="sxs-lookup"><span data-stu-id="9c06c-112">Delete the COM reference that is generating the error from your project.</span></span>  
  
3.  <span data-ttu-id="9c06c-113">Do Windows **iniciar** , aponte para **programas**, aponte para **Microsoft Visual Studio 2008**, aponte para **ferramentas do Visual Studio**, e em seguida, clique em **Prompt de comando do Visual Studio 2008**.</span><span class="sxs-lookup"><span data-stu-id="9c06c-113">From the Windows **Start** menu, point to **Programs**, point to **Microsoft Visual Studio 2008**, point to **Visual Studio Tools**, and then click **Visual Studio 2008 Command Prompt**.</span></span>  
  
4.  <span data-ttu-id="9c06c-114">Acesse o diretório onde deseja colocar o wrapper do assembly.</span><span class="sxs-lookup"><span data-stu-id="9c06c-114">Move to the directory where you want to place your assembly wrapper.</span></span>  
  
5.  <span data-ttu-id="9c06c-115">Digite o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="9c06c-115">Type the following code.</span></span>  
  
    ```  
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>  
    ```  
  
     <span data-ttu-id="9c06c-116">Um exemplo do código que pode ser inserido seria o seguinte.</span><span class="sxs-lookup"><span data-stu-id="9c06c-116">An example of the code you might enter would be the following.</span></span>  
  
    ```  
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"  
    ```  
  
     <span data-ttu-id="9c06c-117">Use aspas duplas (") se um caminho ou arquivo contiver espaços.</span><span class="sxs-lookup"><span data-stu-id="9c06c-117">Use double quotation marks (") if a path or file contains spaces.</span></span>  
  
6.  <span data-ttu-id="9c06c-118">Em [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], inclua uma referência .NET Assembly para o arquivo que acabou de ser criado.</span><span class="sxs-lookup"><span data-stu-id="9c06c-118">In [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], add a .NET Assembly reference to the file you just created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c06c-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9c06c-119">See Also</span></span>  
 [<span data-ttu-id="9c06c-120">Al.exe (Assembly Linker)</span><span class="sxs-lookup"><span data-stu-id="9c06c-120">Al.exe (Assembly Linker)</span></span>](https://msdn.microsoft.com/library/c405shex)  
 [<span data-ttu-id="9c06c-121">Ferramenta de Al.exe erros e avisos</span><span class="sxs-lookup"><span data-stu-id="9c06c-121">Al.exe Tool Errors and Warnings</span></span>](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b)  
 [<span data-ttu-id="9c06c-122">Sn.exe (Ferramenta Nome Forte)</span><span class="sxs-lookup"><span data-stu-id="9c06c-122">Sn.exe (Strong Name Tool)</span></span>](https://msdn.microsoft.com/library/k5b5tt23)  
 [<span data-ttu-id="9c06c-123">Como criar um par de chaves pública/privada</span><span class="sxs-lookup"><span data-stu-id="9c06c-123">How to: Create a Public-Private Key Pair</span></span>](http://msdn.microsoft.com/library/05026813-f3bd-4d7c-9e0b-fc588eb3d114)  
 [<span data-ttu-id="9c06c-124">Fale conosco</span><span class="sxs-lookup"><span data-stu-id="9c06c-124">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
