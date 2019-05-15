---
title: 'Não foi possível emitir o assembly: <error message>'
ms.date: 08/14/2018
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords:
- BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
ms.openlocfilehash: 012284aa42dfa29ad1a5e4ec4a4df5eaacbd4fb7
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65642271"
---
# <a name="unable-to-emit-assembly-error-message"></a><span data-ttu-id="d1c4d-102">Não é possível emitir o assembly: \<mensagem de erro ></span><span class="sxs-lookup"><span data-stu-id="d1c4d-102">Unable to emit assembly: \<error message></span></span>

<span data-ttu-id="d1c4d-103">O compilador do Visual Basic chama o Assembly Linker (*Al.exe*, também conhecido como Alink) gerar um assembly com um manifesto e o vinculador relata um erro no estágio de emissão da criação do assembly.</span><span class="sxs-lookup"><span data-stu-id="d1c4d-103">The Visual Basic compiler calls the Assembly Linker (*Al.exe*, also known as Alink) to generate an assembly with a manifest, and the linker reports an error in the emission stage of creating the assembly.</span></span>

<span data-ttu-id="d1c4d-104">**ID do erro:** BC30145</span><span class="sxs-lookup"><span data-stu-id="d1c4d-104">**Error ID:** BC30145</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="d1c4d-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="d1c4d-105">To correct this error</span></span>

1. <span data-ttu-id="d1c4d-106">Examine a mensagem de erro entre aspas e consulte o tópico [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) para obter mais explicações e conselhos.</span><span class="sxs-lookup"><span data-stu-id="d1c4d-106">Examine the quoted error message and consult the topic [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) for further explanation and advice.</span></span>

2. <span data-ttu-id="d1c4d-107">Tente assinar o assembly manualmente, usando o [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) ou o [Sn.exe (ferramenta de nome forte)](../../../framework/tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="d1c4d-107">Try signing the assembly manually, using either the [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) or the [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md).</span></span>

3. <span data-ttu-id="d1c4d-108">Se o erro persistir, reúna informações sobre as circunstâncias e notifique o Microsoft Product Support Services.</span><span class="sxs-lookup"><span data-stu-id="d1c4d-108">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>

### <a name="to-sign-the-assembly-manually"></a><span data-ttu-id="d1c4d-109">Para assinar o assembly manualmente</span><span class="sxs-lookup"><span data-stu-id="d1c4d-109">To sign the assembly manually</span></span>

1. <span data-ttu-id="d1c4d-110">Use o [Sn.exe (ferramenta de nome forte)](../../../framework/tools/sn-exe-strong-name-tool.md)) para criar um arquivo de par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="d1c4d-110">Use the [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)) to create a public/private key pair file.</span></span>

   <span data-ttu-id="d1c4d-111">Esse arquivo tem um *. snk* extensão.</span><span class="sxs-lookup"><span data-stu-id="d1c4d-111">This file has an *.snk* extension.</span></span>

2. <span data-ttu-id="d1c4d-112">Exclua a referência COM que está gerando o erro no projeto.</span><span class="sxs-lookup"><span data-stu-id="d1c4d-112">Delete the COM reference that is generating the error from your project.</span></span>

3. <span data-ttu-id="d1c4d-113">Abra o [Prompt de comando do desenvolvedor para Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="d1c4d-113">Open the [Developer Command Prompt for Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md).</span></span>

   <span data-ttu-id="d1c4d-114">No Windows 10, insira **prompt de comando do desenvolvedor** na caixa de pesquisa na barra de tarefas.</span><span class="sxs-lookup"><span data-stu-id="d1c4d-114">In Windows 10, enter **Developer command prompt** into the search box on the task bar.</span></span> <span data-ttu-id="d1c4d-115">Em seguida, selecione **Prompt de comando do desenvolvedor para VS 2017** na lista de resultados.</span><span class="sxs-lookup"><span data-stu-id="d1c4d-115">Then, select **Developer Command Prompt for VS 2017** from the results list.</span></span>

4. <span data-ttu-id="d1c4d-116">Altere o diretório para o diretório onde você deseja colocar o wrapper do assembly.</span><span class="sxs-lookup"><span data-stu-id="d1c4d-116">Change the directory to the directory where you want to place your assembly wrapper.</span></span>

5. <span data-ttu-id="d1c4d-117">Insira o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="d1c4d-117">Enter the following command:</span></span>

    ```cmd
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>
    ```

   <span data-ttu-id="d1c4d-118">É um exemplo do comando real que você pode inserir:</span><span class="sxs-lookup"><span data-stu-id="d1c4d-118">An example of the actual command you might enter is:</span></span>

    ```cmd
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"
    ```

   > [!TIP]
   > <span data-ttu-id="d1c4d-119">Se um arquivo ou o caminho contiver espaços, use aspas duplas.</span><span class="sxs-lookup"><span data-stu-id="d1c4d-119">Use double quotation marks if a path or file contains spaces.</span></span>

6. <span data-ttu-id="d1c4d-120">No Visual Studio, adicione uma referência de Assembly do .NET para o arquivo que você acabou de criar.</span><span class="sxs-lookup"><span data-stu-id="d1c4d-120">In Visual Studio, add a .NET Assembly reference to the file you just created.</span></span>

## <a name="see-also"></a><span data-ttu-id="d1c4d-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d1c4d-121">See also</span></span>

- [<span data-ttu-id="d1c4d-122">Al.exe</span><span class="sxs-lookup"><span data-stu-id="d1c4d-122">Al.exe</span></span>](../../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="d1c4d-123">Sn.exe (Ferramenta Nome Forte)</span><span class="sxs-lookup"><span data-stu-id="d1c4d-123">Sn.exe (Strong Name Tool)</span></span>](../../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="d1c4d-124">Como: criar um par de chaves pública/privada</span><span class="sxs-lookup"><span data-stu-id="d1c4d-124">How to: Create a Public-Private Key Pair</span></span>](../../../framework/app-domains/how-to-create-a-public-private-key-pair.md)
- [<span data-ttu-id="d1c4d-125">Fale conosco</span><span class="sxs-lookup"><span data-stu-id="d1c4d-125">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
