---
title: 'Não é possível emitir o assembly: &lt;mensagem de erro&gt;'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords:
- BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 59288ba7b4cec34cd2266d66aa931e92598e819a
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="unable-to-emit-assembly-lterror-messagegt"></a><span data-ttu-id="2c279-102">Não é possível emitir o assembly: &lt;mensagem de erro&gt;</span><span class="sxs-lookup"><span data-stu-id="2c279-102">Unable to emit assembly: &lt;error message&gt;</span></span>
<span data-ttu-id="2c279-103">O compilador do Visual Basic chama o Assembly Linker (Al.exe, também conhecido como Alink) para gerar um assembly com um manifesto, com o vinculador relatar um erro no estágio de emissão de criar o assembly.</span><span class="sxs-lookup"><span data-stu-id="2c279-103">The Visual Basic compiler calls the Assembly Linker (Al.exe, also known as Alink) to generate an assembly with a manifest, with the linker reporting an error in the emission stage of creating the assembly.</span></span>  
  
 <span data-ttu-id="2c279-104">**ID do erro:** BC30145</span><span class="sxs-lookup"><span data-stu-id="2c279-104">**Error ID:** BC30145</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2c279-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="2c279-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="2c279-106">Examine a mensagem de erro citada e consulte o tópico [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="2c279-106">Examine the quoted error message and consult the topic [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span></span> <span data-ttu-id="2c279-107">Para obter mais explicações e conselhos.</span><span class="sxs-lookup"><span data-stu-id="2c279-107">for further explanation and advice.</span></span>  
  
2.  <span data-ttu-id="2c279-108">Tente assinar o assembly manualmente, usando o [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) ou [Sn.exe (ferramenta de nome forte)](../../../framework/tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="2c279-108">Try signing the assembly manually, using either the [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) or the [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md).</span></span>  
  
3.  <span data-ttu-id="2c279-109">Se o erro persistir, reúna informações sobre as circunstâncias e notifique o Microsoft Product Support Services.</span><span class="sxs-lookup"><span data-stu-id="2c279-109">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
### <a name="to-sign-the-assembly-manually"></a><span data-ttu-id="2c279-110">Para assinar o assembly manualmente</span><span class="sxs-lookup"><span data-stu-id="2c279-110">To sign the assembly manually</span></span>  
  
1.  <span data-ttu-id="2c279-111">Use o [Sn.exe (ferramenta de nome forte)][Sn.exe (ferramenta de nome forte)](../../../framework/tools/sn-exe-strong-name-tool.md)) para criar um arquivo de par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="2c279-111">Use the [Sn.exe (Strong Name Tool)][Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)) to create a public/private key pair file.</span></span>  
  
     <span data-ttu-id="2c279-112">Esse arquivo tem a extensão .snk.</span><span class="sxs-lookup"><span data-stu-id="2c279-112">This file has a .snk extension.</span></span>  
  
2.  <span data-ttu-id="2c279-113">Exclua a referência COM que está gerando o erro no projeto.</span><span class="sxs-lookup"><span data-stu-id="2c279-113">Delete the COM reference that is generating the error from your project.</span></span>  
  
3.  <span data-ttu-id="2c279-114">Do Windows **iniciar** , aponte para **programas**, aponte para **Microsoft Visual Studio 2008**, aponte para **ferramentas do Visual Studio**, e em seguida, clique em **Prompt de comando do Visual Studio 2008**.</span><span class="sxs-lookup"><span data-stu-id="2c279-114">From the Windows **Start** menu, point to **Programs**, point to **Microsoft Visual Studio 2008**, point to **Visual Studio Tools**, and then click **Visual Studio 2008 Command Prompt**.</span></span>  
  
4.  <span data-ttu-id="2c279-115">Acesse o diretório onde deseja colocar o wrapper do assembly.</span><span class="sxs-lookup"><span data-stu-id="2c279-115">Move to the directory where you want to place your assembly wrapper.</span></span>  
  
5.  <span data-ttu-id="2c279-116">Digite o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="2c279-116">Type the following code.</span></span>  
  
    ```  
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>  
    ```  
  
     <span data-ttu-id="2c279-117">Um exemplo do código que pode ser inserido seria o seguinte.</span><span class="sxs-lookup"><span data-stu-id="2c279-117">An example of the code you might enter would be the following.</span></span>  
  
    ```  
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"  
    ```  
  
     <span data-ttu-id="2c279-118">Use aspas duplas (") se um caminho ou arquivo contiver espaços.</span><span class="sxs-lookup"><span data-stu-id="2c279-118">Use double quotation marks (") if a path or file contains spaces.</span></span>  
  
6.  <span data-ttu-id="2c279-119">No Visual Studio, adicione uma referência de Assembly do .NET para o arquivo que você acabou de criar.</span><span class="sxs-lookup"><span data-stu-id="2c279-119">In Visual Studio, add a .NET Assembly reference to the file you just created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c279-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2c279-120">See Also</span></span>  
 
 <span data-ttu-id="2c279-121">[Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="2c279-121">[Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span></span>  
 <span data-ttu-id="2c279-122">[Sn.exe (ferramenta de nome forte)] [Sn.exe (ferramenta de nome forte)](../../../framework/tools/sn-exe-strong-name-tool.md))</span><span class="sxs-lookup"><span data-stu-id="2c279-122">[Sn.exe (Strong Name Tool)][Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md))</span></span>  
 [<span data-ttu-id="2c279-123">Como criar um par de chaves pública/privada</span><span class="sxs-lookup"><span data-stu-id="2c279-123">How to: Create a Public-Private Key Pair</span></span>](../../../framework/app-domains/how-to-create-a-public-private-key-pair.md)  
 [<span data-ttu-id="2c279-124">Fale conosco</span><span class="sxs-lookup"><span data-stu-id="2c279-124">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
