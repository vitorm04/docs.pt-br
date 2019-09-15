---
title: 'Não foi possível emitir o assembly: <error message>'
ms.date: 08/14/2018
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords:
- BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
ms.openlocfilehash: 530aaee40be92bf72ee4b83b4141108e9b81c8a1
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70968861"
---
# <a name="unable-to-emit-assembly-error-message"></a><span data-ttu-id="99d7e-102">Não é possível emitir o \<assembly: mensagem de erro ></span><span class="sxs-lookup"><span data-stu-id="99d7e-102">Unable to emit assembly: \<error message></span></span>

<span data-ttu-id="99d7e-103">O compilador Visual Basic chama o vinculador do assembly (*al. exe*, também conhecido como ALink) para gerar um assembly com um manifesto, e o vinculador relata um erro no estágio de emissão da criação do assembly.</span><span class="sxs-lookup"><span data-stu-id="99d7e-103">The Visual Basic compiler calls the Assembly Linker (*Al.exe*, also known as Alink) to generate an assembly with a manifest, and the linker reports an error in the emission stage of creating the assembly.</span></span>

<span data-ttu-id="99d7e-104">**ID do erro:** BC30145</span><span class="sxs-lookup"><span data-stu-id="99d7e-104">**Error ID:** BC30145</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="99d7e-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="99d7e-105">To correct this error</span></span>

1. <span data-ttu-id="99d7e-106">Examine a mensagem de erro entre aspas e consulte o tópico [al. exe](../../../framework/tools/al-exe-assembly-linker.md) para obter mais explicações e conselhos.</span><span class="sxs-lookup"><span data-stu-id="99d7e-106">Examine the quoted error message and consult the topic [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) for further explanation and advice.</span></span>

2. <span data-ttu-id="99d7e-107">Tente assinar o assembly manualmente, usando o [al. exe](../../../framework/tools/al-exe-assembly-linker.md) ou a [ferramenta sn. exe (Strong Name)](../../../framework/tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="99d7e-107">Try signing the assembly manually, using either the [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) or the [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md).</span></span>

3. <span data-ttu-id="99d7e-108">Se o erro persistir, reúna informações sobre as circunstâncias e notifique o Microsoft Product Support Services.</span><span class="sxs-lookup"><span data-stu-id="99d7e-108">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>

### <a name="to-sign-the-assembly-manually"></a><span data-ttu-id="99d7e-109">Para assinar o assembly manualmente</span><span class="sxs-lookup"><span data-stu-id="99d7e-109">To sign the assembly manually</span></span>

1. <span data-ttu-id="99d7e-110">Use o [sn. exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)para criar um arquivo de par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="99d7e-110">Use the [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)) to create a public/private key pair file.</span></span>

   <span data-ttu-id="99d7e-111">Este arquivo tem uma extensão *. SNK* .</span><span class="sxs-lookup"><span data-stu-id="99d7e-111">This file has an *.snk* extension.</span></span>

2. <span data-ttu-id="99d7e-112">Exclua a referência COM que está gerando o erro no projeto.</span><span class="sxs-lookup"><span data-stu-id="99d7e-112">Delete the COM reference that is generating the error from your project.</span></span>

3. <span data-ttu-id="99d7e-113">Abra o [prompt de comando do desenvolvedor para o Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="99d7e-113">Open the [Developer Command Prompt for Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md).</span></span>

   <span data-ttu-id="99d7e-114">No Windows 10, insira o **prompt de comando do desenvolvedor** na caixa de pesquisa na barra de tarefas.</span><span class="sxs-lookup"><span data-stu-id="99d7e-114">In Windows 10, enter **Developer command prompt** into the search box on the task bar.</span></span> <span data-ttu-id="99d7e-115">Em seguida, selecione **prompt de comando do desenvolvedor para VS 2017** na lista de resultados.</span><span class="sxs-lookup"><span data-stu-id="99d7e-115">Then, select **Developer Command Prompt for VS 2017** from the results list.</span></span>

4. <span data-ttu-id="99d7e-116">Altere o diretório para o diretório onde você deseja posicionar o seu wrapper de assembly.</span><span class="sxs-lookup"><span data-stu-id="99d7e-116">Change the directory to the directory where you want to place your assembly wrapper.</span></span>

5. <span data-ttu-id="99d7e-117">Insira o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="99d7e-117">Enter the following command:</span></span>

    ```cmd
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>
    ```

   <span data-ttu-id="99d7e-118">Um exemplo do comando real que você pode inserir é:</span><span class="sxs-lookup"><span data-stu-id="99d7e-118">An example of the actual command you might enter is:</span></span>

    ```cmd
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"
    ```

   > [!TIP]
   > <span data-ttu-id="99d7e-119">Use aspas duplas se um caminho ou arquivo contiver espaços.</span><span class="sxs-lookup"><span data-stu-id="99d7e-119">Use double quotation marks if a path or file contains spaces.</span></span>

6. <span data-ttu-id="99d7e-120">No Visual Studio, adicione uma referência de assembly .NET ao arquivo que você acabou de criar.</span><span class="sxs-lookup"><span data-stu-id="99d7e-120">In Visual Studio, add a .NET Assembly reference to the file you just created.</span></span>

## <a name="see-also"></a><span data-ttu-id="99d7e-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="99d7e-121">See also</span></span>

- [<span data-ttu-id="99d7e-122">Al.exe</span><span class="sxs-lookup"><span data-stu-id="99d7e-122">Al.exe</span></span>](../../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="99d7e-123">Sn.exe (Ferramenta Nome Forte)</span><span class="sxs-lookup"><span data-stu-id="99d7e-123">Sn.exe (Strong Name Tool)</span></span>](../../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="99d7e-124">Como: criar um par de chaves pública/privada</span><span class="sxs-lookup"><span data-stu-id="99d7e-124">How to: Create a Public-Private Key Pair</span></span>](../../../standard/assembly/create-public-private-key-pair.md)
- [<span data-ttu-id="99d7e-125">Fale conosco</span><span class="sxs-lookup"><span data-stu-id="99d7e-125">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
